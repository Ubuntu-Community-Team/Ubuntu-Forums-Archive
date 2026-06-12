---
title: "Need help with widescreen resolution and touchpad"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Wandel on 2006-10-26
Hi, I'm completely new to Linux/Ubuntu, and I've just installed edgy on my laptop(a HP nx6400), and I have some problems I was hoping someone could help me with.

Firstly, the built-in graphics card in my laptop is a Mobile Intel 945GM Express Chipset, and the resolution I want to use is 1280x800. How do I do that? Currently, the only resolution available for me is 1024x768.

Second, I've got a Synaptics Touchpad, and I don't want to be able to click with the mouse by just tapping on the pad, how do I change that?

Third, how to a change the settings for the power button, so that when I press it, instead of shutting down, the computer hibernates?

And lastly, I want eye candy :p  Can someone direct me to a guide to set up XGL/Compiz(or the equivlent for people with Intel graphics cards)?


Thanks in advance :)

---

### Post by lowracer on 2006-11-09
To get the additional screen resolution, try editing your /etc/X11/xorg.conf file.  You'll see the place where resolutions are listed, just key in your desired resolution, save the file, and restart X.  Then you should be able to use it, assuming your screen is capable of displaying it. 

Good luck!

---

### Post by localuser on 2006-11-09
> **Wandel said:**
> I've got a Synaptics Touchpad, and I don't want to be able to click with the mouse by just tapping on the pad, how do I change that?

Install qsynaptics package, then execute from command line
```
$ gksudo qsynaptics
```

You can execute automatically at start-up by adding an entry to System | Preferences | Sessions | Startup Programs tab
```
qsynaptics -r
```

> **Wandel said:**
> How to a change the settings for the power button, so that when I press it, instead of shutting down, the computer hibernates?

System | Preferences | Power Management | General Tab

---

### Post by Directrix1 on 2006-11-12
Yeah, I have the same laptop resolution problem on my widescreen Dell.  There is a testing driver for Intel's new 8xx/9xx graphics chipsets that correctly supports these newer resolutions, but it doesn't work on my laptop at the moment.  But what will work is:

```
sudo apt-get install read-edid
sudo bash
get-edid | parse-edid >> /etc/X11/xorg.conf
```

That will add a new "Monitor" section to the bottom of your xorg.conf file with all the correct settings read directly from your monitor.  You then need to go into your xorg.conf scroll to the end and copy all of the contents inside of the new "Monitor" section starting after the Identifier line, and paste it up inside the previous "Monitor" section.  I kept the DPMS option and the existing Identifier line so I wouldn't have to edit more than I had too.  Then remove your new Monitor section from the bottom as it is redundant.  Then find 'Section "Screen"' and add your new mode to all the "Modes" lines.  Make sure it is in quotes exactly like the other ones and seperated by spaces.  Then save and quit your editor, and run:

```
sudo apt-get install 915resolution
```

This will install the 915resolution hack which works around the temporarily broken Intel drivers.  Restart your computer and it should be working.  This will most likely not be necessary with the next version of the Intel drivers as they already have an almost working driver in testing.  Enjoy. :-D

EDIT: And for the eyecandy search the forums for Beryl ([www.beryl-project.org)](www.beryl-project.org)), there are several walk-throughs on getting that going.  Just so you know, with the Intel card if you are using Ubuntu 6.10 Edgy or beyond then you don't need XGL to get Beryl running, because it works through the built in AIGLX.

---

