---
title: "CPU scaling"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by andrem on 2006-12-27
Hi, I'm a beginner, and I'm using Edgy on a HP nc6320.

I already got most things working, but my Core Duo doesn't seem to speedstep any of the cores.

I read a tutorial that uses powernowd, and I have it installed. The problem is, when i do /etc/init.d/powernowd start i get:

[I] * Starting powernowd...                                                        
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported[/I]

Actually, running "ls /sys/devices/system/cpu/cpu0/" returns only:
*cache  crash_notes  topology*

Seems like cpufreq dir is missing... Can anyone help me with this?

Thanks in advance!

---

### Post by ramjet_1953 on 2006-12-27
Try running gksu before the command.
It will ask you for your admin password, before executing the command.

Hopefully, this will help.

Roger 8)

---

### Post by andrem on 2006-12-28
Sry, I forgot to tell that i'm already using sudo -s...

Using gksu turns into the same error...

---

### Post by kinematic on 2006-12-28
you also need a cpu driver(like powernow-k8 0r p4-clockmod)but chances are a driver for a core2 duo isn't in the kernel yet since it's a new line of processors.

---

### Post by mcduck on 2006-12-28
Using generic kernel my Core Duo works perfectly out-of-the-box in Edgy.. And it worked in Dapper too, with 686-smp kernel.

---

### Post by andrem on 2006-12-28
I have a Core Duo, not a Core 2 Duo.
As for the driver, how can I get it? Should I have it already?

---

### Post by Nucleus on 2006-12-31
Hello my friend.
I have same laptop and same issue. My battery was decharging in 2 hours.
And my batery indicator wasn't work properly.

I have just upgraded my bios from F.08 to F.09 and I think I have solved the problem.
I am still testing but I haven't faced a problem yet.

Maybe a bios upgrade can be useful for you , too...

---

### Post by OffHand on 2006-12-31
> **ramjet_1953 said:**
> Try running gksu before the command.
It will ask you for your admin password, before executing the command.

Hopefully, this will help.

Roger 8)
On the command line you use sudo instead of gksudo.

---

### Post by meldroc on 2007-01-02
I would like to know how to get this feature working as well.  I'm running an Asus A8Js, with a T7200 2GHz Core 2 Duo.  I'm getting the same errors as the OP, and YES, I'm using sudo to make sure I'm attempting to run powernowd with root privileges.

---

### Post by andrem on 2007-01-02
> **Nucleus said:**
> Hello my friend.
I have same laptop and same issue. My battery was decharging in 2 hours.
And my batery indicator wasn't work properly.

I have just upgraded my bios from F.08 to F.09 and I think I have solved the problem.
I am still testing but I haven't faced a problem yet.

Maybe a bios upgrade can be useful for you , too...
My BIOS is F.08. I'll probably upgrade it to F.09 too and check if the problem persists.

---

### Post by andrem on 2007-01-02
Just updated my BIOS to F.09 and the problem seems to be solved! :D 

Right now I'm running on battery and both cores are at 1GHz, and the remaining time is 2:40 for a 96% charge. Still not as good as I get using Bill's OS (over 3 hours) in this PC, but way better than before!

Thanks for helping! :mrgreen:

---

### Post by andrem on 2007-01-04
Just to add some extra info on this subject, after upgrading to F.09 the scaling is working, but Ubuntu seems not to recognize when my laptop is AC powered. It reports it is charging the battery though.

Right now it is AC powered, batteries fully charged, and my cores are still scaling like they were when on battery power... Not a really big deal, but I thought this might help someone. :KS

---

### Post by andrem on 2007-01-05
Well... I must report a problem, now that I've further tested these bios upgrade and Edgy: It seems that my Ubuntu Power Manager stops updating its status often. I mean, when I boot up, it shows the correct info, but it never updates... ](*,)

---

### Post by belial6 on 2007-01-22
Had a similar problem with HP nw8440. On boot-up the status was ok, but later on it wasn't updated anymore. 
After searching through numerous forums found a thread from the HP site [http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1026460&admit=-682735245+1169499744650+28353475]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1026460&admit=-682735245+1169499744650+28353475")


It's a quite long thread, so I'm going to sum it up:

In most cases the problem is caused by BIOS going to a so-called "bad state". 
Strangely enough this is caused by the touchpad. :D
Because Ubuntu already has PS/2 mouse driver compiled as a module, it isn't too hard to fix this.
No kernel recompiling necessary :)

This is what you have to do:
1. Create a script for unloading psmouse module during shutdown using nano
```
sudo nano /etc/init.d/psmouse
```

Paste the following into it:
```

#! /bin/sh
# For unloading psmouse module at shutdown

. /lib/lsb/init-functions

case "$1" in
start)
  ;;

stop)
  log_begin_msg "Unloading psmouse module"
    modprobe -r psmouse
  log_end_msg $? "Failed to unload psmouse module"
  ;;

*)
  log_success_msg "Usage: $N {start|stop}" >&2
 
esac

```

2. Make the script executable
```
sudo chmod +x /etc/init.d/psmouse
```

3. Add this script to default runlevel, so it is executed at shutdown
```
sudo update-rc.d psmouse defaults
```

4. Now you have to get your computer out of the bad state, before this fix will work.
In order to do this:
[LIST]
[*]turn off your laptop
[*]remove the power cord and battery
[*]wait for about 5 seconds or so
[*]put the battery back in and also connect the power cord, if you like
[/LIST]

5. Boot up as usual and test the battery notifications.

---

### Post by andrem on 2007-01-23
Thanks. I realized that this happens sometimes, not every time. I'll try that, and post the result!

---

### Post by matejkenda on 2007-02-01
> **belial6 said:**
> Had a similar problem with HP nw8440. On boot-up the status was ok, but later on it wasn't updated anymore. 
After searching through numerous forums found a thread from the HP site [http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1026460&admit=-682735245+1169499744650+28353475]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1026460&admit=-682735245+1169499744650+28353475")


This is still a problem in Feisty on nw8440 and other newer dual core HP laptops.

It seems that this problem can be solved with a simple patch in the ```
psmouse
``` kernel module. I have opened a bug:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82681](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82681)

---

### Post by andrem on 2007-02-02
Thank you all for your contribution.  BTW I also noticed the loss of keyboard response at startup (using dual boot is quite annoying... :-k )

---

### Post by matejkenda on 2007-02-06
> **matejkenda said:**
>  I have opened a bug:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82681](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82681)

FYI: Fix was committed for this bug and will be available in one of the next kernels for Feisty Fawn.

---

