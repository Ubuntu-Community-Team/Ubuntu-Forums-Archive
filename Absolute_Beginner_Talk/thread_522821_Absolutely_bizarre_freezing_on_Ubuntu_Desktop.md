---
title: "Absolutely bizarre freezing on Ubuntu Desktop"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-11
This might be long and possibly confusing because I'm not much of a writer, so bear with me.  You might want to take a look at the questions I ask to prepare yourself for what you might be answering :), but you'll probably have to read the backstory to make any sense out of them.  

I decided today to switch completely from Windows to Ubuntu. I downloaded the appropriate ISO, Ubuntu Desktop, and burned it to a CD.  I booted the CD, checked it for errors with the built-in utility, and it came up error-free.  I booted the CD into the live OS, just like with the older computer, and it froze dead at the "loading Nautilus screen" right before the desktop.  I thought it was a fluke, turned the PC off and then on again manually and let it boot into the live OS again.  It made it to the desktop, loaded whatever had to load, and then I decided to open Firefox to make sure I had a net connection; I didn't want to install the OS if I couldn't get a a net connection.  I made it to the front page of this website and BAM, it froze just like before.  Nothing worked, not even the mouse.  I was hoping it was a live CD problem and I manually rebooted like before.  I get to the desktop again and it freezes, yet again.  I manually reboot and pray it makes it to the desktop, and somehow, it does.  

I double-click the install icon and it begins the process.  I answer the questions, it begins to format the drive and does that successfully.  It begins copying and configuring files and I watch a little TV while it does that.  I look over a little bit later and it is at a login screen with a countdown.  It says its going to boot the user Ubuntu.  I assume this is a part of the installation so I let it.  It boots to the desktop, but it is frozen.  The mouse doesn't move and no keyboard shortcuts do anything.  I let it set for a few minutes hoping it is installing, but eventually I decide that it just froze like always and hoped it had loaded the OS.  I power down and power back on, let it boot from the HDD and I get an "OS loading error."  I manually reboot yet again, get to the desktop, and begin the install sequence again.  I let it format the drive again, it starts installing and configuring stuff, and this time I watch the progress to see what may happens.  This time, it gets to 100% and tells me to reboot the system.  I tell it to restart, it tells me to take out the CD, and then it powers off and back on.  I boot the system and it loads the OS from the HDD and it freezes before it gets to the desktop!

Now I think I have a problem.  I try a couple of more times and it freezes within 3 or 4 minutes each and every time.  Dead freezing, no mouse, no keyboard, NOTHING.  It always freezes and I don't have any way to get support because my Dad's PC is in their bedroom and the only other PC I have is running Ubuntu Server and has no GUI or way of accessing a support forum or IRC chat.  And that gives me an idea.

I get out my Ubuntu Server CD, boot it up, format the drive and let it install.  I'm at the bash shell and I execute the command sudo apt-get install ubuntu-desktop.  I'd seen that earlier tonight actually somewhere on this forum, and I was hoping it would do what I want it to.  Luckily, it did.  It installed all of the applications and system tools that come with Ubuntu and thats how I'm on the forum now.  Everything looks exactly like the desktop version I had installed on my older PC, and everything is working.  Finally, that leads to my questions.

1.  Any idea why Ubuntu Desktop would crash like that?  This PC has had XP installed on it for 3 years and worked up until I formatted, so I know it wasn't a hardware problem.  The fact that the sort of hacked solution I came up with is stable also indicates that.  I was thinking maybe it was the media I used, but the Ubuntu Server CD is on the same media, and in addition to that the CD check utility verified that the CD was good.

2.  Are there any differences between the Desktop and Server kernal?  Are there going to be any conflicts on the system because of the manner in which I have the core components installed?  Will the Synaptic Package Manager 'see' whatever packages were installed with the Server edition, since it came with the ubuntu-desktop package I installed?

3.  When I do system -> preferences -> screen resolution, the highest available is 11xx by 7xx.  Sometime in the installation progress after I executed sudo apt-get install ubuntu-desktop, it asked me to select resolutions that I might want to use for x windows (or maybe it said x.org, I can't remember).  I tried to select 12xx by 10xx but I hit the wrong button and it went on with the configuration.  How can I add that resolution to the list?  The resolution it is stuck at now is blurry on my 19 inch lcd :).

If anyone can answer my questions or give any useful comments, I'd be much obliged.  I'd rather not run a machine running Ubuntu Server with the Desktop package inside; I'd rather just have the same ol' Ubuntu everyone else has until I get more familiar with the OS.

Also, here is some pertinent information.

All mentioned versions of Ubuntu are 7.04 downloaded from [http://www.ubuntu.com/](http://www.ubuntu.com/) and installed with default configurations.

My PC specs are as follows:

Athlon XP 2800+
1 gig DDR ram
Radeon 9500 Pro
40 gig IDE HDD

If there is anything I left out, let me know. 

Thanks.

---

### Post by forestpixie on 2007-08-11
1 - bit odd - but I'd say that it was probably a dodgy cd - I get 2 or 3 in a batch

2  - I don't know the differences, but I think Synaptic will see everything, I believe that installing the desktop will only install the missing bits. 

3 - you probably need to reconfigure the x server - 

```
sudo dpkg-reconfigure xserver-xorg
```
 Hope that's of some help

---

### Post by sad_iq on 2007-08-11
Sounds like a bad media...have you done an md5 check on the iso before burning? Have you burned it a the lowest speed?? Also try the memcheck when you boot the live cd, maybe it's a faulty memory!!!
 I also have installed ubuntu the same way as you have and i have no problems, the kernel is the same!!!
 About the resolution you probably have to install the video driver for your card before using 1280x1024 (could be wrong thou)

---

