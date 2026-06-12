---
title: "Can't get Xorg to work on Arch"
date: 2009-02-09
forum: Arch and derivatives
---

### Post by Dani Filth on 2009-02-09
Hello folks,

I just installed Arch on my old laptop (Fujitsu S2020 Lifebook) which is about 4 years old. The core was installed ok, but I can't seem to get X/Xorg to work.

I wanna try LXDE on Arch, so I followed the instruction on their wiki and installed it with

> pacman -Sy lxde xorg xorg-video-drivers xorg-input-drivers hal gamin

Then as I recall reading somewhere, it says that if you're not sure with setting up Xorg, you can just install another distro and copy the xorg.conf from that distro to put on your Arch system and it *should* works.

Please see the attachment for my xorg.conf (which is copied from Slackware 12.2 that I installed on my laptop as well - the hardware is exactly the same)

However, after all these, I can only get X/Xorg display on the screen with 3 windows (xterm and 2 others I can't remember the names :P ) but the mouse and keyboard totally don't work (neither do Ctrl+Alt+Backspace/Ctrl+Alt+F1). I can only press the Power button to switch off the computer manually.

I also tried startx/xinit/startlxde but none of them work.

(I'm writing this on another computer, so if you want the /var/log/Xorg.0whatever-the-name-is file I can upload it later too)

Please advise, thank you :popcorn:

---

### Post by smartboyathome on 2009-02-09
Read up [here]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging"). You are probably having problems with hotplugging.

---

### Post by Dani Filth on 2009-02-09
Thanks smartboyathome, I will give it a try :D

Just another attachment, this is the Xorg.0.log from /var/log

---

### Post by Dani Filth on 2009-02-09
I followed the instruction on that site, and it says that HAL must be run before anything related to Xorg starts. But I'm unable to get HAL start :confused:

Whether
I have already added "hal" to DAEMONS in /etc/rc.conf
I even tried "/etc/rc.d/hal start" to manually start HAL but it still doesn't work.

And I notice when the computer boots, there are some messages say
> FATAL: Module ath_hal not found
FATAL: Module ath_pci not found
FATAL: Module wlan not found

I've never seen this before, as I did try to install Arch once before, and didn't even see these kind of messages.

Please advise me what to do, thank you

EDIT:
I also tried the "I don't want this crap" part to disable hotplugging, still no luck :(

---

### Post by ubersolid on 2009-02-09
> **Dani Filth said:**
> I followed the instruction on that site, and it says that HAL must be run before anything related to Xorg starts. But I'm unable to get HAL start :confused:

Whether
I have already added "hal" to DAEMONS in /etc/rc.conf
I even tried "/etc/rc.d/hal start" to manually start HAL but it still doesn't work.

And I notice when the computer boots, there are some messages say


I've never seen this before, as I did try to install Arch once before, and didn't even see these kind of messages.

Please advise me what to do, thank you

You seem to need madwifi, drivers for the wireless card.
```
 pacman -Sy madwifi
```

And try this too:
```
pacman -Sy xorg hwd
```
```
hwd -u
```
```
hwd -xa
``` this generates and xorg.conf using vesa for you.

---

### Post by handy on 2009-02-10
Yes I use the hwd method to get X installed also.

Dani Filth, you have been following the Beginners Guide?

---

### Post by cb951303 on 2009-02-10
add this to your xorg.conf and you're good to go. As its already said the problem is hotpluggin. This piece of configuration disables hotplugging and falls back to the good old input system

```

   Section "ServerFlags"
     Option "AutoAddDevices" "False"
   EndSection

```

---

### Post by K.Mandla on 2009-02-10
Personally, I prefer the old-fashioned way, without HAL, etc.

[http://kmandla.wordpress.com/2008/11/30/hal-xserver-153-and-allowemptyinput/](http://kmandla.wordpress.com/2008/11/30/hal-xserver-153-and-allowemptyinput/)

I might be in a minority though. :)

---

### Post by kerry_s on 2009-02-10
> **K.Mandla said:**
> Personally, I prefer the old-fashioned way, without HAL, etc.

[http://kmandla.wordpress.com/2008/11/30/hal-xserver-153-and-allowemptyinput/](http://kmandla.wordpress.com/2008/11/30/hal-xserver-153-and-allowemptyinput/)

I might be in a minority though. :)

i'm going to try that. :)

quick question, do i still need "Option "AutoAddDevices" "False" " in my xorg.conf? **never mind, it's not needed.**


hey it works. what other tricks you hiding? :lolflag:

---

### Post by handy on 2009-02-10
I don't use HAL either.

---

### Post by .Maleficus. on 2009-02-10
If you don't need to use Hal, I'd suggest you don't.  Hal 5.11-7 and PolicyKit 0.9-7 are having some pretty strange issues with automounting devices and generally don't work very well.  I've found a sudo-fix for the problem (before I can use my external drive as a normal user I need to open it as root) but it's still kind of annoying.

---

### Post by handy on 2009-02-10
I use the directory utilility Worker, where I mount & umount whatever, using 2 buttons dedicated to their respective purposes.

---

### Post by K.Mandla on 2009-02-10
I do something similar with emelfm2, which allows you to right-click on a folder and mount it to a location determined in your /etc/fstab file. 

Really, I've got nothing against HAL & company, I just don't find it necessary, so I don't use it. :roll:

---

### Post by K.Mandla on 2009-02-10
> **kerry_s said:**
> hey it works. what other tricks you hiding? :lolflag:
No, no tricks over here. I'm just another newb. :D

Nice screenshot, by the way. I don't usually like black as a theme, but that's very clean. And JWM rocks, etc. ;)

---

### Post by kerry_s on 2009-02-10
> **K.Mandla said:**
> No, no tricks over here. I'm just another newb. :D

Nice screenshot, by the way. I don't usually like black as a theme, but that's very clean. And JWM rocks, etc. ;)

:lolflag: thanks, i was bored, i had the stock theme like forever, i also wanted to get rid of the gradients, make things a single color. it's not actually black, i'm using gray20 and gray30, i don't use a wallpaper, just a waste of resources to me.

i don't use external drives very often, maybe once a month to backup some settings. in debian i would just pmount /dev/sda1 them, so i'll do the same in arch, but haven't tried yet.

---

### Post by Dani Filth on 2009-02-10
Wow, thank you all for your replies :D

@ubersolid : I tried hwd too, it didn't work.

@handy : Yes, I followed Arch's Beginner's Guide. Is there something wrong with their guide? :confused:

@cb951303 : Did that after reading the "I don't want this crap" part, it still didn't work.

@K.Mandla, kerry_s, handy, .Maleficus. : It's not that I find HAL is a must, it's just what I followed the Arch's Guide, thus it instructed me to install & use HAL. In fact, I'll use whatever method to get the X work.

I will try out K.Mandla's suggestion later :popcorn:

Again, thank you all :)

---

### Post by handy on 2009-02-10
The Beginners Guide is problem free as far as I'm concerned.

---

### Post by Dani Filth on 2009-02-10
K.Mandla's tips to add
> "ServerLayout"
Option "AllowEmptyInput" "False"

didn't work on my computer :confused: . But this is after I remove "hal" from rc.conf's DAEMONS, do I need to have hal running together? From what I've read, you don't use HAL and you don't find it necessary as well.

@All:
I usually get this kind of error when I "startx", sometimes after I edit some part of xorg.conf it may be a bit different, but I usually see this error 
> Fatal server error:
no screen found

giving up
xinit : No such file or dir (errno 2) : unable to connect to Xserver
xinit : No such process (errno 3) : Server error

As I recall, there are something else about the system can't find the directory for /mouse and /type1.

---

### Post by K.Mandla on 2009-02-11
No, you should be able to start X without HAL running, and still get mouse and keyboard input.

I don't know how well it will work, but this is what I usually do.
[LIST=1]
[*]Install xorg group and leave out the crud that I don't need (like twm or whatever).
[*]Install the video driver for the card.
[*]Run X -configure
[*]Edit /root/xorg.conf.new for the card I'm using, adding the AllowEmptyInput line.
[*]Move /root/xorg.conf.new to /etc/X11/xorg.conf.
[*]Add the user, the window manager, login and startx.
[/LIST]
It might be that those don't quite apply for your system though. I fall into habits at times, and forget there are computers that were made after 2001. :roll:

---

### Post by Dani Filth on 2009-02-11
Cheers K.Mandla

I followed exactly the steps from your last post. Now I'm able to "startx" as well as "exec startlxde", except that I have to do that as root, normal user still can't "startx"

Does anyone have any advice?
Thanks :D

---

### Post by kerry_s on 2009-02-11
> **Dani Filth said:**
> Cheers K.Mandla

I followed exactly the steps from your last post. Now I'm able to "startx" as well as "exec startlxde", except that I have to do that as root, normal user still can't "startx"

Does anyone have any advice?
Thanks :D

did you put yourself in the video group so you can use X ?

---

### Post by Dani Filth on 2009-02-11
As far as I recall, I did follow the Beginners Guide and add my user with "useradd -m -G users,audio,...video username", how do I see what an user can do, then? :P

---

### Post by kerry_s on 2009-02-11
i just do mine manually with the text editor.
in terminal:

**cat /etc/group | grep you**

replace "you" with your user name.

---

### Post by Dani Filth on 2009-02-11
I get
> video:X:91:username
So I suppose my username is already in the video group?

Still, normal user can't "startx", I notice there are some error messages like :

> Could not init font path element /usr/share/fonts/Type1, removing from list!

and

error setting MTRR (base = 0xe4000000, size = 0x01000000, type = 1) Invalid argument (22)

---

### Post by kerry_s on 2009-02-11
those are common errors, shouldn't effect X.

---

### Post by Dani Filth on 2009-02-11
But I still cannot "startx" as normal user. Any suggestion?

---

### Post by kerry_s on 2009-02-11
> **Dani Filth said:**
> But I still cannot "startx" as normal user. Any suggestion?

try going over all the steps again, if X works in root, there must be something you missed.

---

### Post by smartboyathome on 2009-02-11
edit: oops

---

### Post by Dani Filth on 2009-02-11
The Arch forum has a similar thread aboutt his [http://bbs.archlinux.org/viewtopic.php?id=65065](http://bbs.archlinux.org/viewtopic.php?id=65065)

So I guess there's something wrong with the fresh install from CD and it's needed to re-install or do a ftp install instead :confused:

I'll mark this thread as [SOLVED] soon if nobody has a solution for this, thank you all for your time & patience. :popcorn:

---

### Post by kerry_s on 2009-02-11
> **Dani Filth said:**
> The Arch forum has a similar thread aboutt his [http://bbs.archlinux.org/viewtopic.php?id=65065](http://bbs.archlinux.org/viewtopic.php?id=65065)

So I guess there's something wrong with the fresh install from CD and it's needed to re-install or do a ftp install instead :confused:

I'll mark this thread as [SOLVED] soon if nobody has a solution for this, thank you all for your time & patience. :popcorn:

agreed, you should try a fresh net install.

---

### Post by wolfvorkian1 on 2009-02-12
> **Dani Filth said:**
> The Arch forum has a similar thread aboutt his [http://bbs.archlinux.org/viewtopic.php?id=65065](http://bbs.archlinux.org/viewtopic.php?id=65065)

So I guess there's something wrong with the fresh install from CD and it's needed to re-install or do a ftp install instead :confused:

I'll mark this thread as [SOLVED] soon if nobody has a solution for this, thank you all for your time & patience. :popcorn:
Have you tried running without an xorg.conf file? I don't have one. After the big update a few weeks ago that hosed many if not most .... I renamed the xorg.conf file to something besides what it should be and did a startx. Worked like a champ. X came back and I don't have a xorg.conf file anymore or if I do, 'locate' can't find it.

---

### Post by Dani Filth on 2009-02-12
wolfvorkian1,
I just tried that and it still didn't work. The screen blinked/flashed for a second then reverted back to text mode.

If there's no xorg.conf, root can't go in X mode either. I have to rename xorg.conf.root back to its old name in order to get X works.

By the way, where's the "Mark thread as SOLVED" option in "Thread Tools", I haven't used that for some times and now I can't find it :D

---

### Post by wolfvorkian1 on 2009-02-12
> **Dani Filth said:**
> wolfvorkian1,
I just tried that and it still didn't work. The screen blinked/flashed for a second then reverted back to text mode.

If there's no xorg.conf, root can't go in X mode either. I have to rename xorg.conf.root back to its old name in order to get X works.

By the way, where's the "Mark thread as SOLVED" option in "Thread Tools", I haven't used that for some times and now I can't find it :D

FWIW, I just checked the laptop I recently installed Arch on ( 6-7 year old Gateway) and it has no xorg.conf file either. The install disc I used was 2008.06.-2 according to the /var/log/pacman.log file ( I think that is what it means) and I didn't do any configuration for a xorg.conf file on that machine after the experience I had with the desktop xorg update. I just did a startx after what was needed (installed) for an X server after the base install and the new system started and worked flawlessly. 

Sorry it didn't work for you. I had a heck of a time getting xorg to work when I first tried to install Arch. Finally had to change video cards in the old desktop. The on board video card which worked fine with any debian type distribution simply didn't hack it with Arch. A couple of times I was able to get a graphical interface going but after loading a half dozen or so programs it would crash horribly and none of the commands in the wiki would bring it back. But after putting an old Nvidia card in, haven't had a problem since.

---

### Post by smartboyathome on 2009-02-12
> **Dani Filth said:**
> By the way, where's the "Mark thread as SOLVED" option in "Thread Tools", I haven't used that for some times and now I can't find it :D

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714) :popcorn:

---

### Post by Dani Filth on 2009-02-12
Hello all,

I've just re-installed a fresh FTP install and things are now going smoothly. Nothing's wrong :guitar:. So I presume there's still something different between a fresh core/CD install and a fresh FTP install :confused:

Thank you all for your time & replies :D

---

### Post by smartboyathome on 2009-02-13
Just to let you guys know, there is a new version of the Arch Linux cd coming out soon (Arch Linux 2009.02).

---

