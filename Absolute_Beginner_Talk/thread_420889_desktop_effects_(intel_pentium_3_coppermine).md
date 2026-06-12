---
title: "desktop effects (intel pentium 3 coppermine)"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by dynoweb on 2007-04-24
I am running ubuntu 7.04 feisty and I am having trouble getting any of it to work if there is anyone out there that would know how please respond.

ask any questions please.....

---

### Post by hardyn on 2007-04-24
processor has very little to do with effects, what video card do you have?

have you tried searching to see if this has been asked before?

---

### Post by dynoweb on 2007-04-24
> **hardyn said:**
> processor has very little to do with effects, what video card do you have?

have you tried searching to see if this has been asked before?

How do I find out said information? if you want you can instant message me I am on all of my messengers .... this process might take a little quicker that way.

---

### Post by kfehr911 on 2007-04-24
If you want direction give people a place to start!  What problems are you having?  Do you hace ANY linux/ubuntu experience?  I know that at the moment I cannot use the desk top effects because when I try I'm given a error message of "The Composite extension is not available" . I'm not sure what that means...  I search a bit then post my problem if I find nothing.  Start with a brief description of what is "wrong" and people will be more willing to help.

---

### Post by dynoweb on 2007-04-24
> **kfehr911 said:**
> If you want direction give people a place to start!  What problems are you having?  Do you hace ANY linux/ubuntu experience?  I know that at the moment I cannot use the desk top effects because when I try I'm given a error message of "The Composite extension is not available" . I'm not sure what that means...  I search a bit then post my problem if I find nothing.  Start with a brief description of what is "wrong" and people will be more willing to help.

when i try to enable the desktop effects it says that i cannot enabled
I dont know where to go from here... I am new to ubuntu and linux so I need to know how tosearch for the problem.

the route i took was:
System > Preferences > Desktop Effects

screenshot enclosed

---

### Post by dynoweb on 2007-04-24
> **dynoweb said:**
> when i try to enable the desktop effects it says that i cannot enabled
I dont know where to go from here... I am new to ubuntu and linux so I need to know how tosearch for the problem.

the route i took was:
System > Preferences > Desktop Effects

screenshot enclosed

I still need help if there is anyone that can help me please respond to this on here or message me on any of my messengers.

Thank You

---

### Post by george29 on 2007-04-24
You need to tell us what graphics card your computer has - also check that you have installed the correct drivers for your card. ie the Nvidia driver or ATi driver depending on your card.

check out this link - lots of very useful info.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by dynoweb on 2007-04-24
> **george29 said:**
> You need to tell us what graphics card your computer has - also check that you have installed the correct drivers for your card. ie the Nvidia driver or ATi driver depending on your card.

check out this link - lots of very useful info.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

how do I find out what graphics card I have?
that way I can install the right drivers and I am going to need help doing that too.

---

### Post by george29 on 2007-04-24
There are two commands that can be used: lspci and glxinfo. The lspci command can be used to identify the card even when no graphics drivers are installed, but it may not report the exact model of the card correctly.

The glxinfo command will report the exact model of the card installed, but it will only work if the graphics drivers are properly installed and Xwindows is up and running. The glxinfo command must be run from an xterm that is being displayed on the machine's local monitor (it cannot be run from a remote ssh login or from a text-only console).

Here is a sample run of lspci and glxinfo:
```

$ /sbin/lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV35GL [GeForce FX 5900]  
$
$ cat /var/log/XFree86.0.log |grep -i GPU
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(--) Chipset NVIDIA GPU found
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5900 Ultra
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
$
$ glxinfo |grep renderer
OpenGL renderer string: GeForce FX 5900 Ultra/AGP/SSE
```
	  

If your card was detected when linux was loaded on the machine, then a section in /etc/X11/XFree86Config, similar to the following, will be found:

Section "Device"
     Identifier  "Videocard0"
     Driver      "nvidia"
     VendorName  "Videocard vendor"
     BoardName   "NVIDIA GeForce 4 (generic)"
EndSection

If there are multiple "Device" sections, look towards the end of the file for a section named "Screen" to determine which "Device" is currently being used.

Please note that there are multiple X11 implementations, and the exact configuration file names, locations and formats may vary slightly depending on your linux distribution. Please see XFree86 and X.org for an up to date description of the configuration files. 

taken from [http://software.sci.utah.edu/doc/User/FAQ/faq.html#card1](http://software.sci.utah.edu/doc/User/FAQ/faq.html#card1)

---

### Post by smartalecks on 2007-04-24
> **dynoweb said:**
> how do I find out what graphics card I have?
that way I can install the right drivers and I am going to need help doing that too.

Umm... if you have a computer that was "already built" and is a brand name (such as Dell) you can probably look up the model online.

Otherwise, you can go System > Preferences > Hardware Information, but you need to have some idea of what you are looking for. Because it is a video card, it should be near wherever it says "AGP" or "PCI" (assuming it isn't an onboard video card). This may not tell you the correct information, however.

---

### Post by dynoweb on 2007-04-24
> **smartalecks said:**
> Umm... if you have a computer that was "already built" and is a brand name (such as Dell) you can probably look up the model online.

Otherwise, you can go System > Preferences > Hardware Information, but you need to have some idea of what you are looking for. Because it is a video card, it should be near wherever it says "AGP" or "PCI" (assuming it isn't an onboard video card). This may not tell you the correct information, however.

Well I found it. the graphics card is:
Rage Mobility M3 AGP 2x

what steps do i take now that i know what the card is?

---

### Post by sailor2001 on 2007-04-24
you might need an accelerater if your card is old.........check in synaptics.......

---

### Post by dynoweb on 2007-04-24
> **sailor2001 said:**
> you might need an accelerater if your card is old.........check in synaptics.......

when anyone gives me instructions to do tell me what it is, what it is for, and why. otherwise what you say is useless .... I am NEW to linux 
I have only had it long enough to only know 7.04 feisty. And obviously i dont know it that well.

---

### Post by Sunflower1970 on 2007-04-24
You may wish to do a  forum search for "Rage Mobility M3." When I did a search for that card here, it looks like some other people have had a similar question/problem as you. :)

ETA this link:

[http://ubuntuforums.org/showthread.php?t=7200&highlight=Rage+Mobility+M3](http://ubuntuforums.org/showthread.php?t=7200&highlight=Rage+Mobility+M3)

---

### Post by compmodder26 on 2007-04-24
> **dynoweb said:**
> when anyone gives me instructions to do tell me what it is, what it is for, and why. otherwise what you say is useless .... I am NEW to linux 
I have only had it long enough to only know 7.04 feisty. And obviously i dont know it that well.

A simple "could you please explain that better" would suffice.  He/she was trying to help you.  No need to bite his/her head off.

---

### Post by dynoweb on 2007-04-24
Topic moved to [http://ubuntuforums.org/showthread.php?p=2526554#post2526554]("http://ubuntuforums.org/showthread.php?p=2526554#post2526554")

---

