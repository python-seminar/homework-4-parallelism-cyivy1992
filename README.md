# homework-4-parallelism-cyivy1992
homework-4-parallelism-cyivy1992 created by GitHub Classroom

All codes for this assignment can be found in the Monte Carlo dart-throwing Pi approximation.ipynb file.

The resulting plot is Camparison.png.

#### Name
Ying Cao

#### SID
25937400

## The program
Monte Carlo dart-throwing Pi approximation.ipynb takes the monte carlo algorithm provided in the assignment and implements it 
1. as is, 
2. using the multiprocessing module, and 
3. using ipyparallel module to parallelize.

Ten different numbers of darts ranging from 10 to 10^7 were used, for each 100 simulations were conducted.

## Results
Mean execution time and mean simulation rate for all three methods were plotted as a function of number of darts, with a 1-sigma interval.

## System Specs
Ubuntu 16.04 with Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz, 2 “cores”.

## Run
To start Ipcluster, run the following commands in shell before using the ipyparallel module:
```
$ ipcluster start -n 4
```
and the following command when the simulations are finished:
```
$ ipcluster stop
```
The other part can be ran as normal Jupyter Notebook file.

## Plot Illustration

1. Serial Method has a relatively stable simulation rate, and its execution time grows almost linearly as the number of darts increases.
This implies that the single processor used to handle the job was at full load for all the experiments.
2. When the number of darts is small, paralleled algorithm did not take the full capacity of four processors. 
So the execution times of the two paralleled algorithm remained constant for a while, when they tolarate more workload without slowing down.
However, parallelism also requires the time to split the task and gather information, thus took more execution time (with lower simulation rate) than the serial method when the number of darts is small.
3. By comparing the two parallism modules, it seems that Iparallel takes more time to handle the task distributuion process than Multiprocessing module. Thus, it took more execution time (lower simulation rate) with small datrs numbers.
But, as the number of darts increases so that the simulation time dominates, these two methods eventually performed similarly, and beat the serial method.
