---
title: "Uncompatible Graphics Card?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by lilro on 2007-05-26
hey i have a NVIDIA card, but im not sure of the model and every time i try to install the drivers i get a bunch of problems and have to reinstall feisty. i've tried downloading the drivers directly from the nvidia site which didn't work, then i tried [this]("http://ubuntuforums.org/showthread.php?p=2725570#poststop") and when i rebooted i got a big NVIDIA logo that wouldn't go away so i turned off my computer via power button and left it for a few minutes then turned it back on and the nvidia logo was mixed with the login screen and i logged in and did this:

```
sudo dpkg-reconfigure xserver-xorg
``` and rebooted again and now it doesn't work at all. i see the ubuntu loading screen then when it finishes i get a blank black screen. so im stuck with the live cd for now. can anybody help me?

---

### Post by Enverex on 2007-05-26
To find out the model do "lspci" in a terminal and it should list an nVidia display adapter.

---

### Post by lilro on 2007-05-26
here's my output:

```
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Unknown device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:07.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
ubuntu@ubuntu:~$ 


```

im a noob to this so i don't know which one to look at. any help would be appreciated.

im guessing its this:**02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)** but i didn't see that exact model on the nvidia site. i saw geforce2, then i saw mx in a seperate download. so im unsure of what to do.

---

### Post by overdrank on 2007-05-26
Hi the last one is the graphics card
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
I have found this to install your drivers 
sudo apt-get install nvidia-glx-legacy
Hope this helps good luck!

---

### Post by lilro on 2007-05-26
is there a way i can install that on my previous installation as im on my live CD now.

---

### Post by overdrank on 2007-05-26
> **lilro said:**
> is there a way i can install that on my previous installation as im on my live CD now.

Yes, sudo dpkg-reconfigure xserver-xorg
Choose the versa driver. Then you should be able to install the proper drivers after boot.

---

### Post by lilro on 2007-05-26
i tried that and that's what messed me up. it's in my first post.
i'll try again though.

EDIT: do you mean *Vesa* driver because i don't see Versa

---

### Post by overdrank on 2007-05-26
> **lilro said:**
> i tried that and that's what messed me up. it's in my first post.
i'll try again though.

EDIT: do you mean *Vesa* driver because i don't see Versa
Yes sorry!:KS

---

### Post by lilro on 2007-05-26
nope still no go. when i enter sudo dpkg-reconfigure xserver-xorg, what are the other options supposed to be set to?

---

### Post by overdrank on 2007-05-26
> **lilro said:**
> nope still no go. when i enter sudo dpkg-reconfigure xserver-xorg, what are the other options supposed to be set to?

You can just select the default with the vesa driver!;)

---

### Post by lilro on 2007-05-26
but when i enter the command, there is other questions that it asks and some of them i have no clue about.

---

### Post by icechen1 on 2007-05-26
> **lilro said:**
> but when i enter the command, there is other questions that it asks and some of them i have no clue about.

Ignore them as they are set to default if you don't change them.

---

### Post by overdrank on 2007-05-26
> **lilro said:**
> but when i enter the command, there is other questions that it asks and some of them i have no clue about.

Yes and the answer should be there as default. If there is a blank then fine if it lets
you proceed. We are just trying to get you back to the desktop and the install the proper drivers!:p

---

### Post by lilro on 2007-05-26
ok i appreciate the help. i will try again lol.

---

### Post by lilro on 2007-05-26
grrr...still not working, maybe i should try default instead of vesa? or would that be a bad idea

---

### Post by Happy_Man on 2007-05-26
Vesa *is* default..... have you tried logging in to the recovery mode and entering this, or are you still able to login to a desktop?

---

### Post by hessiess on 2007-05-26
try setting the driver to nv, when you installed the driver it should have baked up your old xorg conf, then it usaly ses use (command) to return to your old xorg thingie

dont type command, lol!

---

### Post by lilro on 2007-05-26
> **Happy_Man said:**
> Vesa *is* default..... have you tried logging in to the recovery mode and entering this, or are you still able to login to a desktop?

my default is nv. i have to scroll to vesa. and im doing it from the live cd. should i be doing it from recovery?

[QUOTE=hessiess]try setting the driver to nv, when you installed the driver it should have baked up your old xorg conf, then it usaly ses use (command) to return to your old xorg thingie

dont type command, lol![/QUOTE]

i tried using nv as well and it still wont do any thing. i get the loading screen with the ubuntu logo and the orange loading bar and once it completes i have a black screen that does nothing.

---

### Post by Happy_Man on 2007-05-26
You should be doing this from recovery mode, not LiveCD! It's an option in GRUB.

Since you were doing it from the LiveCD, nothing on your HDD changed; hence your recurring problem.

---

### Post by overdrank on 2007-05-26
> **Happy_Man said:**
> You should be doing this from recovery mode, not LiveCD! It's an option in GRUB.

Since you were doing it from the LiveCD, nothing on your HDD changed; hence your recurring problem.

Thanks Happy;)

---

### Post by lilro on 2007-05-26
thanks a bunch you guys. it works now. i had to reboot a few times though.

---

### Post by overdrank on 2007-05-26
> **lilro said:**
> thanks a bunch you guys. it works now. i had to reboot a few times though.

Glad to hear you are going in the right direction!:popcorn:

---

### Post by HeppY on 2007-05-26
hi all! please help! one is a apsolut beginer in linux at all! my first is ubuntu 7.04, i manage to install and run dual boot with win XP but i cant run xorg 4 use with byril, only vesa drivers work, cant  install nvidia 7800 gtx drivers, try to falow directions on Ubunto How-To exactly but its not working 4 me, provide log file and go to console mode after restart! try to run it from system/ administration/ restricted drivers manager where is listed as a NVIDIA accelerated graphics driver but again not working :(
can anyone help? 

07:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)

---

### Post by lilro on 2007-05-26
what's the command to disable the driver? because its not enabled but i fear that once i enable it i will be stuck again.

---

