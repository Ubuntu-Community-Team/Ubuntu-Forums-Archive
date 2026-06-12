---
title: "Error on fresh Ubuntu install on iBook G4"
date: 2009-03-06
forum: Apple Hardware Users
---

### Post by Thorney on 2009-03-06
I have been on gentoo for the last month or so but got a bit feed up with all the configuring so have decided to go to ubuntu.

After installing and logging in I am greeted by 9 pop up errors all similar to the following:

> 
The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet". 
Do you want to delete the applet from your configuration?
[Don't Delete][Delete]


My searching found a [bug]("https://help.ubuntu.com/community/UbuntuDateBug") involving the date being incorrect. It says to execute the following command:
```
date
```
When I execute this command the output is correct...

However after more grepping the internets it still seems like the most likely problem.

Turns out date has a counterpart - hwclock. Running 
```
sudo hwclock --show
```
tells me its 1904!!!

So then ran:
```
sudo hwclock --localtime --systohc
```

Which seems to have set the hardware clock correctly. Will restart gdm and see what happens.

---

### Post by Thorney on 2009-03-06
Well mixed results. The system just hung on a black screen after logging out. With a manual power down and restart I have no logged in with all the panel apps working (and no errors) The date was wrong immediately after logging in but is now correct.
Something is a bit funny because the log off button under System is gone...```

brian@brian-laptop:~$ dmesg |grep err
[   22.575540] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)

brian@brian-laptop:~$ date
Fri Mar  6 20:13:28 NZDT 2009
brian@brian-laptop:~$ sudo hwclock --show
Fri 06 Mar 2009 20:13:30 NZDT  -0.546695 seconds

```
Any ideas of what could be wrong now - or where to look for clues?

---

### Post by mkvnmtr on 2009-03-06
I have a G4 Ibook. The battery is dead. If I try to start it not connected to the internet I have the time and date problem in either Mac os or Ubuntu. Could this be your problem with the date?
As for your other problems I have not encountered them and have installed everything from 6.06 to 8.10.

---

### Post by lethrj on 2009-05-15
I am having the same problem.  Many Panel errors.  They must not like the time.

```
$ sudo hwclock
Fri 01 Jan 1904 12:41:47 AM EST  -0.077807 seconds

```I'm on a PowerBook G4 with no battery.  And I have some PMU issues.  Log out/Log in fixes clock and errors.

---

### Post by stream303 on 2009-05-15
Be sure to tell us exactly which verson of Ubuntu you installed.

If it was Intrepid 8.10, I'd suggest falling back to Hardy, or skip immediately to Jaunty - Intrepid 8.10 had some major issues beyond the norm.

---

### Post by Thorney on 2009-05-16
I have only had this come back up once or twice in the time since first installing ubuntu. It always happened after having a very low  battery.

---

### Post by paulodelgado on 2009-09-21
Disregard this...

---

### Post by Thorney on 2009-11-09
Same problem exists in Karmic - if I ever leave my laptop on till battery runs out it restarts with a million gdm errors.

---

