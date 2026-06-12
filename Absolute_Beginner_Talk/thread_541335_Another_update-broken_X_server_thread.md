---
title: "Another update-broken X server thread"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-09-02
I've looked at all the other threads, and jumped into one, but probably should have made my own.  None of them have quite had the same issues.  This happened a couple of days ago with the kernel update, but I haven't had the time or patience to devote to it just yet.  However, I don't think I can tolerate using XP much longer. 

Here are  the errors I've gotten:
> 
The X server is now disabled.  Restart GDM when it is configured correctly.

Failed to load module "wfb" (module does not exist, 0)

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9746.  Please make sure that the kernel module and all NVIDIA driver components have the same version. 

(EE) NVIDIA (0): Filed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.  Please consult the NVIDIA README for details. 
**aborting**

(EE) Screen(s) found, but none have a usable configuration. 

Fatal server error: 
no screens found

XIO:fatal IO error 104 (connection reset by peer) on X server":0.0" after 0 requests  (0 known processed) with 0 events remaining. 


Running dpkg-reconfigure -phigh xserver-xorg is of no use.  I bring it up, and then as I pick NVIDIA on the first screen, it kicks me out to a warning about possibly over writing a customized setting and tells me where it's made a back up, and then I'm presented with a command line under the blue box.

Sooooo...um.  What now? :confused:

Am I looking at reinstalling the NVIDIA driver, do I need to find an updated one?  Why is dpkg-reconfigure -phigh xserver-xorg acting the way it does?

---

### Post by steveneddy on 2007-09-02
The correct command is

```

sudo dpkg-reconfigure xserver-xorg

```

Write this down somewhere. Something tells me that you will need it in the future.

If you are using nvidia drivers that aren't in the repos then get used to doing this when there is a kernel update.

9755 works great for me.

---

### Post by Wartooth on 2007-09-02
Thanks for your reply.

Apparently the Rx med I'm taking for some stupid allergic reaction (stupid mango!) I had this week is making me extra stupid at the moment.  I've no idea why I shoved phigh in there.  Thank you for pointing that out to me. 

I had a notebook full of notes on what I did to install my NVIDIA driver and get everything working, but I've managed to lose it and am desperately trying to find it.  

I attempted to stumble thorugh the configuration, and got kicked back to a command line when I got to the screen about picking _bit color.  Again, it gave me a notice of where to find the backup, left me at a command line hanging.  

I have found some rather cryptic notes of mine in another notebook, and I can't tell if it's related to what I need to be doing or not.  It seems like it might be...

I've things like this scribbled down:

> 
sudo apt-get install nvidia-glx
sudo nvidio-glx-config enable
sudo nano /etc/X11/xorg.conf
replace "nv" w/ "nvidia"

(sudo dpkg-reconfigure xserver-xorg)
(ctrl-alt-bkspc resets X)

sudo apt-get install nvidia-glx
sudo nvidia-xconfig
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

change driver from "nv" to "vesa" 

sudo /etc/init.d/gdm restart
sudo /etc/init.d



I'm now starting a permanent notebook of notes that will reside in my new and handy filing cabinet from now on, I promise :D  I wish I didn't feel so light-headed and sluggish, I'm sure I'd be better at this.  Well, maybe.  

There's another page with other stuff regarding 915 resolution and such.  I had fought with a second computer many months ago, trying to install Ubuntu, but it had faulty hardware, and I'm not sure if this is from that attempt, or from my trying to get the machine I'm on now to work.  I believe the other machine was Intel, though, with some on-board video...

---

### Post by Wartooth on 2007-09-02
Well, I've tried stumbling through lots of various commands, including the ones above, at one point, I got the GUI at something like 640x480 and then another time at a larger resolution, but managed to somehow break things all over again to the point where I can't get anything working right.  

So much for experimenting, eh?

---

### Post by Wartooth on 2007-09-03
Well, by going through dpkg-reconfigure xserver-xorg a thousand times and playing with variables, I've gotten back on by choosing vesa and going through all the prompts, STILL getting kicked to a command line when choosing 24 bit color, but then entering startx at that command line.  

**HOWEVER:  I am stuck with 1280x1024 when I should be at 1920x1200.  **

So, perhaps this is progress, but I'm not yet back to where I was.  How do I get there?

---

### Post by Wartooth on 2007-09-04
Well, yesterday I tried making things better, and have made them worse... X is broken, and I've given up.  I obviously have no idea what I'm doing, and am very frustrated.  I also don't know how much longer I can tolerate using this buggy XP box of mine. :/

---

### Post by afonic on 2007-09-04
How have you installed the nvidia driver? (through apt or from nVidia site?)

Edit /etc/X11/xorg.conf and change "nvidia" in the Driver section to "nv" or "vesa" to get back into X and fix stuff.

---

### Post by FuturePilot on 2007-09-04
> **steveneddy said:**
> The correct command is

```

sudo dpkg-reconfigure xserver-xorg

```

Write this down somewhere. Something tells me that you will need it in the future.

If you are using nvidia drivers that aren't in the repos then get used to doing this when there is a kernel update.

9755 works great for me.

Actually both commands are correct. But. ```
sudo dpkg-reconfigure xserver-xorg
``` is the harder way to do it.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Basically autodetects everything and only asks you 2 questions (what driver you want and what resolution you want, done) vs. about 20 rather confusing questions with the other way. Your xorg.conf actually recommends using the -phigh option.

How did you install the driver? Did you use the repos or did you download it from Nvidia's website?

---

### Post by pizzutz on 2007-09-04
I am dealing with the same issue, and haven't had time to fix it yet.  When you boot up your computer, select the old 2.6.20-15 kernel, and you will start fine.  I know it's a problem with the nvidia drivers, because switching my driver nv will work with the new kernel.  I will post a permanent fix as soon as a track it down.

---

### Post by steveneddy on 2007-09-04
> **Wartooth said:**
> 
I had a notebook full of notes on what I did to install my NVIDIA driver and get everything working, but I've managed to lose it and am desperately trying to find it.  


I've things like this scribbled down:



I'm now starting a permanent notebook of notes that will reside in my new and handy filing cabinet from now on, I promise :D  

LOL - me too - we just moved and my "special" notebook is nowhere to be found.

I always had good luck by reconfigure the xserver, choose vesa and a safe display resolution. Then I go in and make sure that I have the nvidia driver, then change the driver in xorg.conf to nv to start out.

I will Ctrl+Alt+Backspace to restart the xserver, one step at a time, until I finally get the xserver to run properly. 

Good luck.

I recommend the nvidia driver from the repos.

nvidia-glx-new, I think.

---

### Post by hanzomon4 on 2007-09-05
I have the nvidia driver from the repos but after the latest update only one kernel works...

---

### Post by afonic on 2007-09-05
> **hanzomon4 said:**
> I have the nvidia driver from the repos but after the latest update only one kernel works...

What version of Ubuntu? Which nVidia card?

---

### Post by Hobo Joe on 2007-09-05
In my experience, drivers break after a kernel update.

Use Envy to reinstall them, I have a link in my sig.

---

### Post by afonic on 2007-09-05
> **Hobo Joe said:**
> In my experience, drivers break after a kernel update.

Use Envy to reinstall them, I have a link in my sig.

It shouldn't happen if they are installed from the Ubuntu repos.

Envy is a pain as when you do a kernel upgrade X fails and you need to run it again by logging in at vesa mode. Installing the drivers from the repositories is the way to go, unless you need something that is not available.

---

### Post by Nythain on 2007-09-05
drivers only brake after a kernel upgrade if you used the drivers from nvidia's site installed teh way they say too... (and the way automatix and envy installs them, though envy might now use the correct method through the repos, im not sure because i dont use envy).

if you install the package from the repos (nvidia-glx, nvidia-glx-new, nvidia-glx-legacy) it will get updated with each kernel upgrade... no breakage.

if you're broke, you are either going to have to A. log in with the most current kernel and re-install the drivers via the method from nvidia's site... B. remove teh previously installed drivers and install the correct package from teh repo's or C. well, those are about your only two options... i guess you could go the envy route, but i dont know why when its so easy to just type sudo apt-get install nvidia-glx-new

---

### Post by hanzomon4 on 2007-09-05
I'm running feisty and have the glx-new nvidia drivers, it worked for all of my kernels before the update from *15 to *16. Now X only works with one kernel *gasp. I know how to install the drivers from nvidia but I don't want to deal with reinstalling the drivers every kernel update, argh!! *frustrated*

---

### Post by hanzomon4 on 2007-09-06
Ha, fixed it by reinstalling all of the restricted-modules packages

---

### Post by soma4me on 2007-09-06
hanzomon4,

I'm having the similar issue with my nvidia driver, the new kernel (20-16) says "Failed to load the NVIDIA kernel module!".       I do have nvidia-glx-new installed and it's working fine for kernel 20-15.

Would you mind be a bit more specific?  What retricted-modules packages did you install? Did you use command line or Synaptic?

In Synaptic, I see "linux-restricted-modules-generic" already marked installed, I also see both "linux-restricted-modules-2.6.20-15-generic" and "linux-restricted-modules-2.6.20-16-generic" marked installed.

Thanks a bunch for your help!!

---

### Post by hanzomon4 on 2007-09-06
This is what you do, "apt-get install --reinstall"  the specific restricted-modules kernel packages that are not working. In synaptic you would mark the package for reinstall. 

This is the command I ran```
sudo apt-get install --reinstall linux-restricted-modules-2.6.20-15-generic linux-restricted-modules-2.6.20-15-lowlatency linux-restricted-modules-2.6.20-16-generic linux-restricted-modules-2.6.20-16-lowlatency linux-restricted-modules-2.6.20-16-realtime
```

I hope it helps

---

### Post by soma4me on 2007-09-07
hanzomon4,

AWESOME!!  THANK YOU!   This fixed my problem!   I executed the following command in kernel 2.6.20.16 recovery mode:

```
apt-get install --reinstall linux-restricted-modules-2.6.20-16-generic
```

And it worked like a charm!!   I've been looking around, thinking I might not have any choice but to install the nVidia native driver....Anyway, thank you so much!!

:D

---

### Post by Wartooth on 2007-09-08
I'm sorry I've been away from this thread, the XP machine of mine has gone completely haywire recently, so I've had limited time online.  If this thing lets go, I'll be relying on my Nokia 770.  

This is the first time I have had anything break from a kernel update.  I suppose I was just lucky?  

I have a lot of questions after reading these replies, but as for the question about how I installed the driver...I'm not sure.  That would be in the notes.   I DO seem to remember getting something from nVidia, but I also found an [ old thread of mine](http://ubuntuforums.org/showthread.php?t=363033) where I 
did something else entirely?  However, trying to duplicate the steps from the links in that thread just made everything worse.  SO, no go there. 

As to using -phigh or not, running -phigh gets me the configuration box that appears cut off at the top, and kicks me out of it and into a command line as soon as I choose 'ok' regardless of what driver I choose.  It also lets me know the location of the backup file it makes.  

However, I picked vesa this last time, got lucky, and have my lower resolution GUI again...so...more from THAT machine, KVM willing...

---

### Post by Wartooth on 2007-09-08
Better than nothing, but, a long way to go.  

Questions:

How does one select a previous kernel when booting?   Even if that is not what I need to do now, it sounds like it might be a good thing to know. 

If the nvidia-glx-new will work for me, what do I need to know to install this properly?  I've gotten >  sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nvidia-glx-new



I marked things for reinstall under Synaptic and am going to restart X

Still 1280x1024.  Not so great on a 24" monitor :/ 

I am in need of some idiot-proof instructions as wild stabs in the dark aren't panning out.

---

### Post by soma4me on 2007-09-08
Wartooth,

You don't see GRUB menu when you boot up? Have you try hitting escape key after the BIOS message?   Sounds like you're dual-booting, you should see the GRUB menu....If you do see GRUB menu, how many kernel versions are listed?

If you do see the command line, can you try running

```
sudo apt-get update
sudo apt-get install --reinstall nvidia-glx-new
```

and see if you get a different results....

---

### Post by Wartooth on 2007-09-08
Nope, not dual booting.  I go back and forth between my two machines using a KVM.

Just opened terminal and used the commands you listed, still can't find nvidia-glx-new. :/

I'll reboot the machine and see what I see.

---

### Post by Wartooth on 2007-09-08
I had to edit menu.lst to see  GRUB menu, never had seen that before.  However, it flashed on the screen for only a moment and continued on.  My KVM is so slow that, during a reboot, the keyboard is not yet functional when GRUB pops up.  

So, I'm going to try to find another keyboard to plug-in directly.  Which option should I choose when I see GRUB?  I saw quite a few, Since I haven't had my first cup of coffee yet, I don't remember what all the options were.

---

### Post by soma4me on 2007-09-09
Wartooth,

Sorry it did not work for you.    Never use KVM, so can't say anything about it.

You can check out /boot/grub/menu.lst file, find the timeout value, I think the default is 10 seconds, you can extend it if you'd like.

In the grub menu, you should see kernel name with something like [Recovery] mode, if you select it, you'll end up in the root command line.

You can also try re-installing the retricted modules -- that's what fixed my problem:

[http://ubuntuforums.org/showthread.php?t=542977&page=2](http://ubuntuforums.org/showthread.php?t=542977&page=2)

Hope this help.

---

### Post by Wartooth on 2007-09-09
Reinstallation of things doesn't seem to change anything. :(  And, even after having 

I need to know how I can get out of 1280x1024 and get back into 1920x1200. 

I also need to know why, when trying to reconfigure xserver-xorg, it kicks me out immediately after choosing 24 bit color.  I just tried it again, and I'm quite sure that when I restart X, I'll not have a GUI.  

At this point, I'd be willing to just go out and BUY a new video card if it would fix things. 

I'm going to see what happens giving myself 60 seconds with the GRUB menu being available.

---

### Post by Wartooth on 2007-09-09
Found an adapter to get my USB keyboard into the PS2 port on the back.  Selected previous kernel, recovery, and got some error message about Power Manager, decided recovery mode was not what I needed.  Rebooted again, chose previous kernel, non-recovery, and here I am, back with 1920x1200, and not even caring to try to get the new kernel/driver thing fixed. I'm not sure I can be convinced that it's possible. Not worth the aggro. 

Thanks for your time, concern and assistance.

---

### Post by Wartooth on 2007-09-09
Ha, now I have no sound :(

---

### Post by soma4me on 2007-09-10
Wartooth,

Glad to hear you're back in GUI.   Yeah, previous kernel never gave me any trouble, even when was getting nVidia driver error, I was able to get into kernel 2.6.20-15 without any issues.   And I can certainly understand you want to just stick with the prior kernel -- I had the same exact thought.

No sound? In the old kernel? That's wierd.   I do see some other posts regarding sound problems after the update, you may want to search a little....

---

