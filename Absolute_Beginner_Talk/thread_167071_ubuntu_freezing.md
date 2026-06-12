---
title: "ubuntu freezing"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by dentdoc on 2006-04-27
I am trying to load Ubuntu onto a system as the stand alone OS. The system is an old system with a K6-2/450 and i have a 20g hd. it started up just fine until i got to 71% while installing packages Configuring xserver-xorg and it just stops. I tryed a different Ubuntu CD but still get the same thing. ](*,)  Can anyone help pleassssse

Thanks 
dentdoc

---

### Post by tburns on 2006-04-27
try a live cd first. also, try an older version.

---

### Post by dentdoc on 2006-04-27
i ran the live cd on the computer and it worked just fine........

---

### Post by tburns on 2006-04-27
I have had better success with 5.01 on older systems than 5.10. Are you trying 5.01? or 5.10? or the dapper?

---

### Post by khightower on 2006-04-27
[QUOTE=dentdoc]i ran the live cd on the computer and it worked just fine........[/QUOTE]

On older system I boot to the Live CD and let it login all the way to the desktop> From the Desktop I click the install icon. This has worked for me.

---

### Post by dentdoc on 2006-04-27
I am trying to use 5.10

---

### Post by Qrk on 2006-04-27
Try isntalling over the 'net. It might work a little better. If you boot up into your (broken) ubuntu installation, even though the process was halted, you should still get into the command line. 

Log in, make sure your cd is out of the drive and run the command:

```
sudo apt-get install ubuntu-desktop
```
You'll need an internet connection.

---

### Post by dentdoc on 2006-04-27
I do not have internet on the computer that I am trying to set up with Ubuntu and when it trys to reboot after installing from cd and sticks at 71% while trying to finish instalation. It always gets to installing packages and is trying to Configuring xserver-xorg and just stops cant get any further. The hard drive was wiped clean before instalation so I dont even have Windows on it anymore to boot up to get online. :confused:

---

