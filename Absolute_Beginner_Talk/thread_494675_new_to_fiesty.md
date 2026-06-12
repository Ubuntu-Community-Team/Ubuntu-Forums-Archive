---
title: "new to fiesty"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by kartik2104 on 2007-07-07
i m very much new to ubuntu 7.04 just yesterday i have installed 7.04 on my system of 80gb hdd out of which windows is using 60 gigs and 20 gigs is used by ubuntu ram of my system is 512 mb and my processor is a intel 2.8 dual core processor,
when i check the usage of cpu from the system monitor to my horror i find to see that cpu 1 is being used up to 75 % and the cpu 2 is being used upto 30 % , this kind of a usage never took place even wid full loads in windows.
i have watched this just after installing ubuntu i havent changed any processes or services.
is this the normal usage of cpu for ubuntu ?
if no then what might be the problem and how can i set i right.
please some one help me.

---

### Post by felicity on 2007-07-07
I'm not sure, but use gnome-system-monitor to look at which processes are using processing power and this might help narrow the problem a bit.

---

### Post by steve.horsley on 2007-07-07
As felicity says, use System > Administration > System monitor to get a task list, and then choose View > All Processes.

There is a process that kicks of a few minutes after boot that catalogs all files on the disk (for the **locate** utility) but that should only run for a minute or less. My thingy currently says processor is 0% in use. 75% is abnormal.

---

### Post by dptxp on 2007-07-07
> **kartik2104 said:**
> i m very much new to ubuntu 7.04 just yesterday i have installed 7.04 on my system of 80gb hdd out of which windows is using 60 gigs and 20 gigs is used by ubuntu ram of my system is 512 mb and my processor is a intel 2.8 dual core processor,
when i check the usage of cpu from the system monitor to my horror i find to see that cpu 1 is being used up to 75 % and the cpu 2 is being used upto 30 % , this kind of a usage never took place even wid full loads in windows.
i have watched this just after installing ubuntu i havent changed any processes or services.
is this the normal usage of cpu for ubuntu ?
if no then what might be the problem and how can i set i right.
please some one help me.

DID YOU SAY THAT 20 GB IS USED BY UBUNTU RAM oF YOUR SYSTEM ?

---

### Post by 3rdalbum on 2007-07-07
A better idea than using the Gnome System Monitor is to open up a terminal and type this:

```
top
```

Top is a great little console program that shows you a constantly-updating list of the programs that are putting the most load on the system. If there's a program at the top of the list that stays on the top over multiple updates (there's an update every 4 seconds), then you should post back to this thread with the information. Or you could try killing the program yourself.

---

