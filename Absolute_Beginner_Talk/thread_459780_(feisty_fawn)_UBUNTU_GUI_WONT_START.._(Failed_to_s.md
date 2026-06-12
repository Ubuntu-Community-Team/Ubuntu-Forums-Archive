---
title: "(feisty fawn) UBUNTU GUI WONT START.. (Failed to start Xserver)"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Zegga on 2007-05-31
Hey everyone im extremely new to Ubuntu.. I only just installed Ubuntu for the first time yesterday so naturally i went to figure out how to install my nvidia drivers so i found and followed this tutorial [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html) following method 1. After i completed it i got a message saying i was using restricted drivers and desktop effects would not work. So i decided to restart the computer again which is when ubuntu decided not to start up and showed me an error message saying - Failed to start Xserver... Restart CDM when configured properly.     Any ideas on what to do now? 

Thankyou for your time

I have a Intel Core2Duo 6300 with an Intel 965gf mobo.
1gig kingston DDR2 ram, 260gig WD/Seagate sata 2 HDD
Nvidia 7600GT - Palit
Feisty Fawn 7.04

---

### Post by mkoehler on 2007-05-31
Hey,

      You've probably messed around with the xorg.conf file, and made incompatible modifications.  Therefore, use the following command ```
cp /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
``` After this, you should try restarting GDM or KDM, whichever you are using.  You can either press CTRL + ALT + F7 or: ```
For KDM: /etc/init.d/kdm restart
For GDM: /etc/init.d/gdm restart
```
Hope this solves your problems.

---

### Post by pissedoffdude on 2007-05-31
try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by davidingram on 2007-12-29
Hi

I was having the same problem, so i tried this code as suggested:

sudo dpkg-reconfigure xserver-xorg

I got a whole bunch of screens that required me to set about 20 different values, i was totally lost so i went with the auto-detect option and the default suggested values, now my machine is worse than ever.

When i do manage to get a GUI started it is completel;y different to my previous desktop and all my folders and files are GONE.  On my start button (which takes about a minute to do anything) I dont even have a shutdown option so i have to press and hold the power button. 

I fear my computer is totalled, is there any way back from this?
I've lost all my work and i have an inoperable computer.

Can anyone help me?

---

### Post by Amazona aestiva on 2007-12-29
Someday I had the same problem. These  helped me.

Try:
```
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure xserver-xorg
```

In "sudo dpkg-reconfigure xserver-xorg" you have to find the "right" way, and don't worry about what you doing because it can't be worse.

---

### Post by davidingram on 2007-12-30
Hi, I think I am in a real problem, i tried to startup today and just got a black screen.  No way to even type in those commands.  There does seem to be some sort of recover boot option if i hit escape during boot, but there are five options of different modes.  I have NO idea which one to try.  If you have the patience, cuold you please take me through this one step at a time?

Thanks
D

---

### Post by Mazza558 on 2007-12-30
> **davidingram said:**
> Hi, I think I am in a real problem, i tried to startup today and just got a black screen.  No way to even type in those commands.  There does seem to be some sort of recover boot option if i hit escape during boot, but there are five options of different modes.  I have NO idea which one to try.  If you have the patience, cuold you please take me through this one step at a time?

Thanks
D

There should be a few options when you press "esc" during boot up, things like this:

Ubuntu <version number> 2.2.16 
Ubuntu <version number> 2.2.16 (recovery mode)
Ubuntu <version number> 2.2.14 
Ubuntu <version number> 2.2.14 (recovery mode)

etc. Choose the second one down here, which will get you to a command line. Then you can try the commands suggested in this thread. For example, using 

> sudo dpkg-reconfigure xserver-xorg

Follow the steps, following the suggestions (if you're not sure, choose "yes/OK"). When you get to the choice of graphics driver, there'll be a load of them, like "ati", "nvidia" fglrx" etc. Regardless of your graphics card, go down the list and find "vesa". When the wizard is complete. Type:

> sudo reboot

This'll fix it for now, and hopefully get you back to your desktop. From there, we can try and see what went wrong.

---

### Post by popman on 2007-12-30
hello? i need some help

---

### Post by davidingram on 2007-12-30
Here's what happenned.  I tried booting into one of the recovery options so i at least had some sort of 

prompt.  The one i picked was this:
"Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)"

I typed the first command you suggested and nothing happened.

SO, I am trying again, here are the five options I have when I hit esc during boot:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
Ubuntu 1.10, memtest86+

This time I tried the first option (Ubuntu 7.10, kernel 2.6.22-14-generic).
I end up with a screen of vertical blue, green, black, purple and pink stripes, nothing else.
Only way out of this was to hold down the power off button, then i tried again.

This time i chose the second option
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
I get a scrolling screen of text which looks like lots of system stuff loading (i guess)...
When that stops the last thing it says is:

root@david-home:~#


I try the first command you suggest (sudo dpkg-reconfigure gdm) and i get

sudo: dpk-reconfigure: command not found
root@david-home:~#


so it looks like that did nothing.  SO, i try your second command:

sudo dpkg-reconfigure xserver-xorg

And this time I get something, a blue window called "package configuration".

From here I have NO IDEA what I should be doing, it looks like it is expecting me to configure video drivers, but where do i start.  I tried just going with all the defaults, then i get back to some sort of command prompt, but what now.  What do i do next? DId I do the right stuff? I have no idea?

Can anyone be more specific in what i must do?
(I am using a Sony Vaio VGN-T150).


D

---

### Post by popman on 2007-12-30
i need some help with tribes the game

---

### Post by popman on 2007-12-30
i cant find any servers in multiplayer
tribes 1.11

---

### Post by davidingram on 2007-12-30
Hi Mazza558
Looks like i was writing while you were writing.
I am just trying what you suggested right now.
(thanks)
D

---

### Post by davidingram on 2007-12-30
Hi Mazza

Nope, no joy, i chose the second boot option as you suggested, then tried:

sudo dpkg-reconfigure xserver-xorg

all i get is

sudo: dpk-reconfigure: command not found
root@david-home:~#

---

### Post by davidingram on 2007-12-30
sorry, i missed a character, trying it now 
(total noob!)

---

### Post by popman on 2007-12-30
I Have The Old Version Of Tribes,and I Was Playing It With Servers And All,
But I Delete The Game By Accident And  Download It Again From My Disk
Butt This Time I Refresh The Server List And No Servers Found Massage
Shows Up  ,,,some Help Please I Like The Game,,,,,,,,,

---

### Post by davidingram on 2007-12-30
Hey Popman, you are in the wrong forum/thread.  This is NOTHING do do with you game.  Please can you find the appropriate place for your request.

---

### Post by davidingram on 2007-12-30
Hi Mazza
Ok, i have something that looks like my desktop back :))
What do i do now, do i need to make any further changes, or work out what actually went wrong?

You have been SO helpful, thank you.

D

---

### Post by Mazza558 on 2007-12-30
> **davidingram said:**
> Hi Mazza
Ok, i have something that looks like my desktop back :))
What do i do now, do i need to make any further changes, or work out what actually went wrong?

You have been SO helpful, thank you.

D

No problem, glad to have helped. Sorry for the late reply.

Right, I think I'm right in saying you tried the latest drivers using "Envy", like the original poster? This broke my Xserver ages ago too. It's a good script, but doesn't always work for everyone. You presumably have these new drivers installed, which don't seem to want to work for you. That's okay. What you just did (using my instructions) is tell Ubuntu to use the failsafe graphics driver, which works fine for most people, but is pretty sluggish, especially in 3D and if watching videos. What you presumably want is the proper Nvidia drivers. 

The first thing you need to do is get rid of the drivers you installed with Envy. Go to the Synaptic Package Manager (System > Preferences) and do a search for "nvidia". With any luck, you should find the drivers you installed. Can you tell me what the name of the drivers are? They might be similar to "nvidia-drivers-new".

---

### Post by jlh on 2007-12-31
I may have to do the xserver reconfiguration described in this post.  If I wanted to select the correct driver, not the vesa failsafe version, how would I go about identifying that driver?

---

### Post by Mazza558 on 2007-12-31
> **jlh said:**
> I may have to do the xserver reconfiguration described in this post.  If I wanted to select the correct driver, not the vesa failsafe version, how would I go about identifying that driver?

If you install the proper drivers, they should automatically be set on gutsy.

---

### Post by jlh on 2007-12-31
Sorry.  I'm not geeky.

How do I know what the proper drivers are?

Thanks.

---

### Post by davidingram on 2008-01-04
Hi Mazza, I am just trying to follow your helpful instructions for locating the nvidia drivers.  I have done the search in the package manager but come up with nothing.  Not sure what route to take next?  If you are happy to advise that'd be very helpful, thanks.
D

---

### Post by davidingram on 2008-01-04
Mazza, i found those nvidia drivers in package manager (i was wrong, they ARE there).  But there are a  lot that have names 'like' you mentioned, though none exactly the same:
nvidia-glx
nvidia-glx-dev
nvidia-glx-legacy
nvidia-glx-legacy-dev
nvidia-glx-new
nvidia-glx-new-dev
nvidia-kernel-common
nvidia-kernel-source
nvidia-legacy-kernel-source
nvidia-new-kernel-source
nvidia-settings
nvidia-xconfig

Does this mean anything to you?

---

### Post by meindian523 on 2008-01-04
> 

sudo: dpk-reconfigure: command not found
root@david-home:~#


You made a typo,not dpk-reconfigure,dpk**g**-reconfigure

and instead of ```
dpkg-reconfigure xserver-xorg
```

use 

```
dpkg-reconfigure -phigh xserver-xorg
```

edit: oops,I only saw the 1st page before posting.Please ignore this post.

---

### Post by meindian523 on 2008-01-04
Use the [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") script for your drivers.

---

