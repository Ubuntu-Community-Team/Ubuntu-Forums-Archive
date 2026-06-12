---
title: "mpich problem, please help"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by |Taulant on 2008-04-09
Hello there.
I am running mpich in ubuntu and when i try to run a program i get this problem:

i write -->  ./mpirun -np 4 hello++

i get --> 

ssh: connect to host dennis-laptop port 22: Connection refused
p0_19477:  p4_error: Child process exited while making connection to remote process on dennis-laptop: 0
p0_19477: (6.260091) net_send: could not write to fd=4, errno = 32

Please help...

---

### Post by sdennie on 2008-04-09
It's been a long time since I've used mpich but, the error message looks like it's trying to ssh back to your machine but you don't have an ssh server running.  Doing something like:

```

sudo apt-get install openssh-server

```

Should fix your problem (or at least be a step in the right direction).

---

### Post by |Taulant on 2008-04-09
Thank you very much. Ok this problem was gone but now i have a new one...

When i run a program i have to enter the password as many times as the number of processors ( minus one ) that i want to use.

For example when i write >./mpich -np 5 hello_world

I have to enter it 4 times
...

---

### Post by arkangel on 2008-04-09
[http://linuxproblem.org/art_9.html](http://linuxproblem.org/art_9.html)

---

### Post by arkangel on 2008-04-09
[http://www-unix.mcs.anl.gov/mpi/mpich1/docs/mpichman-chp4mpd/node108.htm](http://www-unix.mcs.anl.gov/mpi/mpich1/docs/mpichman-chp4mpd/node108.htm)
[http://linuxproblem.org/art_9.html](http://linuxproblem.org/art_9.html)

---

### Post by |Taulant on 2008-04-10
Thank you very much... :)

---

