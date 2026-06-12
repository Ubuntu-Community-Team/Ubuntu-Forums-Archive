---
title: "re-installing a crashed XP on a dual boot dual hard drive ubuntu"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by chaotik on 2008-01-28
I had a dual boot system with XP and ubuntu 7.04, each on their own hard drive.   When I created the system, I had installed xp first and then ubuntu.   The windows system crashed and will require a re-install.  I am afraid that when I re-install windows I will overwrite my MBR and be unable to use ubuntu.  

How can I make sure that after I re-install windows, I can get my dual boot configuration working properly without having to reinstall ubuntu?

Thanks.

---

### Post by TygerTung on 2008-01-28
Open up your box and then unplug your hard drive with ubuntu on it. XP won't even know it is there and it will be all fine I reckon.

---

### Post by chaotik on 2008-01-28
So if I disconnect the hard drive with ubuntu on it, and reload xp on its ntfs hard drive, the grub bootloader and configuration will be preserved because that is on the ubuntu hard disk?  And when I boot up the machine with both hard drives connected it will default to the grub?  And nothing has to be done with the MBR (which I think resides on the windows hard drive)?

Just want to make sure before I screw things up worse.

---

### Post by TygerTung on 2008-01-29
Yep that sounds about right.

To ensure that the grub loads up though you're gonna have to go into the bios and make sure that the boot order will be the hard drive with ubuntu on it is loading first after you've finished the job if you know what I mean.

---

### Post by gangrelsurf on 2008-01-29
errrr, maybe. It depends which mbr your boot off of Try this:

shut down, take out the windows harddrive. Boot up. If you boot to grub and then ubuntu, and you plan on keeping the partitions the same through tis reinstall, you're good. You can do what TygerTung says.

If that does not work then you are booting off the mbr on the windows drive and it will be a bit trickyer. Windows will over write that when you reinstall

---

### Post by chaotik on 2008-01-29
Ok. 

I disconnected the windows hard drive, and then tried to boot.

I got an error 21 and grub did not load completely, and no ubuntu.

So this means I am booting off the MBR on the windows hard drive, which will be overwritten when I re-install windows.  

If I do this, is there a way to restore the grub bootloader to access ubuntu???

---

### Post by Moop on 2008-01-29
You can restore grub using the Super Grub cd. 

[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

---

### Post by plucky on 2008-01-29
> If I do this, is there a way to restore the grub bootloader to access ubuntu???

If you have a live cd see this  [thread](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

Good luck

---

### Post by chaotik on 2008-01-30
I had no luck.  In fact, neither the live CD or superGrub worked.  That may have been my fault.  In fact, I ended up screwing everything up and then had to do a re-install of Ubuntu.  Lost everything......

I am a slow learner.....

Now I have the computer with 2 hard drives.... so I am looking for suggestions  (very explicit instructions would be appreciated) as to what to do now.  I would like to have a dual boot ubuntu & XP, each on their own hard drive.... but avoid the same scenario again so if the windows system crashes I will not be dependent on that drive for booting.    (originally I installed xp and then ubuntu over xp).

---

### Post by Shazaam on 2008-01-30
What you can do is run a seperate bootloader like GAG. It will run from a cd or floppy. Do a search and you will find many more similar apps.
IF you read through this....

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

you will be able to understand grub better.

---

