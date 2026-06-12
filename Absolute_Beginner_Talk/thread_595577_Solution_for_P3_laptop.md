---
title: "Solution for P3 laptop"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by wanderingpilgrim on 2007-10-28
I have a Compaq Presario 1700 laptop currently running Windows 2000.  IT is a Pentium 3 with 256MB of memory.  Sometimes, especially multitasking or online, it runs very slowly.  I have been thinking about running Ubuntu 7.04 or 7.10 on it because I know Ubuntu 6.06 is considerably more efficient than Windows 2000.  I have really enjoyed Windows 2000 and it runs well on even a Pentium, but my P3 has been running very slow, more so than the aforementioned Pentium 166.  I thought I'd replace windows with Ubuntu, but I am having trouble getting Feisty installed.  It will load on the live cd but will hang indefinately on any attempt to install.  On other machines, it runs fine though.  I have in the recent past had success with Ubuntu 6.06.  Should I just stick with 6.06?  Can I upgrade it after the initial install?  Can I upgrade either 6.06 or 7.04 to play mp3s and jpg files out of the box?  This is a large part of why I have not already replaced Windows for good on my laptop.

What should I run?

Thanks

---

### Post by Six_Digits on 2007-10-28
I'd suggest 7.04. Worked great for my old machine!

Try Wubi's installer [here.]("http://wubi-installer.org/")

---

### Post by kerry_s on 2007-10-28
with 256 you should be using the alternate disk to install. you might also want to consider going with xubuntu instead.

---

### Post by alwiap on 2007-10-28
> **kerry_s said:**
> with 256 you should be using the alternate disk to install. you might also want to consider going with xubuntu instead.

Xubuntu uses XFCE which is lighter on resources so you might want to check that out, [www.xubuntu.com](www.xubuntu.com)

---

### Post by oilchangeguy on 2007-10-28
you won't be able to load even 6.06's live cd with 256mb of ram. your laptops video is taking some of that ram. and you have to have 256mb min. to install via the live cd. and as far as your windows 2000 install, how many icons are there to the left of the clock?(all programs that load at startup take system resources) how long has it been since you've done a fresh install? you've probably got spyware, maybe a virus. when's the last time you did system maintenance? defrag, delete temp internet files, etc.? don't blame the os, you've got to maintain it, inorder for it to run at top speed.

---

### Post by PhutterMan on 2007-10-28
I run regular Ubuntu (not Xubuntu, I didn't notice much/any performance difference between XFCE and gnome) on a Compaq Armada M300 with a 500mhz p3 and 320MB of ram.  It works fine.  It's not lightning fast, but it gets the job done.

I installed by netbooting it with a file I hosted on my desktop and then did a network install from there, because it hasn't got an optical drive (or a floppy drive - it's really thin and light) and can't boot from USB.

---

### Post by linuxlizard on 2007-10-28
I really love ubuntu, and prefer it wherever possible, but tell you what- I've got a pentium 3 700 laptop with 192 mb ram and ubuntu doesn't cut it on there, even xubuntu was painfully slow for me. 

I run pcfluxboxos on there and it flies. It feels as fast as my desktop running ubuntu, and my desktop is an amd athlon xp 2800+ with 756 mb ram.

Highly recommend pcfluxboxos for older hardware. It's full featured like ubuntu and you can mp3 and jpg out of the box.

---

### Post by Paulmd on 2007-10-29
> **wanderingpilgrim said:**
> I have a Compaq Presario 1700 laptop currently running Windows 2000.  IT is a Pentium 3 with 256MB of memory.  Sometimes, especially multitasking or online, it runs very slowly.  I have been thinking about running Ubuntu 7.04 or 7.10 on it because I know Ubuntu 6.06 is considerably more efficient than Windows 2000.  I have really enjoyed Windows 2000 and it runs well on even a Pentium, but my P3 has been running very slow, more so than the aforementioned Pentium 166.  I thought I'd replace windows with Ubuntu, but I am having trouble getting Feisty installed.  It will load on the live cd but will hang indefinately on any attempt to install.  On other machines, it runs fine though.  I have in the recent past had success with Ubuntu 6.06.  Should I just stick with 6.06?  Can I upgrade it after the initial install?  Can I upgrade either 6.06 or 7.04 to play mp3s and jpg files out of the box?  This is a large part of why I have not already replaced Windows for good on my laptop.

What should I run?

Thanks

I think you should figure out why it's slow. As you stated, win2k on your p166 is running better than your p3. Win2k runs just fine on p2 machines.

Either you have a software problem, viruses, spyeware, or just too many quickstarters. Or the apps you have been running of late are more cpu intense than the ones you used to run.

Or a hardware problem

I suspect hardware, as software shouldn't interfere with the linux install. In particular, I suspect the hard drive. hard drives can start to read really slow before they start to fail entirely. 

Download the appropriate diagnostic from the manufacutuor of your hard drive. seatools from seagate will do, if you don't know.

Also run memtest from the Ubuntu live cd.

To answer the 2nd part of your question: Fiesty and dapper, and gutsy are all perfectly capable of reading mp3s and jpgs.

For mp3s, I perfer xmms. It's not "pre-installed", but it is in the repositories.

Figure out what's wrong with the machine, then decide what to do with it.

---

### Post by Six_Digits on 2007-10-30
> **oilchangeguy said:**
> you won't be able to load even 6.06's live cd with 256mb of ram. your laptops video is taking some of that ram. and you have to have 256mb min. to install via the live cd. and as far as your windows 2000 install, how many icons are there to the left of the clock?(all programs that load at startup take system resources) how long has it been since you've done a fresh install? you've probably got spyware, maybe a virus. when's the last time you did system maintenance? defrag, delete temp internet files, etc.? don't blame the os, you've got to maintain it, inorder for it to run at top speed.

It's true. I'm constantly cleaning people computers out for them, from gigabytes of temp files to golfball size chunks of dust in the case. You paid alot for your machine, care for it.

---

