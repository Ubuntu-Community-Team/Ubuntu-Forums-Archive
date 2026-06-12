---
title: "Time to give up on Xubuntu? (can't wake up) Bug-free alternatives?"
date: 2017-01-20
forum: Apple Hardware Users
---

### Post by joannacw on 2017-01-20
I recently installed 32-bit  Xubuntu Xenial Xerus 16.04.1 LTS from a purchased live dvd on a partition on my [COLOR=#000000]M[/COLOR]*acBook Pro 1,2 with a 2.16 GHz Intel Core Duo processor and 2GB 667 MHz DDR2 SDRAM  *I think this question belongs here, not in the Apple Hardware forum, because, as noted below, I've found many records of people with different hardware types running this distro having this problem.

Everything works fine except for the problem explained in the thread linked below: whenever the computer goes to sleep (whether I shut the lid or not) it 'wakes up' either to a very dim screen which doesn't respond to keyboard brightness controls or to an absolutely black screen, and I have to manually shut it off. This is a large enough problem to render the OS pretty much unusable.:( I've seen online reports of the same problem from Xubuntu users with a variety of Mac and PC laptops; many fixes are given (I've tried the ones I understood how to pull off so far) and some people report solutions, others ongoing problems which eventually led them to switch to another distro.

(Detailed description of the problem, and my attempted fixes, in this thread: [https://ubuntuforums.org/showthread.php?t=2349884&p=13596882#post13596882](https://ubuntuforums.org/showthread.php?t=2349884&p=13596882#post13596882))

3 questions:
 How do you decide whether to keep trying fixes, reinstall what you had before, or try another distro?

If keeping trying seems indicated: Some fixes start with going into 'system settings' and changing settings in a window I've not yet found. I can go into Settings, and thence into Power Manager, but that doesn't offer the exact options shown in the fixes. How should I access system settings, if they're separate from Settings?

If another distro seems indicated, can you recommend any that have ongoing 32-bit support, would run on the older machine I have, and are more bug-free than Xubuntu? Lightweights are fine with me, as I don't need serious graphics capability; the ability to enlarge screen icons would be helpful, as the computer I'm converting to Linux is for my visually impaired mother.

Any advice greatly appreciated. Thanks.

---

### Post by ajgreeny on 2017-01-20
*Thread moved to **Apple Hardware Users**.* which is more appropriate, in spite of your comment, and a better fit.

All questions about Apple hardware should be in that section as there are too many differences from normal to make it easy for anyone other than an Apple knowledgable user to help.

---

### Post by joannacw on 2017-01-20
Ajgreeny, thanks. I'll see that I post here in future.

Anyone: I've been told on another forum that Xubuntu does not officially support Macbook Pros. Are there Linux distros which are better suited to Macbook Pros in partiucular, or 32-bit Apple laptops in general?

---

### Post by g33zr on 2017-01-21
There are several distros you could try. If you don't mind paying a few $$, you can install Elementary OS, which is lightweight and makes installation on a Mac easy. You should also consider other lightweight distros with a LXDE or OpenBox option, such as Zorin, Lubuntu, or BunsenLabs, which originates from CrunchBang (aka #!). Another good lightweight choice is Bodhi.

If you haven't do so already, I recommend wiping OSX from your MacBook and installing just Linux, but make sure you use VirtualBox to test the distros first. When I first ran Linux on my old MacBook, I dual-booted, which, over time seemed to be more of a hindrance than a help. After wiping OSX from the drive, I ran just Linux (Ubuntu, Mint, Debian, CrunchBang, Bodhi, among others) and experienced no serious issues.

---

### Post by joannacw on 2017-01-23
Thank you very much, g33zr. I think I'll be testing some of these, as attempted fixes haven't allowed me to wake the computer back up in Xubuntu.

I see you say you've used an old MacBook. How old is yours? I've Googled around and noticed similar wakeup issues reported for most other distros, and I've seen one article which suggests that some hardware just won't support the Linux suspend and hibernate functions. Any idea about whether my machine is simply too old or whether I am just having a specific distro bug problem?

Thanks again.

---

### Post by g33zr on 2017-01-24
^I've seen various posts about suspend/wake-up issues on various forums, but they're not limited to Macs. Personally, I don't recall having the problem. The only problem I had with my old MacBook, which I bought in 2006, was with iSight, after I wiped OSX and installed just Linux in 2009 (probably #!). The camera no longer worked, but after some research I was able to find a workaround. The MacBook bit the dust in 2013 and I bought a System76 laptop. Even though I wiped OSX from my 2009 iMac, everything works with Ubuntu, including the camera. I use that PC as an "entertainment center" for listening to music, watching streaming feed for news, YouTube, etc. Who needs TV? ;)

---

### Post by schmied on 2017-01-25
Elementary OS is free, no? Last time I checked, it was.

---

### Post by joannacw on 2017-01-27
Good! I'm going to try Elementary OS. It seems to be on a donations-requested system and I'm happy to donate a bit.
One more question which perhaps should be obvious: Do I need to uninstall Xubuntu from the partition before installing Elementary OS, or can I just overwrite from the Elementary OS install DVD?

---

### Post by howefield on 2017-01-27
> **joannacw said:**
> Good! I'm going to try Elementary OS. It seems to be on a donations-requested system and I'm happy to donate a bit.

It is, although you may choose to "donate" a zero amount. 

> One more question which perhaps should be obvious: Do I need to uninstall Xubuntu from the partition before installing Elementary OS, or can I just overwrite from the Elementary OS install DVD?

You can mount the existing Xubuntu partitions and mark for formatting during the partitioning stage of the install process.

---

### Post by joannacw on 2017-01-28
Argh. I read that Elementary OS was no longer developing 32-bit versions, so tried Lubuntu instead--not installing, just trial running from a live CD. I'm having the same problem I had with Xubuntu; the screen is still extremely dark on wakeup. 

Would I be likely to have better success with a non-Ubuntu version of Linux? Is it likely to be a swap space issue? I have 2 GB Linux swap space now. I tried to expand this to 4 in two ways (still running Xubuntu) but failed in both.
[COLOR=#333333]I installed Gparted. I can view my partitions (linux-swap has 1.98 GiB) but seem to have very limited ability to edit: when I select the linux-swap partition the &#8216;Resize/Move&#8217; option in the Partition menu is gray and unusab;e. (Swapoff, Name Partition and Manage Flags are the only options I get there.) [/COLOR]

[COLOR=#333333]When I try the Terminal command line approach to adding swap space, this is what I get:[/COLOR]
[COLOR=#333333]Command: sudo dd if=/dev/zero of=/media/fasthdd/[/COLOR][COLOR=#333333]swapfile.img[/COLOR][COLOR=#333333] bs=1024 count=1M[/COLOR]
[COLOR=#333333]Response: dd: failed to open &#8216;/media/fasthdd/[/COLOR][COLOR=#333333]swapfile.img[/COLOR][COLOR=#333333]&#8217;: No such file or directory exists/[/COLOR]

---

### Post by vasa1 on 2017-01-31
The last two posts in this thread have been moved to their own thread here: [Installing Bodhi Linux on a 32-bit Apple laptop]("https://ubuntuforums.org/showthread.php?t=2351122")

OP, if you wish to have another thread title for the new thread, please use the report button there giving us the title of your choice.

---

### Post by joannacw on 2017-01-31
Thanks. Your current title is excellent. Sorry about that--I am not always sure when to start a new thread.

---

