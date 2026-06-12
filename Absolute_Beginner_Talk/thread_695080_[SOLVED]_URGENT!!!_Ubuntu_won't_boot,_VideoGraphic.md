---
title: "[SOLVED] URGENT!!! Ubuntu won't boot, Video/Graphic Card Driver Problem! Waiting for"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-12
Help!!! I have Intel Graphics Media Accelerator thingy, Intel 915 Video/Graphics card.

By default Ubuntu uses the Experemental drivers etc.. now I changd it to intel 915, because of curiosity at the same time when I am observing my screen saver I see some weird black boxes that flashes I can't describe it but it's something like that.

something like a window wanted to appear even if the screensaver is running.

I only see the following when booting:

[[IMG]http://img257.imageshack.us/img257/7780/p1000673tb9.th.jpg[/IMG]](http://img257.imageshack.us/my.php?image=p1000673tb9.jpg)
**click to enlarge**

Please help me!!!!

I can't believe because of too much freedom this will happen!:lolflag: Thank god I have backup, WinXP, haven't deleted it.

IF only Ubuntu has something like XP, when a wrong driver is installed, you can still boot, only, it uses GENERIC DRIVERS.

And please make the error messages friendly, so that a newbie can understand it.

It would also be a good thing if Ubuntu has a GUI Recovery mode, like safe mode.

Oh yeah, I have soo... many sticky notes regarding my criticism to Ubuntu and regarding some questions like the overheating of laptop etc... I am going to compile your answers into one website which is only for newbie or n00bs as in beginners, those who have no idea with linux.

[http://kinux.uni.cc](http://kinux.uni.cc) <-- if you wanted to help out that would be great.

Anyway my power in case you wanted to know it, userspace, limit, minimum 600Mhz maximum 1.40GHz out of 1.70GHz, performance_ac is by default 85, I set it to 95 ... and what is consider_nice ?

before replying, to my above questions, please prioritize how can I boot to ubuntu!!!! Please!!!!

>>> curious again... how can I have ubuntu i686?:lolflag:

HELP!!!:(:(:(:lolflag:

**TIP to Newbies**: Always have backup like XP ... if only XP was only a live CD which can also let you access the internet ... another one, always make your Digital Camera, with you... you'll never know how to report errors! :lolflag:

---

### Post by smartboyathome on 2008-02-12
Run sudo dpkg-reconfigure xserver-xorg after you log in with your username and password, reconfigure your graphics, and then restart your computer with the command sudo reboot.

---

### Post by karlo on 2008-02-12
> **smartboyathome said:**
> Run sudo dpkg-reconfigure xserver-xorg after you log in with your username and password, reconfigure your graphics, and then restart your computer with the command sudo reboot.

QUESTION, it's very confusing.. can I use the LIVE CD, then run the command there? Why use the LIVE CD, so that I can access this thread from there... via WiFi ... good idea?:confused:

---

### Post by jpittack on 2008-02-12
Recovery mode is the same as safe mode.  Should be in grub unless you have it set up to skip that.

---

### Post by smartboyathome on 2008-02-12
> **karlo said:**
> QUESTION, it's very confusing.. can I use the LIVE CD, then run the command there? Why use the LIVE CD, so that I can access this thread from there... via WiFi ... good idea?:confused:

unfortunately, you can't :( You have to run it from within the black text place.

---

### Post by jordanmthomas on 2008-02-12
OK, I'll try to take this part by part.
1.  Your screensaver issue:
    This only happens if compiz is enabled.  OpenGL stuff doesn't get redirected properly with compiz (try dragging around the screensaver preview and you can see what I mean.  The video just stays in place until the movement is done)  Any time a window behind an openGL window updates itself, the openGL will flicker.  The only way I know of to fix this is to either disable compiz or to use XGL, which is a little bit slower on an i915

2.  To fix your driver issue:
First login at that terminal you get there.  Then, install **either** the intel (experimental) driver or the old i810 (stable) driver:
```
sudo apt-get install xserver-xorg-video-intel
```
```
sudo apt-get install xserver-xorg-video-i810
```
Remember which you installed.
Now, you have a couple of choices here:
Choice 1 is to let X reconfigure itself:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
You should be able to accept the defaults as you go through.
Choice 2 is to manually fix your configuration file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup #make a backup
sudo nano /etc/X11/xorg.conf
```

Then, find the section of the file that looks something like this:
```
Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection
```
And change the line that says 
```
Driver "[COLOR="Red"]intel[/COLOR]"
```
to either say intel or i810, depending on the driver you installed earlier
Hit ctrl - O, enter, ctrl - x to save and exit

Now, you should be ready to start X back up and go about your business:
```
sudo /etc/init.d/gdm restart
```



> It would also be a good thing if Ubuntu has a GUI Recovery mode, like safe mode.
I believe that is scheduled for the next release.  :)

---

### Post by jordanmthomas on 2008-02-12
> **smartboyathome said:**
> unfortunately, you can't :( You have to run it from within the black text place.

It's possible to do if he uses chroot, but that might be harder than just logging into a perfectly booted system with no GUI.

---

### Post by karlo on 2008-02-12
Before, my default driver was the **experimental one** that Right now as of **Today** I selected the **i810** drivers! And ... then **this issue** ... is there still any tweaks for **Compiz?** because I would like my laptop to look more presentable.

How many memory does **compiz** consumes?

Weird, one time I disabled compiz, then all of the screensavers in 3d runs jerky...

---

### Post by jordanmthomas on 2008-02-12
compiz isn't too bad on your memory really. 
Like I said, the only way to stop the flickering is to switch to xgl (which does tend to use a lot of memory).

And yes, there's TONS of ways to customize compiz.  Try installing emerald and compizconfig-settings-manager to get all the options and have another option for your window borders.

Have you tried the suggestions in this thread (and did they work?), or are you waiting for more suggestions?

---

### Post by karlo on 2008-02-12
> **jordanmthomas said:**
> compiz isn't too bad on your memory really. 
Like I said, the only way to stop the flickering is to switch to xgl (which does tend to use a lot of memory).

And yes, there's TONS of ways to customize compiz.  Try installing emerald and compizconfig-settings-manager to get all the options and have another option for your window borders.

Have you tried the suggestions in this thread (and did they work?), or are you waiting for more suggestions?

WOW, you are **GOOD!**, Anyway I can't believe someone can reply to my ridiculously described message..

Anyway, if you are in my case, would you go for XGL?

Installed emerald, made me confused, I thought compiz and emerald made some kind of conflicts, and it's not friendly, must compile etc..

actually I was pissed off by visiting **GNOME Look** because, they don't provide instructions to new users or newbies, on how to install their themes. Although, I have installed a new login graphic, but still, I have to explore...

most of the linux sites specially those who offer softwares are not friendly and requires compilation or requires to compile it, and I think it consumes alot of disk space!:confused::mad:

---

### Post by nikoPSK on 2008-02-12
just on smart boys post, it's better to do this:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by karlo on 2008-02-12
> **jordanmthomas said:**
> compiz isn't too bad on your memory really. 
Like I said, the only way to stop the flickering is to switch to xgl (which does tend to use a lot of memory).

And yes, there's TONS of ways to customize compiz.  Try installing emerald and compizconfig-settings-manager to get all the options and have another option for your window borders.

Have you tried the suggestions in this thread (and did they work?), or are you waiting for more suggestions?

**WAITING** for more suggestions. Easier and friendlier one, of course, with explaination so that I will learn from. I think i'm still a newbie, but I'm used to **sudo** now!:lolflag:

---

### Post by karlo on 2008-02-12
> **nikoPSK said:**
> just on smart boys post, it's better to do this:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Is it as same as the code recommended to me? And pelase explain?:(

---

### Post by karlo on 2008-02-12
> **nikoPSK said:**
> just on smart boys post, it's better to do this:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

I saw on your profile that you use the latest version of **Ubuntu**... well how was it?:)

---

### Post by nikoPSK on 2008-02-12
> **karlo said:**
> Is it as same as the code recommended to me? And pelase explain?:(phigh auto sets things to optimum

> **karlo said:**
> I saw on your profile that you use the latest version of **Ubuntu**... well how was it?:)

good, please read:
[http://nikopsk.wordpress.com/2008/02/02/hardy-alpha-4-adds-new-software/](http://nikopsk.wordpress.com/2008/02/02/hardy-alpha-4-adds-new-software/)

---

### Post by nikoPSK on 2008-02-12
> **karlo said:**
> <snip>
and ```
-plow
``` sets to minimal.

---

### Post by karlo on 2008-02-12
> **nikoPSK said:**
> phigh auto sets things to optimum



good, please read:
[http://nikopsk.wordpress.com/2008/02/02/hardy-alpha-4-adds-new-software/](http://nikopsk.wordpress.com/2008/02/02/hardy-alpha-4-adds-new-software/)

well, where to download the applications that is included in hardy?

also, for example on april hardy is released, can I use install it over my current ubuntu? what about disk space? i mean does it do something like windows xp, backups old files and keeps it?

---

### Post by nikoPSK on 2008-02-12
> **karlo said:**
> well, where to download the applications that is included in hardy?

also, for example on april hardy is released, can I use install it over my current ubuntu? what about disk space? i mean does it do something like windows xp, backups old files and keeps it?

yes, just a simple dist upgrade, read more here:
[http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)

Just look at the other ones like brassero. :)

---

### Post by karlo on 2008-02-12
> **nikoPSK said:**
> and ```
-plow
``` sets to minimal.

I see.. regarding the update thing. did you noticed there's a new update for the linux kernel lately?

---

### Post by nikoPSK on 2008-02-12
> **karlo said:**
> I see.. regarding the update thing. did you noticed there's a new update for the linux kernel lately? maybe? I don't know... I think so.

---

### Post by karlo on 2008-02-13
> **nikoPSK said:**
> maybe? I don't know... I think so.

[http://ubuntuforums.org/showpost.php?p=4318985&postcount=1](http://ubuntuforums.org/showpost.php?p=4318985&postcount=1)

this person above, installed the new kernel, something happened.
but according to another member here, the new kernel is on kernel.org instead of the ubuntu update.

---

### Post by karlo on 2008-02-13
**[SIZE="7"][SOLVED][/SIZE]**

[SIZE="4"]Thanked[/SIZE] **nikoPSK [COLOR="Red"]1+[/COLOR]**

---

### Post by nikoPSK on 2008-02-13
> **karlo said:**
> **[SIZE=7][SOLVED][/SIZE]**

[SIZE=4]Thanked[/SIZE] **nikoPSK [COLOR=Red]1+[/COLOR]**

No problem! :D Glad I could help you. Please mark this thread as [solved] by going to the top of the page then thread tools. :)

---

