---
title: "Live CD and Hard disk repair"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by trorion on 2006-03-16
Thanks for reading.

My wife's laptop is fried and I'm hoping that someone can help me.

Problem: when she tries to boot on windowsXP she gets a "could not access drive" problem.  I can mount the hard disk with DSL and am now trying to boot with an Ubuntu live CD (familiarity).

Once I get the system up with Ubuntu live, how can I do a hard disk repair using Ubuntu?  Otherwise are there any suggestions?  Her system CD tells me it will delete her drive so until I get her a current backup I don't want to do that.  My W2K cd won't even let me go to a prompt login so that doesn't work.

Alternatively, is there a way to burn a backup of her data with Ubuntu live on her only CD player?

Thanks in advance.

---

### Post by atoponce on 2006-03-16
A couple of questions first: is the cdrom a cd burner, and can you mount the windows drive?

---

### Post by trorion on 2006-03-16
Yeah, I can get the hard drive mounted and it does have a cd burner; but only 1 cd drive so my Ubuntu live CD is currently occupying the cd burner :-k

---

### Post by atoponce on 2006-03-16
OK.  No problem, hopefully.  Do you have other computers on the network?  You could transfer the data to a network share using samba.  If that is too much of a pain, then do you have a USB thumb drive to send the data too?  If worst comes to worst, do you have a GMail account?  You could attach her data (up to 10MB) and send it to your GMail address.  Just some ideas.

---

### Post by trorion on 2006-03-16
0 networking on the computer right now.

She only has about 2g of data that needs backing up.  I have an old pcmcia 10/100 card that I can install and re-boot ubuntu live to do some networking and hardwire it to the network.

No way to burn to a CD with ubuntu live?

stepping afk for 1/2 hour or so.

---

### Post by AtinLango on 2006-03-16
Just thinking. Can't Ubuntu Live run off RAM and consequently free the CD drive? I can't check now.

---

### Post by DJ Scribblinni on 2006-03-17
Well if you still wanted to, you can use DSL.  It may not be as familiar but it is still possible.  At the boot prompt type: dsl toram
That will allow DSL to run using the computers ram instead of using a cd, which in turn allows you to burn files to a CD...

Mount the Hard drive, and CD-ROM
right click the desktop and select apps, then tools, then CD Burn App
It is a very crude but very useful app
The hard drives usually mount into the /mnt folder
find that folder and you should see your hard drive, from there add the files by hitting the spacebar button
after the most files possible have been selected, you wanna select Create Image..
(Make sure you insert a blank CD in the tray)
After it lets you know its finished, select Write data CD
The data writing should begin...

Theres an option for ya, I hope it helps you out

---

### Post by Jimmey on 2006-03-17
I'd boot the liveCD, create a new partition at the end of the drive, mount it, store all the data in there, delete the Windows partition, and either re-install Windows, or install Ubuntu. Would that be possible?

---

### Post by sjsenthilkumar on 2008-05-09
My wife's laptop is fried and I'm hoping that someone can help me.

Problem: when she tries to boot on windowsXP she gets a "could not access drive" problem.  I can mount the hard disk with DSL and am now trying to boot with an Ubuntu live CD (familiarity).

Once I get the system up with Ubuntu live, how can I do a hard disk repair using Ubuntu?  Otherwise are there any suggestions?  Her system CD tells me it will delete her drive so until I get her a current backup I don't want to do that.  My W2K cd won't even let me go to a prompt login so that doesn't work.

Alternatively, is there a way to burn a backup of her data with Ubuntu live on her only CD player?

Thanks in advance.[/QUOTE]

---

