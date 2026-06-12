---
title: "Java killed Ubuntu"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Smith101 on 2007-09-24
Hi guys I just installed Java, but now it gets in the way of other code 

when ever I enter sudo apt-get install etc.....
it says "dpkg was interrupted you must manually run 'dpkg -- configure a' to correct the problem

I run apt by itself
it's says
the following apt can be found in 
sun-java5-jdk
sun-java6-jdk

I'm really new to Linux, so I don't know the prompts yet

The problem occurred as soon as I installed java (I was trying to get the Firefox plug in to work) Synaptic package manager won't even work now

Could you guys help.

---

### Post by overdrank on 2007-09-24
> **Smith101 said:**
> Hi guys I just installed Java, but now it gets in the way of other code 

when ever I enter sudo apt-get install etc.....
it says "dpkg was interrupted you must manually run 'dpkg -- configure a' to correct the problem

I run apt by itself
it's says
the following apt can be found in 
sun-java5-jdk
sun-java6-jdk

I'm really new to Linux, so I don't know the prompts yet

The problem occurred as soon as I installed java (I was trying to get the Firefox plug in to work) Synaptic package manager won't even work now

Could you guys help.

Hi you can run the command 
```
sudo dpkg -- configure a
```
and it should correct it. good luck!

---

### Post by Smith101 on 2007-09-24
> **overdrank said:**
> Hi you can run the command 
```
sudo dpkg -- configure a
```
and it should correct it. good luck!

It brings up a list of options,  none of which I can execute
I get this
dpkg --configure returned error exit status 2.

>

Just a side question I thought of just freshly installing Ubuntu over Ubuntu to reset everything, but when I boot from the disk nothing happens, any ideas.

---

### Post by overdrank on 2007-09-24
> **Smith101 said:**
> It brings up a list of options,  none of which I can execute
I get this
dpkg --configure returned error exit status 2.

>

Just a side question I thought of just freshly installing Ubuntu over Ubuntu to reset everything, but when I boot from the disk nothing happens, any ideas.

I am truly sorry the command is 
```
sudo dpkg --configure -a
```

---

### Post by Smith101 on 2007-09-24
Dude you're a life saver, However is there as way to completely reset the OS to it's original state, just in case I ever want to do it.

Thanks for you time

---

### Post by overdrank on 2007-09-24
> **Smith101 said:**
> Dude you're a life saver, However is there as way to completely reset the OS to it's original state, just in case I ever want to do it.

Thanks for you time

Hi I don't know that answer but I have heard of this to backup
[http://livecd.berlios.de/](http://livecd.berlios.de/)
As I am sure there are other ways of restoring your system. Good luck!

---

