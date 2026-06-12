---
title: "Major unknown hardware conflict (looking for generous help)"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by velocitaco on 2007-04-01
**To just read about the problem, scroll down.**
Ok, first of all a little background on me.  I've been using PC's at an upper intermediate level since the Apple II days.  I do computer maintenance and repair for most of my friends.  I have also built every system I've owned for the last 12 years.  I decided to switch to Linux for several reasons.  First, almost all the software I use is open source that's been ported to windows. ex: open office, firefox, and audacity. Second and more importantly, the eventuality of switching to Vista REALLY turns my stomach.  I was reading an OS comparo on PC World online and they used and highly recommended Ubuntu as the Linux representative on the article.  I went over to the Ubuntu site and read up and liked what I saw so I downloaded it.

**The Problem**
First I loaded 6.10 x64 live CD.  It got to the desktop and locked up.  I don't mean BSOD type lock up either.  This is Windows ME type, Bill Gates would be proud, locked up.  Mouse, KB don't respond, Display shows no error messages, animated cursors don't animate, reset button on my box doesn't work.  I have to completely turn off the PC to get out of it.  At this point I rebooted to the Live CD and used the utilities to verify the CD and test my memory. Both passed.
Next, I downloaded the x386 live CD, then the x64 alt install, then the x386 alt install, then the 6.06 x64 alt install and finally the 6.06 x386 install.  The alternate installs actually install completely, but when I go to boot to the OS it locks the same way that the live CD does.
During all this time, I was swapping in & out DIMM's, add-on cards and hard drives to try & eliminate hardware conflicts. (unsuccessfully)
I then tried Fedora. The install went smoothly, but it locks up during boot up.
I have surfed quite a few linux for dummies type forums and websites to find a solution.  I found some useful sites that have great hardware testing programs... FOR LINUX!!! which I obviously can't run:confused: 
I have also talked at length with a buddy of mine who is the head network security admin for the company he works for.  He deals with Windows, Mac, Linux, and UNIX on a daily basis and generally knows his way around a computer.  After telling him about my debacle, he said, "You've got problems!"  Unfortunately he lives 1800 miles away, so house calls are out of the question.
So here I am, in this forum, in Windows, and very grumpy:mad: 

FYI here's my hardware config
AMD Athlon 64 3000+ Socket 754 (retail version)
Chaintech VNF3-250 Mobo
2 sticks of 512MB PC 3200 RAM (tried simultaneously and alternately)
ATI brand 9550 256MB AGP video card
Seagate 120 GB PATA drive for the windows system
IBM 8.5 GB PATA drive for Linux.

- Help me Obi Wan Ken00bie, you're my only hope...

---

### Post by alien21010 on 2007-04-01
So if I'm understanding this correctly, you cannot even boot into the live CD?  Or you can boot into the live Cd and after you install you freeze at the install?  

Where are you freezing during the load of Ubuntu?  Is it when you first start seeing the desktop?  Does it freeze during boot up (like during the splash screen)?

We need more details!

---

### Post by land0 on 2007-04-01
Have you tried swapping out the video card?

---

### Post by velocitaco on 2007-04-01
> **alien21010 said:**
> So if I'm understanding this correctly, you cannot even boot into the live CD?  Or you can boot into the live Cd and after you install you freeze at the install?  

Where are you freezing during the load of Ubuntu?  Is it when you first start seeing the desktop?  Does it freeze during boot up (like during the splash screen)?

We need more details!

Sorry, the live CD boots to the desktop.  Sometimes, it locks up right then, other times, it takes a minute.  I've been able to open firefox once or twice before it locks but it never takes long.  The alt installed versions will do the same thing, the desktop loads and locks up shortly after.  Fedora actually locks during boot up.  I don't have an extra video card right now.

---

### Post by alien21010 on 2007-04-01
When the desktop locks can you press CTRL+ALT+F1 or F2 and drop to a terminal?  Or Ctrl-Alt-Backspace?  Either way should drop you to a terminal.  We need some way to get to a terminal to get access to log files that should be generated during a failure...  If we can't access them, then its going to be virtually impossible to figure out what the problem is.

---

### Post by velocitaco on 2007-04-01
> **alien21010 said:**
> When the desktop locks can you press CTRL+ALT+F1 or F2 and drop to a terminal?  Or Ctrl-Alt-Backspace?  Either way should drop you to a terminal.  We need some way to get to a terminal to get access to log files that should be generated during a failure...  If we can't access them, then its going to be virtually impossible to figure out what the problem is.

That's why this is so frustrating.  The KB and Mouse even lock up.  I'm thinking it's either a Mobo or a memory problem.  The confusing part is that windows has never had a stability issue on this system. I guess Linux is just more picky.:confused:

---

### Post by dstew on 2007-04-01
I couldn't find too much about this motherboard and linux, some people have no problem, but others do. One idea is that a BIOS setting might be making your linux system uncomfortable. It might be the variable clocking setting. Sometimes the interrupt controller can cause problems, and boot options like **noapic nolapic** will help.

---

### Post by chili555 on 2007-04-01
I saw this: [http://www.linuxquestions.org/hcl/showproduct.php?product=2166&cat=39](http://www.linuxquestions.org/hcl/showproduct.php?product=2166&cat=39)

These are comments from a Gentoo user, but all distributions are based on the Linux kernel, so difficulties seem to be common to all. 

It suggests disabling APIC in the BIOS and that one stick of RAM will work, but not two. Another part suggests disabling Cool and Quiet in the BIOS. The nice thing is you can try some or all of these and run the LiveCD. When one works, and works all day, you have a high degree of confidence it will install.

Good luck and post back so other VNF3-250 owners can discover what worked.

---

### Post by velocitaco on 2007-04-02
OK, I disabled APIC and removed my older stick of memory and the live cd seems to be stable.  The memory check utility didn't catch it and Windows doesn't have a problem with it, but apparently Ubuntu doesn't like that stick of memory for some reason.  I'll run the live cd for a couple days and if it stays stable I'll install it.  I never would have guessed to disable APIC as I don't even know what it is, but the computer seems happy again for now.  I'll update in a few days to verify whether it truly worked or not.  Thanks for all the help.

By the way, for people who have this board, the factory shipped version of the BIOS on this motherboard doesn't have cool and quiet control.  Only later bios versions have it.

---

### Post by CRO-MAGnum PI on 2007-05-10
I would like to bump this as I was/am having the same exact problems on my AMD 64 . My motherboard is a k8x800 socket 754, with two sticks of Corsair 1g DDR400 ram. 

I too, went through numerous burns and versions trying to get the installs to stop locking up after the first tan splash. Finally the Fiesty 64 alternative install cd allowed me to actually format/partition, and install ubuntu, but upon booting into the freshly installed system I was getting the same hard freeze (no mouse or keyboard control, pointer was frozen on the screen). After yanking every piece of hardware I could from my system, I finally pulled one of sticks of memory (they are a matching pair, bought together), leaving only one stick in the dimm closest to my processor. Ubuntu finally booted into the OS completely. After further tinkering, i learned that I only get into ubuntu successfully by having only 1 stick in the dimm closet to the processor.

 I have 3 dimm slots, if I attempt to put one stick in either dimm 2 or 3 (which is no problem for my mobo/bios),  it freezes at the tan splash. Combinations of the two sticks dont work, yet both sticks work fine solo, in dimm 1.  Ran dozens of memory checks. This is the first thread i have found that addressed this problem, I'm going to try the apic toggles. And post results. Also, if anyone can help me evaluate my logs, I would appreciate it. I' ve looked through them as best I could, but i'm green when it comes to log analyzing.

---

