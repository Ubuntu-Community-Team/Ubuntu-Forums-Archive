---
title: "What'll happpen if..."
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Lepht on 2007-04-13
What'll happpen if I actually install Ubuntu on my computer? What would happen to my XP? Is it a one way trip? Right now I am only gaving it a test run from the CD. Sorry for the super noob question.

---

### Post by xopher on 2007-04-13
You can have both installed at the same time, and at bootup, choose which one you wish to use.

There's nothing dangerous in doing this, as long as you follow a guide that tells you not to overwrite all the existing partitions ;)

Here's even a video of how to do it.. :rolleyes:

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

**WARNING - possibly unstable:**

[https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

^ This is actually an installer for Windows. Just click on the .exe and it'll install Ubuntu right beside your Windows installation. But I wouldn't install using this. First, you don't learn anything, and second, if things go bad, you haven't learned anything - and can't fix it ;)

---

### Post by compmodder26 on 2007-04-13
If you install and wish to keep Windows, the installer will walk you through it.  In most cases, this works flawlessly, no problems.  However, there is always the chance things can go awry.  So you should always back up your important data from windows before attempting.

---

### Post by aysiu on 2007-04-13
If you're worried, keep giving it a test run for a couple of weeks. Get used to Ubuntu.

It is possible to set up a dual boot, but if you don't know what you're doing, you could easily erase your important data so **back up anything that's important to you**. And the more comfortable you are using Ubuntu's live CD, the easier it'll be for you to troubleshoot any problems that might arise.

Don't rush into an installation before you're ready.

---

### Post by daynah on 2007-04-13
When you go to install Ubuntu, friendly ubuntu will give you the choice of...

A) Letting Ubuntu eat your entire computer, yum yum! This is technically called reformatting your computer. This means you lose all data, unless you made a backup.

B) Letting Ubuntu share and play nice with XP. Ubuntu will tell XP to scoot over and split up the room in the computer and they'll be nice and happy on the same harddrive. You will ge tto tell Ubuntu how much you love XP and how much you love Ubuntu and thus, how many toys each get. This is really called partitioning. After you tell Ubuntu "No, don't eat my computer!" Ubuntu will ask how much room of your hard drive you want to leave XP and how much room you want to leave Ubuntu. When you've done that, you've Dual Booted your computer. I'm lazy so I always Dual Boot 50% 50%, which I think is a good idea unless you have your hard drive almost full. In that case, you'll want to clean out your harddrive while on Windows too make room for the new baby -- I mean Ubuntu.

Noobs are always welcome. :) Have fun!

---

### Post by Lepht on 2007-04-13
Now this guide you said, where can I find it? Or is it something that would should up right before installation? 

Now, I have seen OSX's boot camp when handling dual OS'. For exmple, when managing harddrive spaces it allows you to set up a percentage, say gave OSX 60% of HD sapce and XP 40%. I saw this on a demo somewhere thought it was neat. 

So, how would Ubuntu's used HD space show up in XP (and vise-versa)? Would it just be a bunch of unreadable codes in a folder or would it be totally invisible.

Edit: HD space question answered while I was typing, you read my mind!

---

### Post by aysiu on 2007-04-13
Read these:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and *please* take seriously my advice about not diving into this too soon *and* backing up everything before you do anything!

---

### Post by Patrick K on 2007-04-13
When you install Ubuntu, it will require it's own disk space. You will have an opportunity make partitions for it (a min of 2 are required). During installation, a boot loader (it's call GRUB) will be installed in the hidden partition at the start of the boot drive (your Windows install currently has it's boot loader there). When you boot the computer, GRUB will display a menu with all the existing operating systems installed on your system. You can choose which OS you want to boot to. 

Properly installed, Linux will not touch your Windows installation. The only danger point is during the partitioning operation. You will likely need to shrink the Windows partition to make room for Linux (the tools are included on the Ubuntu install cd). Defrag the drive first to compact the files and make empty space at the end of the drive. You should backup your windows system, just in case something goes wrong, although this is very rare. 

After shrinking the existing partition, you will create two partitions. One for the "root" directory (the actual symbol is "/") and a swap partition (much like the swap file in windows). You could also create a /home partition (this has several advantages, such as keeping your personal data and setting safe if you need to reinstall). 

1 GB is a good size for the swap partition but this depends on the amount of memory installed (less memory needs more swap, I have 512meg and use a 1 GB swap, AFAIK, it has not been used, yet). I suggest using at least 10 GB for / and, it you decide to use it, another 10+ GB for /home. 

HTH

---

### Post by Lepht on 2007-04-13
To test with live CD is nice and all, but when ever I turn my computer off all the Ubuntu  settings are not saved. Maybe I can fix this just by putting system on hibernattion instead of shutting it down everytime.

Aside from HD space, are there any other downsides interms of performance for running dual OS'? 

When you said "but if you don't know what you're doing, you could easily erase your important data". Can you gave a quick example for how this could happen?

---

### Post by aysiu on 2007-04-13
> **Lepht said:**
> To test with live CD is nice and all, but when ever I turn my computer off all the Ubuntu  settings are not saved. Maybe I can fix this just by putting system on hibernattion instead of shutting it down everytime. You can actually save your settings by following this tutorial:
[HOWTO: Persistent home on USB key](http://ubuntuforums.org/showthread.php?t=9893)

> Aside from HD space, are there any other downsides interms of performance for running dual OS'?  None at all. You boot only one OS at a time, so the performance is the same as single boot for both OSes.

> When you said "but if you don't know what you're doing, you could easily erase your important data". Can you gave a quick example for how this could happen? You select the wrong partition to reformat (oops! I meant to reformat /dev/hda2 for Ubuntu, but I selected /dev/hda1, my Windows partition!)

---

### Post by Tsen on 2007-04-13
Here's a tip from my personal experience:
I leave Windows with 60 GB and Ubuntu with 20 GB.  
A lot of people have been saying to split it fifty-fifty, and that works for some cases, but Linux really doesn't need a whole lot of space.
The reason I split it the way I did is because Windows includes a lot of space-consuming games on my computer, so I give it a little extra space.  
Then, I have a massive 35 GB music library, so I put all of that on the Windows partition, so iTunes and all that can find my music without a hassle.
The benefit of this is that Ubuntu can read NTFS (Windows) partitions, but Windows can't read ext3 (Linux) partitions.  So by putting my music on the Windows partition, I can read it from both OS's.  Of course, by default, Ubuntu can only read NTFS, but can't modify the files.  If you need to change that, you'll have to install NTFS-3g, but that's not too big a deal.

---

### Post by Lepht on 2007-04-13
> and please take seriously my advice about not diving into this too soon and backing up everything before you do anything!

Yes, I'll be sure to keep that in mind.

> 
Quote:
When you said "but if you don't know what you're doing, you could easily erase your important data". Can you gave a quick example for how this could happen?

You select the wrong partition to reformat (oops! I meant to reformat /dev/hda2 for Ubuntu, but I selected /dev/hda1, my Windows partition!)

I was asking more of the mistakes during the usage of the OS, if that make sense...

---

### Post by aysiu on 2007-04-13
> **Lepht said:**
> 
I was asking more of the mistakes during the usage of the OS, if that make sense... Oh, that's less likely.

---

### Post by kittyhawk63 on 2007-04-13
There is another alternative, which I apologize for if I missed it reading quickly through the replies. You can do what I do. You can install another hard drive and have Windows on one and Linux on the other. First install Windows to the hard drive of your choice. Now with that done, change the Windows' hard drive jumper to slave and allow the other hard drive for Linux be the master. Make sure both hard drives are connected to the CPU. Install Linux on the master hard drive. Make sure you choose the correct hard drive. My hard drives are different sizes and are therefore easy to select. 
Linux will recognize both hard drives and after installation will allow you to choose which drive you want during boot up.
kh

---

### Post by rajeev1204 on 2007-04-13
> **daynah said:**
> When you go to install Ubuntu, friendly ubuntu will give you the choice of...

A) Letting Ubuntu eat your entire computer, yum yum! This is technically called reformatting your computer. This means you lose all data, unless you made a backup.

B) Letting Ubuntu share and play nice with XP. Ubuntu will tell XP to scoot over and split up the room in the computer and they'll be nice and happy on the same harddrive. You will ge tto tell Ubuntu how much you love XP and how much you love Ubuntu and thus, how many toys each get. This is really called partitioning. After you tell Ubuntu "No, don't eat my computer!" Ubuntu will ask how much room of your hard drive you want to leave XP and how much room you want to leave Ubuntu. When you've done that, you've Dual Booted your computer. I'm lazy so I always Dual Boot 50% 50%, which I think is a good idea unless you have your hard drive almost full. In that case, you'll want to clean out your harddrive while on Windows too make room for the new baby -- I mean Ubuntu.

Noobs are always welcome. :) Have fun!


Nice use of words daynah  :)

---

### Post by Lepht on 2007-04-13
@xopher:
Thanks for the video, A great visual presentation is always appreciated. 

@kittyhawk63:
One HD each does sound very ideal :o  


Is there a way to use Daemon tool to reboot with the live CD? B/c that way, the CDrm speed won't limit me anymore.

I know I am totally getting way far ahead of myself, but, is uninstalling Ubuntu (God forbid) as easy as installing?

---

### Post by phr0ze on 2007-04-13
I'd say take the plunge. In the Ubuntu installer (at least in Edgy) you make all your choices but Ubuntu doesn't do anything until you confirm a final screen. So click the install button, take a peek at the options in there and if you feel comfortable, go ahead. If you don't just cancel the program.

BTW: If you are doing this, I recommend that you defrag windows first. Ubuntu needs to clear space at the end of the drive and it will take longer if it has to move fragmented data.

---

### Post by Tsen on 2007-04-13
No, you can't run it from Daemon Tools.  Daemon Tools is only running in Windows, and you're installing Linux outside of Windows, so it won't work.

---

### Post by Lepht on 2007-04-14
Here is another question.

What would I have to do with updates once a newer version of ubuntu is out? Right now I am checking out the 6.06LTS version, but I know that version 7.X is going to be out soon. How would it update?

---

### Post by Patrick K on 2007-04-14
You need to upgrade to 6.10 first. AFAIK, you cannot skip an upgrade.

---

### Post by Lepht on 2007-04-14
How would this upgrade work? Do I need to download the new version and burnt it on a live CD and install it that way, or would Ubuntu do it on it's own, and all I have to do is click yes when it asks to update (similar to XP' tuesday patches?) Thanks.

---

### Post by Patrick K on 2007-04-14
That I don't know. I have only installed Edgy (6.10) and haven't tried upgrading, yet. That will come in a couple weeks when Feisty comes out.

---

### Post by aysiu on 2007-04-14
Feisty Fawn comes out in five days.

---

