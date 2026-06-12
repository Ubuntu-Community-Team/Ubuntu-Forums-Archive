---
title: "what is runlevel?"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by kimes on 2005-05-29
When I researched about how to start  some programs at bootup, I heard about runlevel many times.. but I couldn't figure it out what exactly means?

What's runlevel?

And I also found that init script rcS.d or something like that( I dont know exactly since I'm on the windows machine now  :| ) has many kind of versions depending on runlevel.. is this correct?

As far as I know in windows machine there's not that kind of thing.. so I'm so confused, help me to figure it out..

many thanks

---

### Post by tread on 2005-05-29
Basically, it's startup scripts. You go in runlevel 2, some programs/services get started, you go into a different runlevel, some other programs/services get started.

You can edit this by installed sys-rc-conf I think ... or UBM .. Ubuntu Bootup Manager.

---

### Post by phen on 2005-05-29
[QUOTE=tread]Basically, it's startup scripts. You go in runlevel 2, some programs/services get started, you go into a different runlevel, some other programs/services get started.

You can edit this by installed sys-rc-conf I think ... or UBM .. Ubuntu Bootup Manager.[/QUOTE]
 There are several runlevels:
0: Halt
1: Multiuser without network
2: Multiuser with network
3: The default (network with Xserver)
4: not used
5: not used
6: reboot

this information is for RedHat Linux. I am sorry, i dont know exactly for Debian based distributions like Ubuntu. 

Now, look in /etc/init.d/ - there you will find scripts to start up all services of your computer. Now take a look in /etc/rc3.d/ this is runlevel 3's directory. You will find links to the init.d directory looking like this: "S1pppd" This link Starts as the first entry the pppd service. K11anacron means that anacron is Killed when entering the runlevel. The other directories rc0.d rc1.d have other links inside, and therefore are doing different things when your computer enters them.

so, if you like to add an program to your startup, you should edit /etc/init.d first, and then make a symlink from S99yourservice to /etc/init.d/yourservice

hope this helps!

you can also try to type sudo init 0, this is the equivalent of shutdown -h now. or just try sudo init 5 and then back sudo init 3, you Gnome should reappear. (never tried the runlevels under ubuntu, just converted from redhat!)

cheers,
kai

---

### Post by ar0d on 2005-05-29
if you want to customize go to /etc/inittab is the file to customize your runlevel. just read it, you'll get a good understanding of what it does. for exsample
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.
is the default levels. I found that by just looking in that file....

---

