---
title: "Resolution stuck at 1024x768"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by jarvis13 on 2007-03-04
So I just did a clean install of Herd 5 and I can't get my resolution to change from 1024x768. 
Usually this is solved right after I install my nvidia drivers, but this isn't the case this time for some reason.
I need to get it to 1280x800. is there any way to do this without editing my xorg?

---

### Post by GameManK on 2007-03-04
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

basically:
sudo dpkg-reconfigure xserver-xorg

and choose the right resolution

---

### Post by jarvis13 on 2007-03-04
sudo dpkg-reconfigure xserver-xorg looks really scary. 
I don't even know what i need to enter in all these fields. 
I'll give it a shot and see what happens.

---

### Post by jarvis13 on 2007-03-04
welp. that caused my stuff to crap itself to death. 
i think i did it wrong.

---

### Post by GameManK on 2007-03-04
> **jarvis13 said:**
> welp. that caused my stuff to crap itself to death. 
i think i did it wrong.

you basically need to choose all default options except choose nvidia for the driver and the correct resolution

---

### Post by mrmonday on 2007-03-04
I think the easiest way to solve your 'sudo dpkg-reconfigure xserver-xorg' problem is to get an automated program to do it for you - do you agree? You can use [envy]("http://www.albertomilone.com/nvidia_scripts1.html"), which will reconfigure your xserver-xorg automatically for you, and also install/uninstall graphics drivers (if you want) for you. You need to enable all repositories to use it for driver though.

EDIT: Using the function for un/installing drivers saves a lot of messing around :)

---

### Post by zhangqt on 2007-03-08
Thanks a lot.
I've just resolve my problem with motherboard msi k8ngm2-l and monitor
of WE1920wmb.I have change the resoultion from 1025X768 to 1440X900(default
resolution in WinXP) successfully.

---

