---
title: "Killed my Xsession"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Aximilli on 2006-05-14
So I installed Ubuntu on my main computer to dual boot with XP. I have an ati radeon 9600 series video card, and I wanted to set up ubuntu to use my dual monitor setup. I went through the wiki help guide on installing video drivers, and I ended up giving it the wrong drivers and/or values, so now i can't get xsession, and I don't know enough yet to make my way around in the terminal. So my questions are:

1. How do I reset the drivers so I can get gnome back? and
2. What's the proper way to set up my dual monitor display?

Thanks

---

### Post by roachk71 on 2006-05-14
I[LEFT]
I wish I could help you with the dual-monitor configuration, but I never could get that to work in Dapper (or Breezy, for that matter) on my low-end ATI.

I can, however, help with getting your X-session back. First, you unfortunately do have to use the terminal. Log in from that and type:

```
sudo dpkg-reconfigure --phigh xserver-xorg
```
and reboot, using sudo reboot. If this doesn't solve the graphical log-in problem, you'll have to manually configure Xorg yourself using the same command:

```
 sudo dpkg-reconfigure xserver-xorg
```
supplying the correct information for your graphics card, monitor, mouse and keyboard, then reboot once more.

A Special Note: Using the --phigh option sets X up with default values for your card, which could be a bit inefficient. Using a manual configuration is recommended.

Also, look in your /etc/X11/ directory for the files xorg.conf, and any backup files (usually with the date and time stamped at the end, replacing the new xorg.conf with your backup:

```
sudo su
cd /etc/X11/
mv xorg.conf xorg.bak
mv xorg.conf.{datestamp} xorg.conf
```

and reboot.[/LEFT]

---

### Post by Aximilli on 2006-05-14
I went through dpkg-reconfigure xsession-sorg and still have the same problem. I'm probably doing something wrong on that end. 

But I first tried your idea, sudo dpkg-reconfigure --phigh xserver-xorg, and it wouldn't execute, said invalid option -p. 
I am lost.

---

### Post by Aximilli on 2006-05-14
Ok I have it working now. I modified the code you gave me, sudo dpkg-reconfigure --phigh xserver-xorg, by removing one of the dashes in fron of phigh, and it worked fine. Thank you very much for your help

---

