---
title: "Desktop Effects - XGL Makes everything slow"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by nutbastard on 2008-01-19
Ok I've been everywhere trying to fix this. Registered just for this one issue.

7.10 Gutsy fresh install with all updates.
Dell Inspiron 8600 w/ nvidia geforce GO5200
Restricted driver enabled
Intel Pentium M 1.5 Ghz

Wifi works, everything works except desktop effects. Selecting one of the options in the Appearance menu results in "Desktop effects could not be enabled" Error message.

Previous instructions indicated that I needed to do:

sudo apt-get install xserver-xgl

However, doing so causes all window drawing to operate very slowly, as well as messing up my keyboard settings (X settings do not match Gnome settings, Keep Gnome or X settings --> I always choose Gnome)

When I say slowly, I mean, When a new window pops up it first draws the upper right half then the lower left half, 2 right triangles of rendering, one after the other.

So I've done a fresh install and omitted xserver-xgl.

Then:

output of $compiz:

nutbastard@nutbastard:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 11
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
NVIDIA: Direct rendering failed; attempting indirect rendering.
Comparing resolution (1920x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

The nvidia 5200 has 64 MB of memory - which is 65536kb. I don't get it. Why this error? The memory exists, what's the big deal?

I've had limited success with installing xserver-xgl in previous gutsy installs on the same computer, where I could get one of the Desktop Effects settings to not give me a "Desktop effects could not be enabled" error, but the effects fail to manifest themselves when I do control-alt-right after enabling the cube etc.... in short, why does gutsy come with non-working compiz, and is it even going to be worth trying to fix, and if it is worth trying to fix, where do I go from here?

Again, xserver-xgl makes everything so slow as to be unbearable.

---

### Post by spiderbatdad on 2008-01-19
possibly try one of the drivers in synaptic "nvidia-glx-new" then reboot and select custom under visual effects.

---

### Post by carlinuxlearner on 2008-01-19
Try installing "Envy" heres some instructions:

1.
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

2.
Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu6_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

3.
Double click on the file you just downloaded and tell it to install

4.
If all those steps went well then Envy should be installed and you should be able to find it on your "Applications" menu under "System tools", just run it and you should be able to install your driver all by your self very easily.

C@RL

---

### Post by nutbastard on 2008-01-20
Ok i'll try envy, but nvidia-glx-new is what I already have going on by default. Installing xserver-xgl enables the use of desktop effects, or rather, enables the other radio buttons to be activated, but desktop effects fail to manifest themselves, and verything is slow slow slow. Im thinking of forgoing the whole thing and downgrading to 6.06, as it seems doing a manual compiz install to 6.06 on the hardware i'm running worked for many people and that 7.10 introduced some sort of bug. I don't see anything in the document that explains the difference between 6.04 and 7.10 to contain anything worth drooling over (well, besides compiz)

I'll let you know if envy does the trick. Thanks!

---

### Post by nutbastard on 2008-01-22
Ok everyone i've talked to has told me that Envy is absolutely useless in Gutsy.

I've given up on compiz - It would have been cool, but i've broken my system 4 times messing with ****. Im not qualified to take this on at this point, and the battery on my laptop will last longer without the GPU going crazy all day anyways.

Perhaps if it "just works" out of the box next release, but im not fighting this. Got to a place where firefox wouldn't play videos and such, and it's only been through repeat installs and noting my steps that i've been able to get youtube, myspace music, stage6 divx, all the toolbars and WICD and everything, and im not risking breaking it again.

If it's going to be included on the CD and the hardware fits the requirements, it ought to work.

1.5ghz Pentium M
64mb nvidia geforce fx GO5200
Fresh 7.10 install
Driver Enabled via Restricted drivers manager


I've only had to get into the CLI for flash, and that was just pointing the shell to the installer. I love the idea od the command line, ultimate control over everything (or whatever) and i don't fear the damn thing, it's just that when things DO go right in the CLI, everyone wants to ignore the fact that the GUI is broken. I understand that the CLI is like a toolbox in the trunk of a car, and, as the analogy goes, it's great to have and bad to need.

---

### Post by nutbastard on 2008-01-22
you know, i was aware this was a profanity-free board, but when i get going, well, apologies - im not trying to be vulgar. I support clean boards - im just so used to gizmodo and open forums where it doesn't fu- uh, where it doesn't matter : )

---

