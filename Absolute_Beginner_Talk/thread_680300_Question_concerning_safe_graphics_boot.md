---
title: "Question concerning safe graphics boot"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by ghoss00 on 2008-01-27
After installing Ubuntu AMD 64 alt my system locked after the first menu during the first boot.  After several tries, I booted using the "safe graphics", loading began but halted waiting for input.  The final line read : root@glen:~#  The curser is flashing awaiting input.  I have "Ubuntu Linux Bible" but can''t seem to fine the correct response.

---

### Post by nowshining on 2008-01-27
ur in recovery mode

:)

the command is

startx

but u'll be warned that ur using root privs just click continue or at the prompt

type

apt-get update

once done

apt-get upgrade

:)

and install all updates if need be :) I'm assuming u have ethernet - if so then u'll already be connected. After that - reboot and try again.

---

### Post by ghoss00 on 2008-01-27
> **nowshining said:**
> ur in recovery mode

:)

the command is

startx

but u'll be warned that ur using root privs just click continue or at the prompt

type

apt-get update

once done

apt-get upgrade

:)

and install all updates if need be :) I'm assuming u have ethernet - if so then u'll already be connected. After that - reboot and try again.
Thanks,  that got me into root, or so it seems.  But it seems that my graphics card is locked out.  I have an ATI graphics card which may be my problem.  Any recommendations as to a Linux friendly graphics card?  Also, it seems that I could not get my network card working.  This may be due to the need to reboot my cable modem and router after I got hung since others were having trouble accessing the internet.  

I tried to restart my system but seem to be at the same line as before root@glen:~#
How do I properly shutdown or restart from this point?

Many Thanks for your help!!

---

### Post by nowshining on 2008-01-28
there are several ways

type 

reboot

shudown now -r

ctrl+alt+del keys on ur keyboard

:)

Nvidia is a nice brand and supports linux well - however u'll have to find some threads on setting up ATI and by the way by default u should be back at ur ol' non recovery mode on u reboot, is ur get a CLI screen or want one, and it freezes again do this

press ctrl + alt + f1

press

ctrl + c

sudo /etc/init.d/gdm stop

enter ur pw as usual - it won't show as u type

then after that get back online from this other computer to continue on from here by me or if another comes by to assist u.

or

at the command prompt u can try

startx

and see if it freezes on u at that point...

if u get a freeze when trying to logout - tha'ts normal with gutsy - it's a known and won't be fixed bug, u can go thru my site in my sig to find a workaround on it :)

---

