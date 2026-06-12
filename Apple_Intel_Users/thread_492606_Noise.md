---
title: "Noise"
date: 2007-07-04
forum: Apple Intel Users
---

### Post by sprucio on 2007-07-04
I am having a problem in Ubuntu where every time I use it, it makes this noise like a fan is constantly rotating at a high speed. I have experienced this problem in OS X as well but it's been very sporadic with OS X. In Linux, it seems like this happens right off boot. Has anyone else experienced this problem?

---

### Post by PaulFr on 2007-07-04
Could this be that your system is running too hot ? Please install acpi using **sudo apt-get install acpi** in a terminal. Then run **acpi -V** to see information on power management (including temperature).

---

### Post by sprucio on 2007-07-05
I will try and post but this is a new install that I just did. I was wondering if anyone else had the same problem.

This is actually my second time re-doing this triple boot. I was hoping that this would go away but it appears unlikely that it will go away by itself.

---

### Post by grim1234 on 2007-07-05
Is it a very high pitched noise, not too loud? If so it's probably the power convertors on the board. google macbook whine for more info.

---

### Post by sprucio on 2007-07-05
I have found some articles about this but again, this seems to happen in Linux almost immediately as where in OS X, it doesn't do this all the time.

---

### Post by grim1234 on 2007-07-06
try this in osx : run idle, open photobooth, then idle again. Does the noise stop when you open photobooth?

If it is the whine, and I can't tell from here, it may be linux is putting less load on the system that osx, so the whine is more noticable.

---

### Post by C0d3Runr on 2007-07-06
In a terminal:
cat /sys/devices/platform/applesmc/fan0_actual_speed
should tell you how fast the fan is presently running (in RPM, i believe).  Around 2000 means the system is running pretty cool and it doesn't need the fan much, around 5000~6000 means that the system is running very hot and the fan is going constantly.  I'm kinda curious what your fan is doing, and this should help to find out.  :)

---

### Post by sprucio on 2007-07-07
5929 is the number I got.  This is a fresh install of Ubuntu. Is there anything I can do to decrease this number?

---

### Post by pveith on 2007-07-07
Please open a terminal and type in the command "top". There should be CPU info in the 3rd line. If your CPUs are "stressed" (categories "us" and/or "sys" having high percentages) you should go through the processes below (staring at line 9) and see which programs cause the stress. That should enable you to change the situation by stopping that program (quit top by pressing q and enter the command "kill -9 <PID>". (PID is the identification number of th e programm you want to stop. The number is noted in the first column in the 9+ line for each programm you see in top.) This should unstress your cpus.

Next i would suggest you to hunt down why the program is running and how to stop it from eating you cpus. I know that beagle and other search engines often eat CPUs until they are done indexing for the first time. Just post the suspects name here and there will be somebody to help.

---

### Post by sprucio on 2007-07-08
The noise actually starts when I'm at the rEFIt boot menu. If I leave it there for more than 20 seconds, the fan noise starts going. I did check top as well before my previous post. I didn't see anything that was draining the CPU at all. However, we now know that the CPU fan is the actual thing that's causing the noise as I've verified this with my last post.

I noticed that it takes about 5 minutes but the speed of the fan does slow down in Linux. With OS X and Windows, it takes about a minute for the fan to slow down.

I'm not sure if I asked this earlier but it takes about 20 seconds after I power on the computer to see the rEFIt menus. Is anyone else in the same boat?

---

### Post by thully on 2007-07-08
If you are having the "MacBook whine" issue, there evidently is a known workaround on Linux.  However, it comes at the cost of a slight amount of battery life.

Simply add the following to the end of /etc/init.d/acpid (before the exit command)
echo 2 > /sys/module/processor/parameters/max_cstate

That will make the whine disappear.

---

### Post by sprucio on 2007-07-08
Thanks for that info. Do you know how much this will effect the battery?

---

### Post by sprucio on 2007-07-08
I added that to the file but it didn't fix the problem. Again, the whine actually starts when I am in the rEFIt window and gets worse before Linux even loads.

---

### Post by sprucio on 2007-07-09
Running the command "acpi -V" didn't give me much information at all. If I recall correctly, it said something about it not being supported.

Is anyone else having the problem with this? I just want to confirm that I'm not the only one who is having this problem where the fan is spinning at such a high RPM.

---

### Post by cyberdork33 on 2007-07-09
no you should definitely have that working.

---

