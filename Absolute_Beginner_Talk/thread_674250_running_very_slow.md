---
title: "running very slow"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Pap3rbag on 2008-01-21
everything in ubuntu is running very slow

i have a ati 1650 512mb

4gig of ram

amd 64 x2 5000

and 80g for this partition 

on vista everything runs very smooth

---

### Post by steve-shinn on 2008-01-21
With that spec, the pc should fly ? has it been running slow ever since you installed Ubuntu ?

---

### Post by duruttye on 2008-01-21
Usually it is the opposite!!!

Install htop and try to find out what is using your CPU, if that is the problem, also you can add a system monitor to one of you panels and watch the CPU and memory there.

You system is pretty well equipped for running 3 ubuntus at a time, so something is clearly wrong there!

---

### Post by yaknowwat on 2008-01-21
hmm looks like an ATI graphics card issue most likely.

Have you tried to use Compiz recently.

if  you have pop open the system monitor (even if you haven't)

Go to the Processes Tab

click '% CPU'

It should give you a list of what the processes are taking.

it may most likely be special graphics related such as Xgl

if thats the case pop open the Synaptic Package Manager ( System > Admin > )

and search for it and uninstall.

---

### Post by JGJones on 2008-01-21
> and search for it and uninstall.

No no I would not suggest this in case it's a package that is needed for Ubuntu to work (ie it might say x.org is taking up all CPU, it's not a good idea to remove x.org unless you fancy a no-GUI system)

Tell us what is taking up your CPU in System Monitor which is found in System > Administration > System Monitor.

Click on the CPU column to sort by that column and see what's at top (on a freshly started Ubuntu, without opening any software and giving it some time to allow everything to load up).

Let us know what's the CPU "suckage" then.

Cheers

---

### Post by yaknowwat on 2008-01-23
> **JGJones said:**
> No no I would not suggest this in case it's a package that is needed for Ubuntu to work (ie it might say x.org is taking up all CPU, it's not a good idea to remove x.org unless you fancy a no-GUI system)

Tell us what is taking up your CPU in System Monitor which is found in System > Administration > System Monitor.

Click on the CPU column to sort by that column and see what's at top (on a freshly started Ubuntu, without opening any software and giving it some time to allow everything to load up).

Let us know what's the CPU "suckage" then.

Cheers

that was a typo im sorry i was thinking about something else I meant to put ' Xgl '
sorry.

---

