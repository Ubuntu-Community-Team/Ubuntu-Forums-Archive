---
title: "[SOLVED] NVIDIA is the Bane of my existence...."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by weeg on 2008-03-12
Alright everyone i'm hoping someone can help me out here. I'm new to Ubuntu and I really want to use it, but for some reason, I have been cursed with destructive fingers.... or something of the sort.

I have an NVIDIA GEForce 8400M GS video card. And i'm going to give you a little history of my problem and what I've tried doing from many many different posts. But i have yet to find a post that outlines my exact issue-hence my new topic.

I installed Ubuntu. Saw that my NVIDIA restricted driver was not enabled. I enabled it, restarted and had a nice desktop. Everything looked good.
I tried to enable desktop visuals and got an error about Dekstop settings could not be changed. Through a posting i discovered i didnt have the latest NVIDIA drivers. SO..... i update to this package NVIDIA-Linux-x86-169.12-pkg1.run.
After i installed that package, of course it shut down my sound and Atheros wireless card - no issue i just rebuilt the drivers. Ok, so i've got atheros working now and the sound works too.
Nvidia drivers and xserver work, so we're good.
then it told me i had to update. So silly me clicked yes.
It installed a slew of updates, and when my computer restarted, it went to the log in screen-i logged in- it sat at a orange default screen, then kicked me back to the log in screen again. Wow how fun was looping between those....
So i read another post that told me to shut down my nvidia-glx. Which i did. now i can get in to the desktop environment, but i cant use the desktop settings because i cant go higher than 640x480 res.
So i tried to install the other NVIDIA drivers that worked before.
To my maazement when i pressed CTRL-ALT-F1 or 2 or 3 or anything other than 7, there is no prompt, just a blinking cursor....

Im getting a little frustrated, partly because im still new and a little lost, and secondly because its frustrating.

Please can someone help me?
I dont want to reinstall everything. Cause when i do, i imagine im going ot have to update something, and then it will just mess me up again. :(

thanks

Ubuntu 7.10
Gnome 2.20

---

### Post by stchman on 2008-03-12
Download and use Envy.  From what I understand the restricted drivers in the repos do not support the 8xxx series of nvidia cards.  You will need later drivers and Envy installs them.

When you install Envy, click uninstall the nvidia driver and then install the nvidia driver.

Go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) for more info.

---

### Post by PmDematagoda on 2008-03-12
Kill the X-Server by going to a tty and executing:-
```
sudo /etc/init.d/gdm stop
```
and then execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
select any options that match your PC, after that is done reboot your PC with:-
```
sudo restart
```
See if that solves your problem.

---

### Post by weeg on 2008-03-12
I did try killing the x-server, the problem was once i did, i had no prompt in the F7 space. I tried to switch to F2 or F3, but they were just a blank screen with a blinking cursor.

I will try installing with Envy, and see where that takes me.

---

### Post by drubin on 2008-03-12
[http://ubuntuforums.org/showthread.php?t=692827](http://ubuntuforums.org/showthread.php?t=692827) 

Take a look  the 3rd post, it worked for me, when nothing else did.

---

### Post by weeg on 2008-03-12
it would work, except i dont have a prompt in F1 F2 F3 or any other instances.

I'm just about to boot into ubuntu to try downloading envy.... i'll be back shortly.. i hope

---

### Post by weeg on 2008-03-12
So.... I installed envy. I asked it to install the NVIDIA Drivers. It went through a lengthy process, built a bunch of stuff. then i restartrted...which took forever mind you... and im back at my dekstop. However, i've gone from 800x600 (before envy) to 640x480 now with Envy. I also cant change my resolution. which means that I cant see any of the options i need to select in the Envy screen, or the NVIDIA x server screens. I'm so lost... AHHH

---

### Post by Peter09 on 2008-03-12
You can move your window around by using the Alt+left mouse key to get to the options you need.

PC

---

### Post by PmDematagoda on 2008-03-13
Boot Ubuntu in Recovery Mode and then execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After reconfiguration is done, restart Ubuntu with:-
```
sudo restart
```

See if that can get you back to a working desktop.

---

### Post by Sef on 2008-03-13
> Download and use Envy. From what I understand the restricted drivers in the repos do not support the 8xxx series of nvidia cards. You will need later drivers and Envy installs them.

Not correct.  I have an 8600, and it works just fine with the restricted drivers.  8800 had a problem working correctly, but they are a fairly new card.

---

### Post by PmDematagoda on 2008-03-13
> **Sef said:**
> Not correct.  I have an 8600, and it works just fine with the restricted drivers.  8800 had a problem working correctly, but they are a fairly new card.

Very true, if you take a look around you would see very few threads(if any) that concern people having problems with their 8600s after they install the drivers using the RDM, unfortunately this does not hold true for the 8800 VGA card.

---

### Post by weeg on 2008-03-13
i tried the recovery mode. 
Firstly it didnt ask me for a password when using the sudo command, that was weird but whatever.

the first command worked.
the second command = 
sudo: restarts: command not found

I'm just restarting manually i guess.

---

### Post by weeg on 2008-03-13
ok so i restarted and i got in to the desktop environment with an awesome resolution, and everything worked..... except i cant apply the custom or high desktop settings. When i click apply them, it asks me to enable the 3D drivers for Nvidia. It says without them i cant use the special effects.
So i clicked yes, and boom it took me back to the crappy low res upon restart where i have to pick a resolution and something about running in low graphics mode. It's like a vicious circle i can't escape from :(

---

### Post by Therion on 2008-03-13
Okay been here, had this problem with my nVidia 8800.  The problem is not insurmountable.  In reading the posts prior, it appears to me you have downloaded the most recent version of Envy from the website, yes?  That's important... If that's NOT correct then GO to the Envy website and download and install Envy.

Run Envy (from the command prompt if you need to (use **envy -t** in the Terminal to run Envy in text-mode)) and allow it to install the driver and reconfigure your xorg.conf file.

Reboot.

Go to the Restricted Drivers Manager and "Enable" the Restricted Driver.

Reboot.  When you reboot, your resolution will be hosed... That's okay; do NOT panic.  We're going to fix that right now...

Manually edit your xorg.conf file:
```
sudo dpkg-reconfigure xserver-xorg
```
Accept all the default settings until you get to the screen where you can choose monitor resolutions.  

Choose three resolutions and de-select the ridiculously low ones (like 600 x 480).
Remember that the HIGHEST RESOLUTION YOU CHOOSE HERE WILL BE THE NEW DEFAULT RESOLUTION.

Save, Exit, etc. and you should be golden.

---

### Post by weeg on 2008-03-13
Love your suggestion!!
The only problem.... I dont have a ALT-CTRL-F1 or F2 or F3 prompt to enter the commands into after i kill the gdm or xserver.

So should i reboot in to recovery and manually reconfigure?

---

### Post by Therion on 2008-03-13
You've downloaded the latest version of Envy, right?  If so, then yeah... Boot into Recovery Mode and when you get dumped out at the command prompt:```
envy -t
``` to run Envy in text mode... Install driver, Enable driver, Reboot again <sigh> so you can edit xorg, selecting the proper resolutions yadda yadda yadda... 
And reboot one. More. Time.

This damn well better work!!!  Crossing my finger's for you.

---

### Post by weeg on 2008-03-13
It worked!!
Thansk so much guys!!

this is now awesome. Now i just gotta figure out what im gonna do with my new awesome Ubuntu desktop!!!!!

Weeee fun. 

Again, many thanks to everyone who tried to help!!

---

