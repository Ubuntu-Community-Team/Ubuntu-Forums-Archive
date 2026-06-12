---
title: "System seems slow under ubuntu 7.04"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by _dinsdale_ on 2007-07-10
Hi all,

New to the world of Linux. Have just installed ubuntu 7.04 onto my old WinME machine: Pent II 350 with 320MB Ram.

ubuntu is on one drive, WinME on the other. ubuntu does all the boot managing which seems to work fine.

ubuntu works well enough finding all the hardware and peripherals BUT the system seems much slower to load applications than WinME on the same system. Even net surfing with ubuntu seems slower than ME with both systems using Firefox and exactly the same LAN set up.

I haven't done anything more than download all available updates offered. Are there tweaks that I should be using to get ubuntu to use my system better? I haven't done anything like download specific drivers, just allowed ubuntu to find and install defaults... if it even does this.

Like I said, I'm new to this OS and ready to be converted if ubuntu shows me it is worth the pain.

thanks in advance

Dins

---

### Post by macogw on 2007-07-10
Xubuntu would be better on that system.  I have a similar one (192MB RAM though).  Xubuntu uses Xfce, which is a lightweight desktop environment.  GNOME is a bit heavier and better for more modern computers...like trying to run something as heavy as XP on that computer (I've done it, not pretty).  You can get Xubuntu's stuff with "sudo apt-get install xubuntu-desktop" then on the login screen if you click options > sessions, Xfce will be an option.  That'll run faster.  Other lighweight options for desktop environments you can use on Ubuntu instead of GNOME include Enlightenment 16 , Fluxbox, and IceWM.  Fluxbox and IceWM aren't as newbie-friendly of environments, but they're not bad.  IceWM has a menu in the bottom left by default, but you can also get it by right clicking on the desktop.  Fluxbox's menu comes from right-clicking on the desktop too.  I haven't use Enlightenment, but it's a very pretty environment.

---

### Post by regomodo on 2007-07-10
Ubuntu (Gnome+Metacity) is not suitable to your computer. 

You are comparing a 9(?) years OS with a current OS.

I suggest Xubuntu for your computer. To do this enter your terminal and enter

```
sudo apt-get update && sudo apt-get install xubuntu-desktop
```

enter your password and wait to hit "y"

If you like Xubuntu (pure xfce) and want to free up hard drive space follow the guide in ayisu's website 

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

His/her site is good if you really want to make your comp' fly. I followed his ubuntu serer with icewm install guide. Uses 28MB once logged in

---

### Post by misfitpierce on 2007-07-10
Indeed Xubuntu may be the way to go. Faster on newer or older machines.

---

### Post by _dinsdale_ on 2007-07-10
Thanks all for the quick replys. Understand that the OS I have installed is too heavy for the system. However tried the terminal code suggested and got the reply "E: Couldn't find package update". Still very new at this so perhaps doing something basically wrong. Do I need to download something before I run this code?

Dins

---

### Post by macogw on 2007-07-10
It's not "sudo apt-get install update" it's just "sudo apt-get update" It tells the computer what the list of available-to-install programs are.

---

### Post by regomodo on 2007-07-10
> **macogw said:**
> It's not "sudo apt-get install update" it's just "sudo apt-get update" It tells the computer what the list of available-to-install programs are.

Yeah, i sorted it. Cut me some slack. The sun's about to rise.

---

### Post by _dinsdale_ on 2007-07-10
Sorry spoke too soon. Tried macogw's simpler code with more success. Will update when finished. Thanks again.

Dins

---

### Post by _dinsdale_ on 2007-07-11
OK after a false start I'm in with the new light OS. Thanks for the help. Look forward to looking under the bonnet.

Cheers

Dins

---

### Post by RedSquirrel on 2007-07-11
> **_dinsdale_ said:**
> OK after a false start I'm in with the new light OS. Thanks for the help. Look forward to looking under the bonnet.

Cheers

Dins
Once you get a bit more comfortable with linux, you might want to try a truly lightweight install:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

You will install just the base system, a window manager, and Synaptic. You can install other applications as you need them, rather than having a whole bunch of applications installed that you may never use. ;)

---

