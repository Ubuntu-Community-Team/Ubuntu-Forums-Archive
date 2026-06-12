---
title: "Dual Boot Installed: Ubuntu 7.04 Login Leads to Blank Screen"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by wbmercer on 2007-05-23
I am an absolute beginner who tried to set up a dual installation with Ubuntu 7.04 and Windows.  

I think I correctly partitioned the hard drive. I can still boot up in Windows and it shows the C drive where it is, and an empty D drive which is now 90GB instead of the previous 180GB (because I took the default partition suggestion in Linux to take half of the 180GB for Linux. I can boot up in the second and third Linux options. The second one says recovery and runs through a lot of stuff, says OK about all of them, and leaves me at a command line. The third one says memtest something. I let it run for 5.5 hours and it just keeps checking stuff and saying it's not finding any errors. I stopped it at 5.5 hours, not knowing whether it just keeps repeating the same steps indefinitely or was still checking more stuff.

The first option, though, to actually boot up in Linux, that should bring me to the GUI I want, doesn't. It starts booting up very slowly, finally asks for my username and password, then stays on a blank tan screen for maybe 15-30 minutes, then pops up a light blue square in the upper left quadrant of the screen with the rest remaining tan colored, and stays that way forever.

I want to fix that without reformatting the whole drive and reinstalling both operating systems.  I installed Linux from this CD earlier with no problem except that I wiped out windows by taking the whole hard drive. When I hit the adapter problem I then re-installed Windows allowing it to have the whole hard drive (divided into C and D). That's where I was until I made this latest attempt at a dual-boot installation.

I'd really love to make this work and feel like I'd gained something from the whole experience, but it's getting discouraging.

Can someone walk  me through, keystroke by keystroke, the commands to diagnose and fix this problem?

Thanks,
Brad

---

### Post by ske1fr on 2007-05-23
> **wbmercer said:**
> 

Can someone walk  me through, keystroke by keystroke, the commands to diagnose and fix this problem?

Thanks,
Brad

Brad, I can't do that keystroke by keystroke walkthrough, but I can tell you what others will want to know.  

What are the details of the hardware you are using, in particular the graphics card or onboard graphics?  The fact that you can get to a command line prompt in failsafe mode is good, but the failure in normal boot suggests a problem with the X server that gets you into a GUI like Gnome or KDE.

State clearly in another post what graphics you've got on this machine, and I'm sure you'll get some help.

---

### Post by siteguru on 2007-05-23
[http://ubuntuforums.org/showthread.php?t=450977](http://ubuntuforums.org/showthread.php?t=450977)

Check that thread.

---

### Post by wbmercer on 2007-05-24
It  looks like it offers two possible solutions, but neither of them give me every detailed step like I need as a total newbie.  I don't know how to do either of the things they suggest without someone walking through it with me.  And I can't tell whether either of them is actually talking about Ubuntu 7.04 Feisty Fawn.

Can someone tell me literally keystroke by keystroke how to do what they're suggesting?

Thanks,
Brad

---

