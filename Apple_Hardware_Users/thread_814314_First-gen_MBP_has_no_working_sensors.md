---
title: "First-gen MBP has no working sensors"
date: 2008-05-31
forum: Apple Hardware Users
---

### Post by apetresc on 2008-05-31
Hey guys.

I tried using the instructions [found here](https://help.ubuntu.com/community/MacBookPro#head-c0f8e103a33dc32cc89664a81513c2497d44b336) to install sensors for hard drive temperature and CPU core temperature. Everything installed without a hitch, but when I add the applet to Gnome and go to the "Sensors" tab, only hddtemp appears on the list. Nothing for CPU cores.

I did indeed follow the instructions for coretemp, and the module is loaded: ```
adrian@gauss:~$ sudo lsmod | grep coretemp
coretemp                8448  0 
``` However, this also happens: ```
adrian@gauss:~$ sudo sensors -s
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```
So I run sensors-detect and it tells me to add "coretemp" to my /etc/modules file, so I do, and I restart. Same thing, nothing has changed. I tried this: ```
adrian@gauss:~$ dmesg | grep coretemp
[   46.282165] coretemp coretemp.0: Errata AE18 not fixed, update BIOS or microcode of the CPU!
[   46.282188] coretemp coretemp.1: Errata AE18 not fixed, update BIOS or microcode of the CPU!
```
I'm not sure if that's normal or not.

Can anyone help me? I'd really feel a lot safer using Ubuntu on the Macbook Pro if I could see what the temperature was like. It certainly FEELS hotter when running Ubuntu as opposed to OS X but I want to make sure it's at an acceptable level.

Thanks in advance :)

---

### Post by cyberdork33 on 2008-05-31
They do seem to run hotter in Ubuntu.

coretemp should be the way to go, but judging from the error messages you posted, it sounds like it is not recognizing your CPU. (you have a Core Duo, not a Core2 Duo, right?)

I would guess that it is a bug in coretemp.

---

### Post by apetresc on 2008-05-31
> **cyberdork33 said:**
> coretemp should be the way to go, but judging from the error messages you posted, it sounds like it is not recognizing your CPU. (you have a Core Duo, not a Core2 Duo, right?)

I would guess that it is a bug in coretemp.
Yes, it's a Core Duo, since this is the first gen. I considered a bug in coretemp, but since pretty much all first-gen MBPs have the same hardware, and certainly *somebody* must have reported this before me if that were the case -- but I couldn't find anyone else with those errors judging from a forum search.

Can anyone else with a first-gen MBP confirm that they can or cannot use any CPU temperature sensors?

Should I file a bug report on Launchpad?


Thanks, cyberdork :) You seem to come to my rescue an awful lot!

---

### Post by cyberdork33 on 2008-05-31
There are actually not too many people posting with 1gen Macbooks anymore... For the most part, they are pretty easy to setup now that most of the issues have been worked out. IDK that launchpad would be the right place since it is likely not particular to Ubuntu... but it might be a good starting point for getting info.

You are the only one I have seen reporting such an issue.

---

