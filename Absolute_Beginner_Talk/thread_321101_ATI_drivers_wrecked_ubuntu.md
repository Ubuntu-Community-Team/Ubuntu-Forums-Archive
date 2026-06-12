---
title: "ATI drivers wrecked ubuntu"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by blake1 on 2006-12-18
I have just installed the Raedeon x300SE drivers, and restarted, but now I have got a command line and no gui.

I have tried startx but it says:
```
Fatal Server Error:
no screens found.
XIO: fatal IO error 104 (Connection reset by peer) on Xserver ":0.0" after 0 requests (0 know processed) with 0 events remaining.

```

What is wrong?

---

### Post by rune_kg on 2006-12-18
Hi

Probably your /etc/X11/xorg.conf file is incorrect.

Correct the errors or replace with your backup xorg.conf. If you did'nt create one yourself there might be a backup called xorg.conf.fglrx-0 in the same dir.

Then restart graphics with:

sudo /etc/init.d/gdm restart

Hope this helps!

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by TooRight on 2006-12-18
I kept having the same problem... my computer does nottttttttt like that radeon driver at all. I never did get it to work. Were you using the fglrx driver before?


**** My comp liked the fglrx driver just fine, and then when i wanted to install beryl I installed the ati propriatory driver instead.



When the radeon attempts would mess up my system, I'd cd into the X11 folder and then at the next prompt type ls to have it list the contents, then I'd go through doing a "sudo nano oldxorgfilename.whatever" on each of the xorg.conf backups until i found a usable one from before, lol, then I'd copy it to the present xorg.conf file by "cp xorg.conf oldxorgfilename.whatever" and at the next prompt, type:

> 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo depmod
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now


and after the reboot, my system was fine again :D

---

### Post by blake1 on 2006-12-19
> **TooRight said:**
> I kept having the same problem... my computer does nottttttttt like that radeon driver at all. I never did get it to work. Were you using the fglrx driver before?


**** My comp liked the fglrx driver just fine, and then when i wanted to install beryl I installed the ati propriatory driver instead.



When the radeon attempts would mess up my system, I'd cd into the X11 folder and then at the next prompt type ls to have it list the contents, then I'd go through doing a "sudo nano oldxorgfilename.whatever" on each of the xorg.conf backups until i found a usable one from before, lol, then I'd copy it to the present xorg.conf file by "cp xorg.conf oldxorgfilename.whatever" and at the next prompt, type:



and after the reboot, my system was fine again :D

Thanks so much! It now works perfectly. :-D

---

### Post by TooRight on 2006-12-19
Awesomeeeee, glad to hear it!! :D

---

