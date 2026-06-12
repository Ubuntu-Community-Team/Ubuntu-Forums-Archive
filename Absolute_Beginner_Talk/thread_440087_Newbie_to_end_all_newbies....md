---
title: "Newbie to end all newbies..."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Ghostlove on 2007-05-11
I installed Ubuntu this morning and, being the impatient kinda gal I am, jumped right into it with very little preparation. I know, I know - I shouldn't have done that. However, it's too late now and I'm loving Ubuntu... so I have some questions. I have Googled, I have searched the forums and documentation but am having trouble understanding a lot of this - it's a very steep learning curve, I guess!

I think when I installed Ubuntu it did its magic automatic partitioning of my laptop's hard drive. However, I have no idea how to access the other partition. I have no idea how to access Windows at all, so I can copy the stuff I want onto a CD and get it into Ubuntu that way. I have tried many of the things from my searches to mount my Windows partition so I can access the files that way, but I'm just getting error after error. All I want is to grab the stuff from my Thunderbird/Firefox preferences and uninstall a load of crap I'll no longer be using.

If anyone could possibly take the time to explain this to me - bearing in mind I have never SEEN anything Linux-related before this but am ready and willing to learn - I would be so, so grateful and might offer homemade biscuits.

Thank you in advance!

---

### Post by Najand on 2007-05-11
Can't you find your windows partition at:
PLACES -> Computer

---

### Post by Kobalt on 2007-05-11
Hello,

During your install of Ubuntu, you selected to install Ubuntu only on a certain part (partition) of your hard drive and not the whole HD right ?
If so, you should see your windows partition from Places > Computer.

---

### Post by aeiah on 2007-05-11
could you open the terminal and run:

```
sudo fdisk -l
```

and copy and paste it in here for us to look at. this should tell you what partitions exist, both mounted and unmounted.

the terminal is located in the applications menu, under accessories

---

### Post by Ghostlove on 2007-05-11
ghostlove@Ghostlove:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36481   293033601    7  HPFS/NTFS

-----

Wow. That's confusing. When I used the documentation the terminal told me that /dev/hda1 didn't exist... now I see why. I just need to figure out which one of these I ought to be using!

---

### Post by seshomaru samma on 2007-05-11
```

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 36481 293033601 7 HPFS/NTFS
```
this is your Windows partition
it appears you have two harddisks

sda is the first one- where you have Linux
sdb is the second one -where you have Windows

i think your discs are probably sata and so they appear as sda/sdb instead of hda/hdb (for IDE type discs)

---

### Post by rich.bradshaw on 2007-05-11
Normally it should just automatically be in your places menu.

---

### Post by rich.bradshaw on 2007-05-11
If you have internet, go to Add/Remove programs on the menu at top left, and search for ntfs-config. Install it, then run it and select to let it read/write both selections.

Then it should work.

---

### Post by Ghostlove on 2007-05-11
Well it's not in my Places menu which is why I was confused.

Yes I do have two hard disks, one is an external hard drive, one is the internal drive of my laptop (40gb). :confused:

---

### Post by Ghostlove on 2007-05-11
> **rich.bradshaw said:**
> If you have internet, go to Add/Remove programs on the menu at top left, and search for ntfs-config. Install it, then run it and select to let it read/write both selections.

Then it should work.

I have already done that. Unless I am looking in utterly the wrong place, I can't find my Windows files, only the ones on the external drive. :(

---

### Post by Ghostlove on 2007-05-11
> **seshomaru samma said:**
> ```

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 36481 293033601 7 HPFS/NTFS
```
this is your Windows partition
it appears you have two harddisks

sda is the first one- where you have Linux
sdb is the second one -where you have Windows

i think your discs are probably sata and so they appear as sda/sdb instead of hda/hdb (for IDE type discs)

That one's already on my desktop; it's my external hard drive.

---

### Post by lakersforce on 2007-05-11
If I remember correctly, the default settings at the partition manager under the install is to erase everything and make a new partition. And you say the ntfs is your external? I am sorry to tell you this, but you have erased your windows partition. Everything you had on it is now gone :(

---

### Post by Inxsible on 2007-05-11
Could you open up the Terminal and enter in this command and paste the output for us 
```

gedit /etc/fstab

```
 
*Note : I just want to see if the sdb (NTFS drive) is mounted. If not then we'd have to sudo it and make changes to the fstab
 
 
EDIT: Whoops too late
 
I shall say it for you GhostLove : "Oh Crap !!!! "

---

### Post by lakersforce on 2007-05-11
> **lakersforce said:**
> If I remember correctly, the default settings at the partition manager under the install is to erase everything and make a new partition. And you say the ntfs is your external? I am sorry to tell you this, but you have erased your windows partition. Everything you had on it is now gone :(

Unless of course anyone knows of a recovery program?

---

### Post by Ghostlove on 2007-05-11
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=cea80802-11c0-411d-b34f-15202e153f28 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=86522661-9ef0-4155-bce3-4b60359a9c3d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_GB.UTF-8 0 0

---

### Post by Ghostlove on 2007-05-11
> **lakersforce said:**
> Unless of course anyone knows of a recovery program?
Well it's a good thing that I keep everything important on the external; the thousands of photos of my son, all my music and stuff - and I copied the 'My Documents' folder to the external drive as well. The stuff on my laptop hard drive was useful but not irreplaceable, thank goodness!

---

### Post by drowner on 2007-05-11
> **seshomaru samma said:**
> ```

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 36481 293033601 7 HPFS/NTFS
```
this is your Windows partition
it appears you have two harddisks

sda is the first one- where you have Linux
sdb is the second one -where you have Windows

i think your discs are probably sata and so they appear as sda/sdb instead of hda/hdb (for IDE type discs)

edit: been done

ghostlove, i am pleased you were smart enough to backup anything irreplaceable.

Welcome, permanently, to ubuntu!

---

### Post by SaddaGocaraRupa on 2007-05-11
you can access your external drive right?

---

### Post by Ghostlove on 2007-05-11
> **SaddaGocaraRupa said:**
> you can access your external drive right?
Yes, thankfully!

---

### Post by drowner on 2007-05-11
> **SaddaGocaraRupa said:**
> you can access your external drive right?

No reason why not.

Even though writing to it will involve using the ntfs-3g thing, she will be able to copy the files no problem.

And, by the looks of things, its been mounted already, so, no problems at all.

(i think..... !)

---

### Post by rich.bradshaw on 2007-05-11
Aha, problem solved...

I can't remember how it's labelled in the isntaller, but was it clear that the automatic configuation would erase what's on the disk and start from scratch?

Is it a good idea having that choice so prominent? People coming from Windows seem to be conditioned to just click yes on every dialog box they see... Is it really fair that the first one they will see will erase their whole drives?

---

### Post by drowner on 2007-05-11
> **rich.bradshaw said:**
> Aha, problem solved...

I can't remember how it's labelled in the isntaller, but was it clear that the automatic configuation would erase what's on the disk and start from scratch?

Is it a good idea having that choice so prominent? People coming from Windows seem to be conditioned to just click yes on every dialog box they see... Is it really fair that the first one they will see will erase their whole drives?

It does warn you.

Its a cruel harsh lesson to being with for new linux people... you can do whatever you want, so THINK ;)

---

### Post by yanqui on 2007-05-11
He did say he jumped in impatiently, at least he was honest with us about it.  Welcome to Ubuntu, there's something of a learning curve coming from Windows, but it's a really cool OS.

There is a great lesson here, and it's this:  the GUI has made operating systems look similar.  But they're not.  Even though Ubuntu "puts the cookies on the bottom shelf" for newbies like us, it's still going to be really important to do backups of your critical stuff before you try anything for the first time, because for one thing, the terminology is different.  "Mount?"  I don't "mount" anything in Windows; I had to learn what that meant, along with a BUNCH of other stuff.  Upside--it wasn't difficult.

---

### Post by Ghostlove on 2007-05-11
> **yanqui said:**
> He did say he jumped in impatiently, at least he was honest with us about it.  Welcome to Ubuntu, there's something of a learning curve coming from Windows, but it's a really cool OS.

There is a great lesson here, and it's this:  the GUI has made operating systems look similar.  But they're not.  Even though Ubuntu "puts the cookies on the bottom shelf" for newbies like us, it's still going to be really important to do backups of your critical stuff before you try anything for the first time, because for one thing, the terminology is different.  "Mount?"  I don't "mount" anything in Windows; I had to learn what that meant, along with a BUNCH of other stuff.  Upside--it wasn't difficult.

Hee hee - just for the record, I'm a she... ;)

I copied the stuff I really, really wanted to keep onto the external drive, and I'm not particularly bothered by the loss. My plan was to get myself 100% free of Microsoft in the end. It just happened a little quicker than I anticipated!

---

### Post by mikewhatever on 2007-05-11
Thumbs up and well done, Ghostlove.:guitar:

---

### Post by Josey on 2007-05-11
> **Ghostlove said:**
> Hee hee - just for the record, I'm a she... ;)

I copied the stuff I really, really wanted to keep onto the external drive, and I'm not particularly bothered by the loss. My plan was to get myself 100% free of Microsoft in the end. It just happened a little quicker than I anticipated!

lol

---

### Post by drowner on 2007-05-11
ghostlove, is that you in your avatar?

<3

---

### Post by yanqui on 2007-05-11
> **Ghostlove said:**
> Hee hee - just for the record, I'm a she... ;)


HAha, so am I!

My laptop has windows, and I am not ready to leave the Windows world, and I didn't have another machine onto which i could load Ubuntu, so I put THAT on a USB external hard drive and I boot from it to the laptop.  But I could also boot from it to any other machine that would recognize it as a hard drive, so after I get the Frankenputer up and running again, I'll give it a try on that.

Welcome to Ubuntu world!

---

### Post by Ghostlove on 2007-05-11
> **drowner said:**
> ghostlove, is that you in your avatar?

<3

Yes. :P

[QUOTE=yanqui]HAha, so am I!

My laptop has windows, and I am not ready to leave the Windows world, and I didn't have another machine onto which i could load Ubuntu, so I put THAT on a USB external hard drive and I boot from it to the laptop. But I could also boot from it to any other machine that would recognize it as a hard drive, so after I get the Frankenputer up and running again, I'll give it a try on that.

Welcome to Ubuntu world![/QUOTE]

Thank you!

I appear to have unmounted my hard drive. Now I need to remember how I did it. This is a very steep and very fast learning curve!

---

### Post by jkeyes0 on 2007-05-11
> **Ghostlove said:**
> Yes. :P



Thank you!

I appear to have unmounted my hard drive. Now I need to remember how I did it. This is a very steep and very fast learning curve!

If the drive is listed in your /etc/fstab file (the one you listed earlier), rebooting should make it show back up.

---

### Post by Ianman on 2007-05-11
> **Ghostlove said:**
>  This is a very steep and very fast learning curve!

If you have been using Microsoft products for a long time, it certainly does seem like a steep learning curve but I have found that the more I use it the sense Linux makes. It has so much more power and ability than Windows.

Stick with it and dont' be afraid to ask questions here...in my opinion there is no such thing as a stupid question!

Welcome to Linux!

---

### Post by sriku on 2007-05-16
Could you provide some instructions to install Ubuntu onto a partition on my external USB drive?
Specifically- 
1. Partitioning the drive (its 80 gig, and i want 30 gigs free for auto syncing my ipod)
2. Does my laptop(vaio c-series, 1.66 Dual core,1GB Ram) automatically detect a usb drive to boot from?
3. Will disk access times be increased by booting from an external drive?
4. Any other dos and dont's for installing ubuntu onto an external drive.

I cant touch the laptop hard drive because I need all the gigs it has already. Vista bloatware and installed apps are waaay too heavy.

Thanks in advance.
sriku

ps: I got a pounding for installing ubuntu on my office desktop, server support team hates me now. So the usb drive is my only option.

---

### Post by infurnus on 2007-05-16
i imagine that IT would be a little upset if you reinstalled ubuntu over their server solution that's f*in hilarious tho i haven't thought of trying that one yet!

i would suggest reading through the forums to find how you should partition your hard drive

[http://ubuntuforums.org/showthread.php?t=315421](http://ubuntuforums.org/showthread.php?t=315421)

a way to check usb boot is in BIOS otherwise get your model number and i would look at the documentation on line at sony's website

[http://ubuntuforums.org/showthread.php?t=366855](http://ubuntuforums.org/showthread.php?t=366855)

even through usb 2.0 its not too bad i had an external i used to boot from it has SuSE on it. i could tell it was a little laggy from time to time but this also depends on the seek speed of your disk and its ability to cache large amounts of data your limited to the hardware your using

[http://ubuntuforums.org/showthread.php?t=414564](http://ubuntuforums.org/showthread.php?t=414564)

[http://ubuntuforums.org/showthread.php?t=407994](http://ubuntuforums.org/showthread.php?t=407994)

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Good luck hopefully this helps out a little.

---

### Post by sriku on 2007-05-17
Thanks Infurnus,
 I'll prowl around the forums more, and check out your links. Will update here when(erm and maybe 'if') I successfully complete the installation on my USB drive. In the meanwhile, I'm still gonna install ubuntu on my office desktop, only now I'll be smart abt it and use wubi :) what IT won't know, won't make them hurt me :)
Wish me luck!

---

### Post by yanqui on 2007-07-19
> **Ianman said:**
> If you have been using Microsoft products for a long time, it certainly does seem like a steep learning curve but I have found that the more I use it the sense Linux makes. 

Made it a lot easier to learn MAC!

---

### Post by thefoolisme on 2007-07-19
> **Ghostlove said:**
> Well it's a good thing that I keep everything important on the external; the thousands of photos of my son, all my music and stuff - and I copied the 'My Documents' folder to the external drive as well. The stuff on my laptop hard drive was useful but not irreplaceable, thank goodness!

Can I just say Congrats on at least backing up your stuff?  So many people hit this forum complaining that Ubuntu wiped out their stuff, and they didn't have backups.  I'm glad you were one of the thinking ones.  Good luck with your ubuntu adventures!:guitar:

---

