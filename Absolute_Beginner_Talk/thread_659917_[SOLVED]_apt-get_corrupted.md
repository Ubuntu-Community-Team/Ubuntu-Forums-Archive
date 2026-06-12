---
title: "[SOLVED] apt-get corrupted"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2008-01-06
Ok not sure what happened but somehow when a relative was on system something got hosed, now will not boot into ubuntu. I get screen that is telling apt-get not installed and to type apt-get install apt  but that doesn't work. Please some help :confused:

---

### Post by PmDematagoda on 2008-01-06
Can you boot Ubuntu in Recovery Mode properly?

---

### Post by J11Gyro on 2008-01-06
> **PmDematagoda said:**
> Can you boot Ubuntu in Recovery Mode properly?

nope cannot even boot to previous kernal, get same result and command does not work

---

### Post by nowshining on 2008-01-06
ur Relative should not of been able to mess the system up that bad, u need ur pw/administrator pw to do install/remove programs, and a lot of stuff requires sudo/gksudo, if u used sudo / gksudo in the last 15m before u gave the computer up to ur relative, u can decrease the timeout, otherwise sudo / gksudo will be active and available without a pw for about 15m.

---

### Post by nowshining on 2008-01-06
oh and u need to put 

sudo apt-get install apt


:) input ur pw and u need a working internet connection

---

### Post by SOULRiDER on 2008-01-06
I doubt whi will work but try some command using aptitude like for example
```
sudo aptitude update
```

---

### Post by J11Gyro on 2008-01-06
> **nowshining said:**
> ur Relative should not of been able to mess the system up that bad, u need ur pw/administrator pw to do install/remove programs, and a lot of stuff requires sudo/gksudo, if u used sudo / gksudo in the last 15m before u gave the computer up to ur relative, u can decrease the timeout, otherwise sudo / gksudo will be active and available without a pw for about 15m.

 The story I got was a update showed up on task bar and he clicked it and system froze so he rebooted, like I said not sure what happened for sure. and sudo apt-get install does not work, I cannot even get to terminal just the recovery screen and it says put in apt-get install apt the ntells me command does not exist or something like that

---

### Post by nowshining on 2008-01-06
in recovery u don't need the sudo part, in updating, u can look at em' but to install them u need an administrator pw. :/ it should not of froze just clicking on the update icon at all. 

okay - boot with a live cd, 

open up a terminal in the live cd and issue

[B][I]sudo fsck -a -w -v /dev/sda1

no need to enter ur pw for the live cd

change /dev/sda1 to ur device if need be, /dev/sdaX

change X to the number other than 1 if need be
[/I][/B]

---

### Post by J11Gyro on 2008-01-06
use those commands even though it is a dual boot system  XP on master and Ubuntu on slave?

---

### Post by nowshining on 2008-01-06
hmmm u'll need to find out the /dev/ ubuntu is located on

it should work fine - 

if need be,

do this

in the live cd - open up a nautilus window

find the disk ubuntu is uninstalled on and double-click it or right-click - mount, from there open up system monitor

last tab - filesystems and find ur disk

in nautilus right-click it and unmount it, close nautilus and issue those commands,

sorry but u can either try it out amd try fixing it from the livcd - or keep booting again and again until the fsck auto-matically kicks in, ??

or wait until someone else comes along - don't have a dual-boot system - :)

---

### Post by J11Gyro on 2008-01-06
hoping it will work :)  trying it now

---

### Post by J11Gyro on 2008-01-06
Thank you very much. It worked in verbose with -v command  up and running thank you again :)

---

### Post by nowshining on 2008-01-06
ur welcome, what that did was scan the filesystem for errors and fix it, in windows the programs that are known to do things like fsck are scandisk and chkdisk
:)

---

