---
title: "Installing help required"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by nadeepa on 2007-12-08
Newbie here!
I'm trying to install ubunty 7.10 as a dual boot with Win XP.
But when I boot with ubuntu live CD and select install, after few minutes a blank screen comes and nothing happens thereafter. Not even the live CD loads..
Please help me out here

Thanks a lot

---

### Post by bren on 2007-12-08
there are a few possibilities.....

1) what is your hardware (processor / memory)
2) it could be bad CD - see instructions on how to check CD on main ubuntu site
3) it could be you have low RAM and computer does not have enough to run LIVE CD in GUI  version.   If so then you can download and burn the "alternate CD".   No live try before you install but installs in more cases

bren

---

### Post by PmDematagoda on 2007-12-08
Post the specifications of your PC.

Another thing, please make the problem a little more clearer as I cannot really understand what your problem is.

---

### Post by nadeepa on 2007-12-08
Thanks for your info!

CPU :AMD 64 x2 Dual core 3600+
RAM: 512 MB
HDD: 80 GB
MB: Gigabyte GA-M61VME-S2

I have already checked the CD. CD does not have any errors.

nadeepa

---

### Post by atlfalcons866 on 2007-12-08
whats your video card?

---

### Post by nadeepa on 2007-12-09
My Video card is onboard on the Mother board.

I have installed ubuntu using the alternate CD. After I select Linux 7.10 on Grub loader, the boot loader would begin booting Gutsy Gibbon. An Ubuntu loading screen appears with a bar underneath it showing the progress of the bootup.

Lately however, this screen just disappeared and is simply replaced by a blank black screen. 

What happened? I didnt change anything in my screen settings. Is there a way I can get it back?

Thanks

---

### Post by Velcor on 2007-12-09
I recently had the same problem after I switched graphics cards, never was able to figure it out though, since the hard drive died within the week. :(

---

### Post by PmDematagoda on 2007-12-09
When you reach the list of booting Ubuntu, edit the entry for Ubuntu by pressing "e", once that is done, edit the line with the kernel like this:-
```

kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=f155c3b9-00c5-4a8c-9fe3-fc71fa758e61 ro quiet splash 

```
And remove the splash and quiet.

Then press "b" to boot Ubuntu, see if that solves your problem.

---

### Post by nadeepa on 2007-12-09
VGA: NVIDIA GeForce 6100 nForce 400

---

### Post by nadeepa on 2007-12-09
PmDematagoda, 
thanks for your info. But it didn't worked..Is there a problem in VGA?

---

### Post by whitenight639 on 2007-12-09
you said it was a dual boot right? 

you could try booting from your windows partition and accessing the log files from ubuntu (ive never run a dual boot so not sure if you can see the other partition as its on the same disk) however if you can get access to them and post the output we might be able to help.

---

### Post by nadeepa on 2007-12-13
Dear All,

Thank everyone for your support.
I've solved my problem. The problem was with the monitor. My monitor (Philips 104S) is not available in the ubuntu hardware list. Therefore in the startup, ububtu uses a higher resolution and a higher refresh frequency. After I manually edited the settings, everything was fine.

Thanks and regards

Nadeepa

---

