---
title: "Error during update to 7.04"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-04-22
Hey all,
Just went to upgrade my system to Fiesty (I figure the servers have cooled down by now) and got the following error:


[B]Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.[/B]
**Failed to fetch [http://free.linux.hp.com/~brett/seveas/freenx/dists/ubuntu-seveas/freenx/binary-amd64/Packages.gz](http://free.linux.hp.com/~brett/seveas/freenx/dists/ubuntu-seveas/freenx/binary-amd64/Packages.gz) 404 Not Found**

Then the upgrade aborts.

I had attempted to install freenx about a month ago and it didn't quite work on the AMD 64 platform (or at least I couldn't get it to).

I went to uninstall if thru synaptic, but it only gives me the "mark for install" option.
Is there a way to uninstall freenx or get the update-manager to skip over that message and continue?

Oh yeah, the network connection on my end is fine, ~brett/seveas... is not there.

Thanks!
Brian

---

### Post by heimo on 2007-04-22
Run,
```
gksudo gedit /etc/apt/sources.list
```
comment out (using # at the beginning of line) references to the repository which is not responding. "sudo aptitude update", retry.

---

### Post by marmaladejackson on 2007-04-22
That did it!
You rock!

---

