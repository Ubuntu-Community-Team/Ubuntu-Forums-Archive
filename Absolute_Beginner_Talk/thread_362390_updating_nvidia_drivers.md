---
title: "updating nvidia drivers"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Psyphre on 2007-02-15
My screen is off centre in ubuntu (xp and everything else is fine) and someone told me that upgrading my nvidia drivers would solve this. How would I do that?
Thx!

---

### Post by Perfect Storm on 2007-02-15
Download the driver from Nvidia.com to your Desktop, then;
[http://ubuntuforums.org/showpost.php?p=2148710&postcount=16](http://ubuntuforums.org/showpost.php?p=2148710&postcount=16)

---

### Post by Psyphre on 2007-02-15
are you sure that was correct?

I downloaded the drivers and followed the steps in the link.

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo /etc/init.d/gdm start

The first line worked,
The second line worked,
The third line said it couldnt find any files or directories,
and the fourth line.... completely shut down the GUI. All i had was a black screen...

Am i doing something wrong?
thx

---

### Post by Perfect Storm on 2007-02-15
No, that sounds right, the third line makes sure there aren't any leftovers.
You need to shutdown gui to make it work.

Print the instruction out or write them down if you can't remember it.

---

### Post by ehowell on 2007-02-15
When I was done installing drivers the screen was still off center. I didn't want to fix it with the monitor control panel since I dual boot Windows and then THAT would be off center.

I ended up running xvidtune to get a modeline which I added to the xorg.conf file as [described here]("http://www.xenocoder.com/blog/archiveposts/54").

Good luck with it!

---

### Post by rsambuca on 2007-02-15
I have 6 different OS's on my rig right now, and for some reason XP and Vista both center OK on the monitor, and the linux distros were all off to the left.  I just used the manual adjustments on my monitor a couple of times, and now somehow the monitor "remembers" the settings for each distro.  I have no idea how or why, just that it works.  When I re-install, I have to manually readjust once again, but only a couple of times.

---

### Post by Patrick K on 2007-02-15
I found the same thing.

---

### Post by Psyphre on 2007-02-16
thx for the replies. Unfortunately updating wont seem to work. When it goes to the blank screen, nothing works. No commands i type in seem to do anything.

---

### Post by Perfect Storm on 2007-02-16
Then <ctrl>+alt>+F1> before typing the commands.

---

### Post by Psyphre on 2007-02-16
Thx artificial intelligence.
afraid i tried another method and have subsequently made a mess of everything....

---

### Post by TheOther on 2007-02-16
Is this helping?

My ubuntu started (after installing) with 75Hz signalling to the monitor. When I addusted it to 60Hz the screen moved to the right. (Menu: System; Preferences; Screen Resolution) Unfortualy the login screens are still to the left. May be someone knows where these settings are stored in for the login screens?

---

### Post by old_geekster on 2007-02-16
Here is the link to my favorite way to update to the latest nVidia drivers (1.0-9746):

[http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

Along with the drivers, it will install "NVIDIA X Server Settings" in Applications/System Tools.  You can setup your monitor from there. 

I am a tweaker and because of this, I have more problems than most.  My cure for doing something wrong is to do a new complete install.  I have done this 11 times in the past two weeks.  The guide I provided has worked at least 9 of those times.

Good luck!

p.s. Be sure to write down the commands that he recommends, because you will have to exit to a command line.

---

### Post by Repent on 2007-02-16
I think this has to be the easiest way to update drivers I have seen, give it a try you wont be sorry.

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) 

And it installs everything his does. ^

---

### Post by Psyphre on 2007-02-17
theother: i think i only have 60hz. So i cant try switching to 75.

old_geekstar & repent: thx , im gonna read thru both your suggestions and try them. I'll try repent's first since you claim it to be easier!

---

### Post by Psyphre on 2007-02-17
Wow repent, that really WAS easy. Thx so much everyone for the help!

---

