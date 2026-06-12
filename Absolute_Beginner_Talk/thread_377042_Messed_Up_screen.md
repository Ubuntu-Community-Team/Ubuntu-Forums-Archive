---
title: "Messed Up screen"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by amantonas on 2007-03-05
I have tried many different Linux distributions. None of them worked. I ordered Ubuntu and Kubuntu  cds in the mail, and It just Started loading! Once it booted off of the live Cd, The screen started to get all wavy on the right side of the screen. I can't install it because I can't read any of the instructions and questions. I am fairly new to Linux. What should I do? Is there any way to resolve this?

---

### Post by Dr. Nick on 2007-03-05
Have you tried the "safe graphic" option on the initial boot screen?
 
It looks to be a issue with how your monitor is detected.

---

### Post by amantonas on 2007-03-05
Ok, It looks Fine. But what do I do there? If I reboot It, will it stay the same?

---

### Post by Dr. Nick on 2007-03-05
Got your email, but will respond here.

It will not stay that way as you may know, What I would recommend doing is look at the menu "system - prefrences - screen resolution" while on the live cd and take note of it. Then install it and chances are the screen will be messed up upon reboot, so choose rescue or recovery mode from the boot screen and it will take you to a command line

type

dpkg-reconfigure xserver-xorg

and follow through the steps, pay attention to the part dealing with the monitor, when given the choice of "simple- advanced - expert) or similar choose the middle one and specify the resolution and refresh rate you noted earlier and see if that helps, If not then try different combinations and see if it looks right.

---

### Post by amantonas on 2007-03-06
Ok, but where should I do it. Off the safe Graphics mode user, the normal user, or should i install it first and then do it?:confused:

---

### Post by Dr. Nick on 2007-03-06
Install it to the hard drive from safe graphics mode, If it boots up off the hard drive after installation and is still messed up then reboot and choose the @nd option from the boot, should say recovery or rescue.

Once that boots you will be in a command line, then do 

[B]dpkg-reconfigure xserver-xorg

[/B]and chose the correct monitor type. May take a few times to get the right setup.

---

### Post by amantonas on 2007-03-07
Ok, That worked. But now, i want to upgrade from Dapper to edgy. i put in the live CD, and i booted it to the normal screen. it was all wavy. so i went to safe graphics mode, and It was all wavy. What should I do?

---

### Post by Dr. Nick on 2007-03-07
Buy a new monitor lol j/k :)

You can compare your xorg.conf between the installed and properly working dapper and the one on the live cd after boot (if its readable) It is located in /etc/X11/xorg.conf

Just compare and see what is different in the monitor and device sections is all I could think to do.

You could also try and update it to edgy online instead of using the live cd by using the commands listed here in method A

[http://ubuntuforums.org/showthread.php?t=227052](http://ubuntuforums.org/showthread.php?t=227052)


If none of that works then you could always get the alternate install cd and install it using text mode then redo the dpkg-reconfigure bit once its installed

---

### Post by amantonas on 2007-03-08
For some reason, Neither of those worked. Should I just Uninstall Kubuntu 6.06 and Install 6.10?

---

### Post by Dr. Nick on 2007-03-08
The online update didnt work? If you want you can install 6.10 (edgy) but you will probably have to redo the dpkg-reconfigure xserver-xorg after the install.

If you decide to isntall a fresh copy I would use the alternate install cd if you can download it, its text based so the screen should be more readable.

---

### Post by amantonas on 2007-03-09
So, I should Download the CD and Install it over dapper, or uninstall dapper and install edgy using text mode?

---

### Post by Dr. Nick on 2007-03-09
> **amantonas said:**
> So, I should Download the CD and Install it over dapper, or uninstall dapper and install edgy using text mode?

You can download it and when you boot you can choose to format the partition dapper is on now. I think you can also update it if you want to try.

You really dont need to uninstall anything, You just have to decide if you want to update dapper or just start over with edgy.

To start over just format the partition with dapper from the installer, If you want to try I think their is a update choice aswell, if the update choice failed then you can still do a clean install by formatting

---

### Post by amantonas on 2007-03-10
I formatted and re-partitioned(using the text mode you suggested) and it worked Great!!!! I had absolutely no problems. I knew all of my configuration settings, so the dpkg-reconfigure took about 5 minutes. After that, my sound started working. Thank you so much for helping me!:KS

---

### Post by Dr. Nick on 2007-03-10
Glad it all worked out!

---

