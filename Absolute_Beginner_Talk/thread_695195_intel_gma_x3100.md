---
title: "intel gma x3100"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-12
A friend is letting me play with his laptop.  I am in the process of trying to decide between ati x1300 and the intel gma 3100 video card.  See other post.  

The question is I just installed ubuntu on the gma x3100 intel system and it appears to have no 3d acceleration.  Compiz will not enable

How, do I enable 3d on the intel gma x3100 and how do I test it? What is a decent score for this card?

How do you get Compiz to work?

It is integrated into his laptop.

thanks

---

### Post by TechDragon on 2008-02-13
anyone

---

### Post by Golem XIV on 2008-02-13
The Intel chipsets are blacklisted in Compiz because they don't play nice.  

To enable Compiz effects, you can edit the file /etc/xdg/compiz/compiz-manager and add the line:

```
SKIP_CHECKS="yes"
```

This will allow you to enable the desktop effects.  However, there is a cost: it will break video playback.

the video problem can also be worked around, though.  Run the Multimedia System Selector that is on the System -> Preferences menu (but it is hidden by default, run the menu editor first to show it) or through the terminal 
```
gstreamer-properties
```

Make a note of the configuration so you can reset it back in case something gets screwed up.  Now go to the Video tab and under Default Output change the Plugin to "X Window System (No Xv)".
This will give you back video playback by using a slower and more resource-intensive renderer (but at lkeast it'll work).  Use the Test button to make sure it works.

The downside is that some apps will not like this new renderer and will not work with it (Skype 2.0 beta will not show you video, for example).

---

### Post by raskolikov on 2008-02-24
I can't add the line
SKIP_CHECKS="yes".
the answer is:
alberto@alberto-laptop:~$ /etc/xdg/compiz/compiz-manager
bash: /etc/xdg/compiz/compiz-manager: Permesso negato (permissionnied)
also if i'm root the permission is denied.
Someone know's why?

---

### Post by ronmarley1 on 2008-02-24
> **raskolikov said:**
> I can't add the line
SKIP_CHECKS="yes".
the answer is:
alberto@alberto-laptop:~$ /etc/xdg/compiz/compiz-manager
bash: /etc/xdg/compiz/compiz-manager: Permesso negato (permissionnied)
also if i'm root the permission is denied.
Someone know's why?

You need to open the file in a text editor.  One option is gedit.  The code is ```
gksudo gedit /etc/xdg/compiz/compiz-manager
```
Add the line above and save the file.  Then try and start compiz-fusion again.  
As the abov poster mentioned, your card is blacklisted due to video playback issues when using compiz-fusion.

Here's a Sticky Thread that discusses this issue: [http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

---

### Post by oasisman on 2008-02-24
> # Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
COMPIZ_NAME="compiz.real"
SKIP_CHECKS="yes"

freshly installed gutsy with a x3100
i did this, but it still wont allow me to enable 3d.

any suggestions?

btw, this is my first time messing with linux so im a total n00b...

---

### Post by d.i. on 2008-02-29
> **Golem XIV said:**
> The Intel chipsets are blacklisted in Compiz because they don't play nice.  

To enable Compiz effects, you can edit the file /etc/xdg/compiz/compiz-manager and add the line:

```
SKIP_CHECKS="yes"
```

This will allow you to enable the desktop effects.  However, there is a cost: it will break video playback.

the video problem can also be worked around, though.  Run the Multimedia System Selector that is on the System -> Preferences menu (but it is hidden by default, run the menu editor first to show it) or through the terminal 
```
gstreamer-properties
```

Make a note of the configuration so you can reset it back in case something gets screwed up.  Now go to the Video tab and under Default Output change the Plugin to "X Window System (No Xv)".
This will give you back video playback by using a slower and more resource-intensive renderer (but at lkeast it'll work).  Use the Test button to make sure it works.

The downside is that some apps will not like this new renderer and will not work with it (Skype 2.0 beta will not show you video, for example).
...it worked but...the videos are stil not playing :( ....any suggestion??

---

### Post by bigred1 on 2008-02-29
I could not get Compiz to work with GMA 3100, even with SKIP_CHECKS. 

Also, video is grainy to the point where I have to switch to Windows in my dual-boot system.

---

### Post by jebasan on 2008-03-02
> **Golem XIV said:**
> The Intel chipsets are blacklisted in Compiz because they don't play nice.  

To enable Compiz effects, you can edit the file /etc/xdg/compiz/compiz-manager and add the line:

```
SKIP_CHECKS="yes"
```

This will allow you to enable the desktop effects.  However, there is a cost: it will break video playback.

the video problem can also be worked around, though.  Run the Multimedia System Selector that is on the System -> Preferences menu (but it is hidden by default, run the menu editor first to show it) or through the terminal 
```
gstreamer-properties
```

Make a note of the configuration so you can reset it back in case something gets screwed up.  Now go to the Video tab and under Default Output change the Plugin to "X Window System (No Xv)".
This will give you back video playback by using a slower and more resource-intensive renderer (but at lkeast it'll work).  Use the Test button to make sure it works.

The downside is that some apps will not like this new renderer and will not work with it (Skype 2.0 beta will not show you video, for example).

Thanks and sorry it took so long to respond; 
here whats happening: the visual effects are working just fine but still no sound.
CODE
luiz@jebasan666:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
sh: jackd: not found
gstreamer-properties-Message: Error running pipeline 'ESD - Enlightenment Sound Daemon': Could not establish connection to sound server [esdsink.c(263): gst_esdsink_open (): /pipeline2/esdsink2:
can't open connection to esound server]
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

---

### Post by Mr. Zilla on 2008-03-19
Adding 'SKIP_CHECKS="yes"' to /etc/xdg/compiz/compiz-manager worked perfectly for me and I am running on the Intel GMA X3100 chipset as well. And actually, I didn't need to use the workaround for video playback. I guess machines are becoming more like people everyday. Can be built nearly the same, but each one is unique.

---

### Post by Uolirod on 2008-03-22
I've tried adding the skip_checks line and commenting out the x3100 lines in the config file and neither one is giving me any success at enabling compiz. I'm trying this on a Compaq running Mint 4.0. Any more direction would be greatly appreciated.

---

### Post by wozzinator on 2008-03-24
> **TechDragon said:**
> A friend is letting me play with his laptop.  I am in the process of trying to decide between ati x1300 and the intel gma 3100 video card.  See other post.  

The question is I just installed ubuntu on the gma x3100 intel system and it appears to have no 3d acceleration.  Compiz will not enable

How, do I enable 3d on the intel gma x3100 and how do I test it? What is a decent score for this card?

How do you get Compiz to work?

It is integrated into his laptop.

thanks

The X3100 IGP is **blacklisted** in Gutsy, that always ticked me off, but then I upgraded to Hardy and it was no longer on the black list. I can now use all of the Advanced Desktop Appearance Features. So from this experience I'm assuming that any version before Hardy doesn't have support for the X3100 IGP.

---

### Post by bigred1 on 2008-04-29
Yes, upgrading to Heron did the trick for me too.

---

### Post by Uolirod on 2008-04-29
I also upgraded to Hardy a while ago and had the same success. Thanks for the replies.

---

### Post by TechDragon on 2008-04-30
When I upgraded to hardy heron with an intel gma x3100 it showed to use the generic VESA drivers, I was unable to even force heron to accept the intel drivers.  Consequentially I was unable to run in dual monitor mode.  Any attempt to do anything other than what Heron sets up automatically resulted in the bulletproofx configure screen at log on.

---

### Post by Uolirod on 2008-05-01
I had to use the intel experimental modesetting driver but I can't remember right now how I did it. I'm pretty sure I had to edit the xorg.conf file. I had to install it to enable compiz/fusion. I'm not awake yet and I won't be near a computer all day but if you're still interested I'll give more explicit directions when I get home tonight?

---

