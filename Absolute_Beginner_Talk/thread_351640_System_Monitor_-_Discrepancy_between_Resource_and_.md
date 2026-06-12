---
title: "System Monitor - Discrepancy between Resource and Process"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-02-02
Probably a stupid question.

I am running Dapper on a twin 733Mhz machine.

The System Monitor/Resource show both processors running at 60-80%

I look at System Monitor/Process and it reports only 30% CPU utilization. So I cannot find what is hammering the CPU because it does not show in Processes when sorted on CPU.

Until yesterday it barely broke a sweat and rarely reached 20% on each processor.

Now the machine is struggling an I cannot find what is eating it,

Any ideas anyone?

Also - If I have a hung window, how do I know what its name is in the Process list, the name of the window does not seem to link to process? It kinda makes it difficult to kill the rogue process if you cannot find it.

Thanks

Mike

---

### Post by halfvolle melk on 2007-02-02
Hey Mike,
To check what process is eating your CPU you could use **top**. Open a terminal and type top. Then press 1, this will make both CPUs show up. Press q to quit.

---

### Post by Busta999 on 2007-02-02
OK - I confess I did a REALLY (R) REALLY dumb thing..........

While trying to hunt down the process that was eating my CPU I saw that a process called XORG was grabbing 30-40%

OK - Now know that was dumb but...

I killed XORG...

OK so my VNC session died.....

I went to the machine and the screen was frozen so I ended up by having to kill the power to get it to reboot. I made sure nothing externally was writing to the machine.

I kinda hoped it would just reboot but.....

Now it boots I get a responsive mouse pointer and the Ubuntu background but that is all - nothing else.

It does not respond to keyboard or mouse.

Can't telnet into it either.

Is it a re-install to fix or is there some way to get it going again?

Thanks

---

### Post by randomnumber on 2007-02-02
It maybe a program running with root privaleges .

in a terminal 

gksudo gnome-system-monitor 

This wil give all applications, I believe. I found out that the system monitor did not display all programs running on machine and that the processes running with root are not allowed to be viewed by non-root.

---

### Post by randomnumber on 2007-02-02
> **Busta999 said:**
> OK - I confess I did a REALLY (R) REALLY dumb thing..........

While trying to hunt down the process that was eating my CPU I saw that a process called XORG was grabbing 30-40%

OK - Now know that was dumb but...

I killed XORG...

OK so my VNC session died.....

I went to the machine and the screen was frozen so I ended up by having to kill the power to get it to reboot. I made sure nothing externally was writing to the machine.

I kinda hoped it would just reboot but.....

Now it boots I get a responsive mouse pointer and the Ubuntu background but that is all - nothing else.

It does not respond to keyboard or mouse.

Can't telnet into it either.

Is it a re-install to fix or is there some way to get it going again?

Thanks

I would try 

ALT + CTR + F1

log in 

You may beable to reconfig xserver and that might solve the problem.
sudo dpkg-reconfigure xserver-xorg
[http://www.ubuntuforums.org/showthread.php?t=333888&highlight=reconfig+xserver](http://www.ubuntuforums.org/showthread.php?t=333888&highlight=reconfig+xserver)

good luck

---

### Post by pandu.rs on 2007-02-02
If your machine is struggling you should also check the memory used by the processes.

for me firefox-bin will eat 60-70% after 1 week and the whole system will respond very slowly. i will kill firefox and restart it,, and then everything will work fine

---

