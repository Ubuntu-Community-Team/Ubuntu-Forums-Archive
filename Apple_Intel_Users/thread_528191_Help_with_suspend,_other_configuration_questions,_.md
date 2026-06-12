---
title: "Help with suspend, other configuration questions, on laptop install"
date: 2007-08-17
forum: Apple Intel Users
---

### Post by E Gardner on 2007-08-17
Hello-

I have just finished installing Ubuntu Studio on my first-generation Macbook Pro with the help of Rapido's install scripts (thanks!). I got it working in a dual-boot arrangement with rEFIt/bootcamp software where it coexists with an OS X partition on my laptop's hard-drive. Aside from a few experimental test runs (first in VMWare fusion, then via boot camp), this is my first time ever installing/using a linux system. These forums have been very useful throughout the process, and I have referenced them constantly without posting anything.

I am pretty pleased with the results so far - x works after installing the ATI support, wireless works, the brightness controls on the keyboard work, sound works, isight works (though I am trying to find a program that uses it), and the trackpad works fairly well after some tinkering with the xorg config file. Xgl and compiz work as well, and are pretty impressive.

A few things still do not work as well as I'd like them to, and I was hoping that people here might have suggestions.

One problem has to do with suspend. On a previous install of the standard Ubuntu 7.04 (via Boot Camp Assistant, without any scripts or other helper applications), suspend worked like a charm. When the lid was closed the light on the front would pulse just like it did in OS X, and when the lid opened I was asked for a password to unlock the screen.

Now the situation is a little different. Without XGL/Compiz running, suspend mostly works (though the window which asks for my password does not work properly - all that is visible is the mouse cursor and the field to enter text - some of the buttons appear if the mouse moves over them; this doesn't get in the way of any actual functionality, though it is a little wierd). With XGL/Compiz, I can enter suspend but cannot leave it - I only get a black screen, no response to anything short of holding down the power key long enough to restart the system.

Power management is another issue - under Ubuntu the system consumes power more rapidly, and  also seems to get hotter than when running under OS X.

Are either of these problems things which can be fixed by adjusting some configuration settings?

---

### Post by benanzo on 2007-08-17
I do not own the MacBook Pro, only the MacBook, but my first thought about your suspend issues was that it probably has to do with ATI's **fglrx** graphics module not resuming properly (given the video issues.)  But then I had a look at the mactel-linux.org MacBook Pro wiki and they claim that suspend *should* work even with the binary module.  Here's a quote from their [MacBook Pro status page]("http://www.mactel-linux.org/wiki/Status#Status_on_Macbook_Pro"):
> 
#  Suspend to RAM and Suspend to Disk using suspend2 2.2.5. You have to unload the sky2 module (ethernet) before suspending. Then it even works with the fglrx driver and 3d hardware acceleration.
# Suspend to RAM seems to work using s2ram with linux-2.6.17's new suspend framework [1] but has problems with Fn keys and/or touchpad after resume. Nevertheless it works really fast (5 seconds for suspend and 5 for resume) and reliable (I write this after three suspend/resume cycles). 


This information is a little old (around the time of Edgy,) but might still be applicable.  I'm sure there are others here who can provide more specific information.

Good Luck!

---

### Post by Gen2ly on 2007-08-17
I've found it useful to use the fusion-icon.  I assume obviously that you have compiz-fusion installed.  I need to stop compiz before reboot, shutdown, ctrl-alt-del... or risk that compiz will freeze it.

What you'll learn in LInux is that power management is still developing.  Since Linux was originally developed for servers, and to some degree is still largely focused on that, that configuring power saving is possible but large up to you.  You'll learn there are a few apps out there that can help.  Ones called powersave (it's used in conjuction with cpufrequtils), and another, I believe it developed by Intel, does a good job with discovering where your power consumption is largely being used, I'm forgetting the name of it at the moment ... ooop powertop.  There's also laptop-mode-tools, which I think helps spin down the hard drive ( a large consumer of power ).

---

### Post by cyberdork33 on 2007-08-17
fglrx used to cause issues, but I think they worked those bugs out finally.

The sky2 driver in the kernel is still experimental (even the latest kernels), so you can't be too suprised if it causes issues.

---

### Post by ivesjd on 2007-08-17
I believe that Dirk was talking about powertop, although that is for advanced users. For the iSight there is a program called [[COLOR="Red"]_***cheese***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=486722") Still early in devlopment but it works.

---

### Post by ElTimo on 2007-08-20
I have the same problem and i have an nvidia card (a quadro 110m specifically). I have tried installing uswsusp, but to no avail. my system consists of a c2d 2.0 GHz 2.0 GB ram mobile workstation btw.

---

### Post by E Gardner on 2007-08-20
Thanks for all the responses so far - I got the compiz icon working (which is useful) as well as Cheese. As far as powertop, I found the site for it but was unable to get it installed - synaptic couldn't find it, and the tar package I downloaded did not work (encountered some kind of error when I tried to install it from command line).

The suspend issue is still a problem. Could the culprit be the XGL session? When not running in XGL suspend seems to work (though it is a bit wonky) - but I've never gotten the machine to wake up when in XGL mode. Prior to installing Ubuntu using the install scripts posted on Rapido's thread I had a vanilla version of 7.04 running, and suspend worked fine. There was no XGL or desktop-effects installed/inabled, but I had installed the fglrx drivers (that seems to be the only way to make ubuntu work in graphical mode with the X1600 video card).

If XGL is the problem, any ideas on how it could be fixed? Should I look into recompiling the kernel with the mactel patches? I understand that many of them are already included in the 7.04 installation, yes? What if anything remains to be incorporated?

Thanks again for the help - without these forums as a resource I don't think I would have gotten anywhere.

---

