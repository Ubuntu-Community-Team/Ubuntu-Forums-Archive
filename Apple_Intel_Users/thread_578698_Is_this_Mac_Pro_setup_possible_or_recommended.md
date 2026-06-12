---
title: "Is this Mac Pro setup possible or recommended?"
date: 2007-10-17
forum: Apple Intel Users
---

### Post by street spirit on 2007-10-17
I'm going to buy a Mac Pro, which I would like to triple boot:

  - Mac OS X
  - Ubuntu Gutsy
  - Windows XP

But before I go and buy it, I'd like to make sure that I won't run into any showstoppers on the Linux side. I've read a few threads on the forums, and there were various problems (sound, partitioning, graphics, fans, etc), but most people seem to have found a solution for their problem. Also, Gutsy isn't out just yet, maybe some of the fixes have made it into the release.

I guess the biggest challenge will be the displays: I'm planning on using a central 24" TFT (the Eizo S2411W), and two cheaper 19" displays to the left and right. I'll have two GeForce 7300 GT graphics cards to be connected to the monitors via DVI.

I'm not going to use any unusual hardware, and no wireless.
Am I going to be alright with Linux, or do you see major problems in what I'm trying to do?
Any insight would be greatly appreciated!

TIA.


PS: I've never actually seen a Mac Pro... are they very loud? can they be set up to be more quiet? Do they get very hot?

---

### Post by nikitavfx on 2007-10-19
Hi,

I can't comment on the dual-display thing, although that should be solvable. As are all the partition and sound problems.

I've got a Mac Pro with Ubuntu 7.10 final on it and after compiling a custom kernel with the mactel patches everything works, except:

-good fan control (one that follows the cpu temperature/load) - this has to be set manually, resulting in somewhat louder fans than on OS X
-CPU frequency scaling - this seems to be a kernel bug, but noone seems to care as it's been known for a long time and it's not been fixed

All said, Ubuntu runs GREAT on my Mac Pro 8-core. The performance of some programs (mainly very CPU intensive ones) is amazing compared to OS X.

So if you don't mind the above mentioned points, go for it. Otherwise wait until these have been fixed.

---

### Post by jamieno10 on 2007-10-19
Hi

I agree with the post above. I have an 8-core, 4 HDD, Geforce 7300GT and use it for numerical work, have 7.10rc on it (no mactel patches) dual-booting with mac os x 10.4.10. The 2 OS are on seperate HDD. 

I have experienced the following problems:

1. Lack of sound (minor for me)

2. DVD drive doesn't close from the keyboard (minor for me)

3. Fan control. 
Although I must say os x isn't much better, the fans don't react there as well. Some users have reported that Firmware upgrades caused more problems. Fan control is apparently firmware controlled?  

4. I've had issues with rEFIt and syncing the MBR/GPT tables when I make convert my other 2 HDD from freespace to ext3. I just can't boot up.

In my opinion, if you can wait, it might be better to do so till the problems have been resolved, which I think will not be that far off.

---

### Post by street spirit on 2007-10-19
Thank you both.

Jamieno, you're probably right about waiting a while. Unfortunately I really need a new workstation soon - I think I'll go ahead and try it (as soon as Leopard is out). Some of the problems (the missing sound, for example) should be solved by the mactel patches (I hope). The missing support for fan and CPU speed control is annoying, though. I really hope the kernel developers get around to that one soon.

Installing the 3 OSes is also going to be a challenge, but with the support of the wonderful people here, I'm pretty confident :-)

(still interested in hearing opinions about the 3-screen setup)

---

### Post by freerick on 2007-10-19
I have two NVidia 6200's, which I'm using to power three monitors that are connected to my workstation. It took me a while to get the drivers going, and to configure xorg.conf correctly, but once that was done, I had no problems with the three monitors. Everything continued to work under Gutsy rc.

In fact, I just hooked up a TV via the S-Video out, which is now acting as a fourth monitor. It just worked. For more info on how I got the three monitor setup going, you can view my thread on the topic [here]("http://ubuntuforums.org/showthread.php?t=381174&page=4").

I'm also thinking of buying a Mac, actually. My current workstation has been very unstable recently, and now has stopped booting completely, so it's time for a change. Hopefully, things will work out better on Apple hardware. I like the fact that with a Mac, I would have an acceptable operating system to fall back to. I wonder if the file systems are compatible. Any ideas?

:popcorn:

---

### Post by DrCR on 2007-10-19
> **nikitavfx said:**
> I've got a Mac Pro with Ubuntu 7.10 final on it and after compiling a custom kernel with the mactel patches everything works, except:

-good fan control (one that follows the cpu temperature/load) - this has to be set manually, resulting in somewhat louder fans than on OS X
-CPU frequency scaling - this seems to be a kernel bug, but noone seems to care as it's been known for a long time and it's not been fixed
Forgive me for being a noob, but what kernel patches? Do you have a HowTo somewheres?

Seriously bumed about the lack of frequency scaling. Is there no way to fix this?! 


To the original poster, you may find my configuration interesting and worth looking into. 
[HowTo: OSX, WinXP, & Vista with Grub hiding, and Linux -- On One Hard Drive.](http://www.linuxforums.org/forum/installation/105234-howto-osx-winxp-vista-grub-hiding-linux-one-hard-drive.html)

DrCR

_____________________
[SIZE="2"]
MacBook Pro Santa Rosa, 2.2GHz, 250GB Scorpio, Ceramique compound
Pending: Tux Logo mod
OSX, WinXP, Vista (MSDN), Vector 5.8 SOHO, Sidux 2007-03
Pending Fusion "bootcamps" pointing to native OS installs[/SIZE]

---

### Post by street spirit on 2007-10-19
> **DrCR said:**
> To the original poster, you may find my configuration interesting and worth looking into. 
[HowTo: OSX, WinXP, & Vista with Grub hiding, and Linux -- On One Hard Drive.](http://www.linuxforums.org/forum/installation/105234-howto-osx-winxp-vista-grub-hiding-linux-one-hard-drive.html)

Interesting read, thank you.
Judging from the linked howto, you got a working multi-boot solution on a Mac**Book** Pro, which uses a different CPU than the Mac Pro. I'm not sure if the Core 2 has the same problems with speedstep as the Xeon.

---

### Post by DrCR on 2007-10-19
Ah, good point. Some how I read that as MacBook Pro rather than Mac Pro.

At any rate, my how to should work for your Mac Pro. As always, backup your data though...I just blew away the partition table of my notebook while attempting to make use of Apple's rubbish disktuil...off to attempt a recovery using testdisk... :mad: :(

DrCR

---

### Post by street spirit on 2007-10-20
> **freerick said:**
> I have two NVidia 6200's, which I'm using to power three monitors that are connected to my workstation. It took me a while to get the drivers going, and to configure xorg.conf correctly, but once that was done, I had no problems with the three monitors. Everything continued to work under Gutsy rc.

This is great news! I was a little worried about this :)

As for the file systems being compatible - I doubt it, but there is a stable ext2/3 driver available for OSX [0], so you should have access to your data, and if you trust the driver enough, you may even be able to do repairs to your linux installation from OSX. You can also read/write HFS+ from Linux. If you're planning on doing that a lot, you'll want to make sure that your users have the same UID in both operating systems.

[0] [http://sourceforge.net/projects/ext2fsx](http://sourceforge.net/projects/ext2fsx)

---

### Post by jamieno10 on 2007-10-20
Hi,

Interesting. So one is able to format the disk as HFS+ (i presume this is mac os x journaled) and read/write data on it from ubuntu?

If you don't mind, how does one do that? Is it stable? (sorry, linux noob here)

Thanks alot!

---

### Post by jamieno10 on 2007-10-20
Hi nikitavfx,

I was wondering how many Hard-disks do you have and if you have been able to mount them in ubuntu and still restart and boot up. If so, could you kindly post some tips?

Thanks

---

### Post by street spirit on 2007-10-20
> **jamieno10 said:**
> Hi,

Interesting. So one is able to format the disk as HFS+ (i presume this is mac os x journaled) and read/write data on it from ubuntu?

AFAIK you can only write to HFS+ partitions that have journaling disabled. You should be able to do that from OSX with Apple's diskutil. There are several threads about HFS+ here on ubuntuforums, and a [through howto can be found here]("http://gentoo-wiki.com/HOWTO_hfsplus").

The related Ubuntu packages are called "hfsplus" and "hfsutils".

---

### Post by nikitavfx on 2007-10-23
Hey Jamieno,

I've only got a single 500GB HD in the Mac Pro. I partitioned it from the shell, than installed refit. I'll try to install more HDs this weekend and tell you how it worked. I don't expect any troubles though as long as I don't try to boot from a different one.

Btw, I'm using the Mac Pro for very CPU-heavy calculations as well.

I'll do a reinstall today with Ubuntu 7.10 final and do more tests.

Cheers

N.

---

### Post by nikitavfx on 2007-10-24
Hey guys,

I've written up a few howtos about kernel compiling and some general issues around the Mac Pro. Check it out and leave some comments so I can improve it.

[http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)

Thanks

---

