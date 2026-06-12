---
title: "New to Linux! Several issues, please help!!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by BHTX84 on 2007-03-13
Ok, so...I'm 23 years old, and have known nothing but Windows since 3.1 days.  Having been using XP pro and never even seen Linux before, I just completely formatted my drive in this HP Pavilion 750n (old), in an attempt to learn Linux and rid myself of Microsoft, cold turkey.  Probably not a smart idea, but..whatever...

So anyway, I finally manged to connect to the internet, as it's my only resource for help, but I was only able to do so by bypassing my Belkin Pre-N wireless router and matching adapter...connecting via ethernet cable directly to the modem.  My wireless adapter wasn't shown in Networking Settings, and I didn't know what else to do..

First thing's first though... I use a 67" Samsung 1080p DLP as my display, and sit back on the couch with a Logitech Bluetooth keyboard/mouse.  My previous resolution in XP that I used was 1280x768 (almost 16:9).  However, I can't seem to get anywhere near that right now.  Device Manager shows my display adapter as NV5M64 [RIVA TNT2 Model 64/Model 64 Pro].  My only options in Screen Resolution Preferences are 640x480, 800x600, and 1024x768.  I changed it to 1024x768 for now, and had to switch from Wide Mode to standard 4:3 on my Samsung DLP, just to hardly stand it.  This is my biggest concern at this point, and I'd like to get this figured out first before anything else, if at all possible.

As for my other problems, they seem to be smaller and much less significant.  And I'm sure I haven't ran into everything I'll need help with yet.  If I can just find a solution to the above, things will be much better...I hope.

Thanks in advance,
~ Brandin

---

### Post by Kateikyoushi on 2007-03-13
Then try to reconfigure your X settings, copy this to the terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by BHTX84 on 2007-03-13
> **Kateikyoushi said:**
> Then try to reconfigure your X settings, copy this to the terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

:confused: Hrmmm...

---

### Post by Kateikyoushi on 2007-03-13
The terminal can be opened from Applications > System tools > terminal.

You have to copy the previous command there and set it up, have to give some details about your hardware.

---

### Post by BHTX84 on 2007-03-13
Alright...did that.  I even thoroughly researched every parameter I entered before entering it, just to make sure I wouldn't make a mistake.  Unfortunately, it didn't seem to do anything whatsoever.  I'm still stuck at 1024x768, when I want to get to at least 1280x768.  Any ideas? :(

---

### Post by dstew on 2007-03-13
Which linux distribution are you using?

---

### Post by BHTX84 on 2007-03-13
Ubuntu edgy?  Yeah...that's it.

---

### Post by BHTX84 on 2007-03-13
I keep coming across people talking about installing a legacy driver for this old video card (nvidia TNT2).  And it's also obvious that I'm not the only person who's had this problem.  I've attempted to follow along with the steps, but as soon as I type the first step in the terminal, I get the following...

bhtx84@bhtx84:~$ $sudo aptitude install linux-686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

..Of course, I have absolutely no clue whatsoever in regards to the meaning of this.

---

### Post by ljpm on 2007-03-13
Not sure it this is relevant but I found that my monitor was not detected properly, specifically the Hscan and Vscan ranges were not set. When I entered the correct values (when reconfiguring my xserver-xorg) I was able to obtain the desired resolution.

I think the problem has to do with the refresh rate. If the hscan and vscan ranges are not set correctly either Ubuntu or the monitor prevents higher resolutions to protect the monitor.


I don't know how this will relate to your monitor but it might be some place to start looking for a solution.

---

### Post by lamalex on 2007-03-13
what is your hardware? nvidia? ati? have you tried installing the drivers for your card?

---

### Post by compmodder26 on 2007-03-13
> **BHTX84 said:**
> I keep coming across people talking about installing a legacy driver for this old video card (nvidia TNT2).  And it's also obvious that I'm not the only person who's had this problem.  I've attempted to follow along with the steps, but as soon as I type the first step in the terminal, I get the following...

bhtx84@bhtx84:~$ $sudo aptitude install linux-686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

..Of course, I have absolutely no clue whatsoever in regards to the meaning of this.

Remove the "$" in front of sudo

---

### Post by Kateikyoushi on 2007-03-13
> **BHTX84 said:**
> I keep coming across people talking about installing a legacy driver for this old video card (nvidia TNT2).  And it's also obvious that I'm not the only person who's had this problem.  I've attempted to follow along with the steps, but as soon as I type the first step in the terminal, I get the following...

bhtx84@bhtx84:~$ $sudo aptitude install linux-686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

..Of course, I have absolutely no clue whatsoever in regards to the meaning of this.

Do you have synaptic open ?

---

### Post by sammao on 2007-04-29
Download this and Install.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Nvidia drivers works fine. 

You might whant automatix2 to get you started with codecs etc..

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Why not install fiesty, ubuntu 7.04 first..

---

