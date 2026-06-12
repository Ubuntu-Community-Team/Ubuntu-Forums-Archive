---
title: "Hardship with NVIDIA GT750M"
date: 2013-04-24
forum: Any Other OS
---

### Post by jqx1990 on 2013-04-24
Several days ago, my new laptop, Lenovo Y400 arrived (what is for Y400 should also work for Y500). I was very happy b/c it has a wonderful graphic card, GT750M. One thing that is not so happy is that GT750M doesn't really have official support. For some reason, I had to format the whole hard drive to get the Win8/Ubuntu dual boot work. I forgot to backup the drivers (for Win8). So I went to Nvidia Official site and surprisingly I found no driver to GT750M. So I went to Lenovo support site. They did have a link for it, but when I clicked the link, I got "file not found." All I am saying is that GT750M seems to be a customized product for Lenovo only. Finally I went to Lenovo China and got the driver downloaded.

Okay, now, it's about Ubuntu (Sorry about the long paragraph of complaint... :)

So, as you can imagine, it won't be supported well by Ubuntu (Not quite Ubuntu, but mostly. I have Linux Mint 14 KDE amd64). I went to Additional Drivers (yes, they still have it with KDE), and as I expected, no proprietary driver is found (why do I want proprietary driver? b/c I need to adjust the brightness of my screen). So I decided to directly install nvidia-current. It didn't work. KDE didn't start. I have to remove it in console. But then I tried nvidia-experimental-310, and amazingly, it worked!

Now that I can adjust brightness through nvidia control center (Fn key doesn't work though).

---

### Post by llpind on 2013-04-28
I'm in the same boat.  Thanks for the tip, i'll try that out.  I've tried nvidia, nvidia-current.  Nothing seemed to work.  Also tried to get the brightness buttons to work using the tutorial:
[http://forum.notebookreview.com/ideapad-essential/716609-tutorial-lenovo-y500-ubuntu-linux-brightness-key-fix.html](http://forum.notebookreview.com/ideapad-essential/716609-tutorial-lenovo-y500-ubuntu-linux-brightness-key-fix.html)

that didn't work for me either (probably because of the drivers).  Anyway i'll try the experimental one.  Thanks

---

### Post by llpind on 2013-04-28
okay that really messed stuff up.  Now i can't even revert back.  I'm stuck at 800X600.  Here is what i did:
sudo apt-get install nvidia-experimental-310

Stuck at 800X600.  when i try to open nvidia settings: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  Running that command does nothing and i continue to get the error.


i tried to 'sudo apt-get autoremove nvidia-*', but it went to even worse resolution.  Can anyone point me in the right direction?  I really don't want to install ubuntu again.  Thanks!

---

### Post by llpind on 2013-04-28
I replaced xorg.conf with xorg.conf.failsafe and I've got the nice 1080p display back, but still no brightness control :(  this sucks

---

### Post by bcschmerker on 2013-04-29
As I understand things, nVIDIA® should support both the GeForce® GTX&#8482; 750 and GeForce® GT&#8482; 750M as of 28 April 2013 (package: nvidia-current-updates); I reckon that both are too recent for open-source support in the Package xserver-xorg-video-nouveau.  I have to use the nvidia-current-updates package on my old eMachines®/Acer® EL1210-09 as retrofitted with a Shuttle® PSU and Asus® EN210/DI/512MD3(LP) under Ubuntu® 12.04.2-LTS, as xserver-xorg-video-nouveau can only drive one GPU and I have two running on the system cited (both the planar GeForce® 8400 and the add-on GeForce® GT&#8482; 210).

---

### Post by jqx1990 on 2013-04-30
> **llpind said:**
> okay that really messed stuff up.  Now i can't even revert back.  I'm stuck at 800X600.  Here is what i did:
sudo apt-get install nvidia-experimental-310

Stuck at 800X600.  when i try to open nvidia settings: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  Running that command does nothing and i continue to get the error.


i tried to 'sudo apt-get autoremove nvidia-*', but it went to even worse resolution.  Can anyone point me in the right direction?  I really don't want to install ubuntu again.  Thanks!

Hi llpind, I am sorry it didn't work out for you. But are you sure your graphic card is GT750M? I tried similar things with a different graphic card, that's exactly what I got. Also, when you are not able to use the driver, just sudo apt-get remove nvidia-experimental-310

---

### Post by jqx1990 on 2013-04-30
Updates:

I can't resist Ubuntu 13.04, so I just installed it. Similar to LinuxMint Nadia, it couldn't figure out my graphic card. So I did the same thing. And it worked.

---

### Post by wikihunter on 2013-05-20
The brightness setting in nvidia-settings is not true brightness control.  It doesn't actually use less power that way.  Does anyone have the ability to actually control backlight for real?  I've tried appending kernel parameters such as acpi_osi=xxx, that are all posted on several forums, but none of them work.  As a result, the battery drains way too quickly.

---

### Post by wikihunter on 2013-05-20
Like I posted in the jumbo y500 thread:  [http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063), this gpu should work with nvidiabl as soon as it is updated with a line identifying its pci id.  The card is simply too new.

---

