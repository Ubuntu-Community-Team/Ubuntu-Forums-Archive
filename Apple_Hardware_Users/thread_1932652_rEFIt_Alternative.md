---
title: "rEFIt Alternative?"
date: 2012-02-27
forum: Apple Hardware Users
---

### Post by jrogge on 2012-02-27
Hi, I have an intel-based macbook pro (64-bit) running OS X Lion and I'm interested in dual booting Ubuntu and Lion, but I've been having troubles with rEFIt. I read you have to restart your computer twice so I did that but on the second restart my laptop gets stuck on the gray apple icon and the loading swirl forever. I've had to restore my computer twice after trying rEFIt twice and neither times working. I've read the threads on the rEFIt forum but i'm relatively new to these kind of advanced computer topics and the threads with similar problems had answers I couldn't understand. So I'm wondering, is there any alternative to rEFIt? Something similar but that might be more compatible with Lion (I read some where that rEFIt as some issues with Lion.)

Sorry, I realize now that this is probably more appropriate for a Mac forum.

---

### Post by skylen on 2012-03-31
No, I think this is an appropriate place... anyone in the Ubuntu Apple forum will be using rEFIt, unless they are single-booting, but that is not recommended since you can't get Apple hardware support without using the Mac OS.

I would like an alternative to rEFIt, too, since I have the same problem as you! I get the Apple logo, the swirl, takes about 30-60 seconds and then I get the Mac OS.

I had Ubuntu 12.04 dev build working great, no problems.  I had rEFIt, and Mac OS X 10.5 on my MacBook Pro 5,1.  Then I let Ubuntu install a few package updates, it wanted to reboot, and BAM!! now my rEFIt menu doesn't show up, and I can't get to my Ubuntu install, only Mac OS, and with a long delay.  I reinstalled rEFIt and blessed it, etc., but can't get it to come up.

I booted the Ubuntu live cd, chrooted into my HD installed system, and did update-grub, but this didn't fix things.  So frustrating!!

---

### Post by luckylud on 2012-04-07
You can find rEFIind here :
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

install instruction here :
[http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html)

rEFInd is a fork of rEFIt.

It's work fine for me on a macbook pro 8.2

---

### Post by kdegaz on 2012-04-16
I have an early 2008 model MacBook Pro 4,1 which recently died after I fried the graphics chip while playing games.  I just finished replacing the motherboard last week and installed a larger HD (750Gb WD Blue) at the same time.  Previously I used rEFIt to dual-boot with OS X and Kubuntu.  However, after I got it all restored to the new drive, rEFIt seemed to be playing up something rotten - I tried reinstalling the latest version several times, but even the installer seemed to be failing, saying files were already there when they weren't.  Worse still, Disk Utility reported file corruptions (file, directory & free block counts all out, plus volume header needing minor repair) after every boot-up.  I tried repartitioning with several smaller partitions instead of one large OS X one, in case it was just the size being the problem, but no difference.  I was all set to swap back to a smaller HD and ditch the big one.  However... having read this thread, I decided to give rEFInd a go instead, and am pleased to say that so far, it's fixed all the problems - no more disk corruptions, repartitioned to one large one for OS X again ok, OS selection screen appearing at boot-up every time again - I'm a happy bunny!  :-)
A big thank you to the guy who created rEFInd, I've just sent him a few dollars on the donate screen, have a drink on me, cheers! 
):P

---

### Post by gennatolls on 2012-04-18
> **jrogge said:**
> Hi, I have an intel-based macbook pro (64-bit) running OS X Lion and I'm interested in dual booting Ubuntu and Lion, but I've been having troubles with rEFIt. I read you have to restart your computer twice so I did that but on the second restart my laptop gets stuck on the gray apple icon and the loading swirl forever. I've had to restore my computer twice after trying rEFIt twice and neither times working. I've read the threads on the rEFIt forum but i'm relatively new to these kind of advanced computer topics and the threads with similar problems had answers I couldn't understand. So I'm wondering, is there any alternative to rEFIt? Something similar but that might be more compatible with Lion (I read some where that rEFIt as some issues with Lion.)

Sorry, I realize now that this is probably more appropriate for a Mac forum.

I used Bootcamp with a little trickery. I had issues with rEFIt similiar to what you mentioned. Bootcamp is alot more elegant in my opinion.

What I did: (worked to install 11.10 and 12.04 with fully updated Lion)
1. Create desired partion with Bootcamp
2. It then asks you insert your Windows Disk, I did then ejected it after it rebooted (before I got the grey apple)
3. Then i inserted my Ubuntu CD and booted it up and installed away.

Now when i start my mac, i hold down the option key on boot  and i get the choice to boot windows, mac, or mac recovery. Windows obviously being the Ubuntu install but was named that way in Bootcamp. 

During the Ubuntu install I just selected install Ubuntu alongside Mac OS X and it properly configured everything for me. Hope this helps.

Good Luck

---

