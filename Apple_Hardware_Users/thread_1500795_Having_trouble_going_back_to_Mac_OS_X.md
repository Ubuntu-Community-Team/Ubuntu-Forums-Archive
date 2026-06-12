---
title: "Having trouble going back to Mac OS X"
date: 2010-06-03
forum: Apple Hardware Users
---

### Post by EvCrock on 2010-06-03
I just downloaded Ubuntu, and it seems pretty cool, but I have no idea of how to go back to Mac OS X.  Getting sort of worried that I lost everything on my hard drive, and I hope that's not the case.

All I did was download Ubuntu to my macbook via the CD method like it says on the website, and now when I start the computer, it automatically goes to Ubuntu.  help!!

---

### Post by Noraphalem on 2010-06-03
Ok what did you exactly?

1. Download the ISO file
2. Burn it onto a CD
3. Install it and use the hole hdd

Is that what you have done?

---

### Post by Guitar John on 2010-06-03
> **EvCrock said:**
> I just downloaded Ubuntu, and it seems pretty cool, but I have no idea of how to go back to Mac OS X.  Getting sort of worried that I lost everything on my hard drive, and I hope that's not the case.

All I did was download Ubuntu to my macbook via the CD method like it says on the website, and now when I start the computer, it automatically goes to Ubuntu.  help!!

Are you running the live cd, or did you click install?  Even if went through the install process, by default Ubuntu is set up as a 50/50 dual-boot unless you tell it to do otherwise.

Tell us a little more about what happened.

---

### Post by EvCrock on 2010-06-03
I ran it using the live cd, then clicked install, than manually partitioned the hard-drive to allocate 10 gigs to Ubuntu, and leaving other 240 gigs untouched.  (250 gigs in all)  I chose the "end" to partition, because that's what some video on youtube told me to do, because it would leave my old information untouched.

let's seee..... I don't know what else, tell me if I need any more info that might be relevant.  And thanks already for the help

---

### Post by Guitar John on 2010-06-03
I'm a little out of my element with Macs, but when you fire up the  computer, do you get any kind of a menu to select which OS you want to use?

---

### Post by Frobber on 2010-06-03
You can Reboot your computer and hold down the *option*key before the start up chime. The display should show what OS are installed. Control tab toggles between the icons then press return.

---

### Post by Noraphalem on 2010-06-03
It should be installed the boot loader GRUB2 now. I think you have to press [ESC] to go into the os menu. I hope this can help you. :P

EDIT:

Ok I see. This seems to be different an Macs. ;-)

---

### Post by tmette on 2010-06-03
> **Frobber said:**
> You can Reboot your computer and hold down the *option*key before the start up chime. The display should show what OS are installed. Control tab toggles between the icons then press return.

Exactly right, hold down the Option key right when you start up, and your Mac OS should be available to boot to, as long as you didn't delete it.  Once you boot into OSX, you can install an application called [rEFit]("http://refit.sourceforge.net/"), which will let you choose what OS to boot to next time you start up your Mac.

---

### Post by Guitar John on 2010-06-03
> **Frobber said:**
> You can Reboot your computer and hold down the *option*key before the start up chime. The display should show what OS are installed. Control tab toggles between the icons then press return.

So if he didn't hold down the option key at startup, would the computer boot directly into the default OS?  I'm not familiar with how Macs work, so I'm learning a few things here as well.

---

### Post by tmette on 2010-06-03
> **Guitar John said:**
> So if he didn't hold down the option key at startup, would the computer boot directly into the default OS?  I'm not familiar with how Macs work, so I'm learning a few things here as well.

Your correct.  GRUB might have made itself the default OS to boot to, so that may be why he can't get back to the OSX partition.  It's happened to me before, but you can always go into OSX and set the default boot OS to back to OSX.

---

### Post by Guitar John on 2010-06-03
Here's hoping that it's that simple.

---

### Post by EvCrock on 2010-06-03
This thread itself is making me like Ubuntu even more.  but there are 180 gigs worth of info (!!!) that I just hope I didn't lose.  I might even make my whole system Ubuntu, but I can't lose all that stuff.

I'll post on here again saying whether or not it worked, thanks team!

---

### Post by EvCrock on 2010-06-03
hmmm, it didn't.  I restarted the computer and held down the option key, and it showed a white screen with an icon of a hard drive with the word "Windows" beneath it.  I never installed windows with bootcamp or anything, it was just a straight OS X before this...

...doesn't look like a good sign

---

### Post by EvCrock on 2010-06-03
anyone got any other ideas?

---

### Post by sha.goyjo on 2010-06-03
> **EvCrock said:**
> anyone got any other ideas?

Can you boot ubuntu and show us the output of
```
$sudo fdisk -l
```
Which will give us a list of all partitions on your drives
That may help.

---

### Post by tmette on 2010-06-03
> **EvCrock said:**
> hmmm, it didn't.  I restarted the computer and held down the option key, and it showed a white screen with an icon of a hard drive with the word "Windows" beneath it.  I never installed windows with bootcamp or anything, it was just a straight OS X before this...

...doesn't look like a good sign

Yes, that isn't a good sign.  I know that the Windows partition is really Ubuntu.  That's how it was back when I had a Mac.  You could also pop in your OSX restore disc, and go to Disk Utility and check out how the partitions are set up.

---

### Post by EvCrock on 2010-06-03
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007ea5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       29186       30402     9765888   83  Linux


O-o that all looks like gibberish to me.  Let me know if I need to do something else, to make it more.... readable?

---

### Post by cbecker78 on 2010-06-03
Until you figure out how to get this fixed (I'm not a Mac, so I can't be of much help there) you can boot ubuntu from the live CD again, and mount your mac partition, or at least see that it is still there.  Then maybe go ahead from the live cd and back all of your data up, then take a deep breath, and get back to fixing the problem...  Good luck!

---

### Post by sha.goyjo on 2010-06-04
> **EvCrock said:**
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Duh. I'm retarded. Parted has a similar command. You can use that. Can we get the output of..

```
$sudo parted -l
```

I'm so sorry. I completely forgot that fdisk didn't support guid by default.

Also, for future reference, in most cases --help will give you a list of supported flags for a given command, such as

```
$parted --help
```

That will give you a big leg up in using the command line.

---

### Post by EvCrock on 2010-06-04
Model: ATA FUJITSU MHY2250B (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size    Type     File system  Flags
 1      240GB  250GB  10.0GB  primary  ext4         boot

---

### Post by linuxopjemac on 2010-06-04
I think you did something very bad....

---

### Post by EvCrock on 2010-06-04
I'm getting that feeling.  :-(  I think I'm gonna call apple tomorrow, see what they say.

---

### Post by towb on 2010-06-04
> **EvCrock said:**
> Number  Start  End    Size    Type     File system  Flags
 1      240GB  250GB  10.0GB  primary  ext4         boot

I don't know parted nor the LiveCD graphical installer, but it looks like you ignored some warning and wiped your drive.

To verify I'd boot from the OS X installation DVD that came with your Mac and, instead of starting an installation, launch Disk Utility from the menu. If that doesn't show your old volume it might still be possible to restore your partition table. I don't know the tools for that, but you could ask the DiskWarrior support.

Good thing you have a backup, right?

> **EvCrock said:**
> I think I'm gonna call apple tomorrow, see what they say.

Don't get upset, but they'll probably (and rightly) say that what you did has nothing to do with OS X and they are neither able nor obliged to help.

---

### Post by cbecker78 on 2010-06-04
Did you try the live CD yet to see if you could mount the osx partition and backup your data?

---

### Post by EvCrock on 2010-06-04
> **towb said:**
> I don't know parted nor the LiveCD graphical installer, but it looks like you ignored some warning and wiped your drive.

To verify I'd boot from the OS X installation DVD that came with your Mac and, instead of starting an installation, launch Disk Utility from the menu. If that doesn't show your old volume it might still be possible to restore your partition table. I don't know the tools for that, but you could ask the DiskWarrior support.

Good thing you have a backup, right?



Don't get upset, but they'll probably (and rightly) say that what you did has nothing to do with OS X and they are neither able nor obliged to help.

I mean, I figured they would say something like that.  There... was no warning?  it just asked me which part of my hard drive I would like to install Ubuntu to, and I followed the directions from the site.  *shrug* If there was one, it was hidden in mumbo jumbo language that I don't know about yet.

I have to wait until I go home, I'm on vacation right now, and am away from my mac start-up disk.

Side question, while we're at it: How do I get Ubuntu to recognize my built-in camera?  Is there a driver I need to install?  I tried looking on the apple website, but alas, no discovery.

---

### Post by towb on 2010-06-04
> **EvCrock said:**
> How do I get Ubuntu to recognize my built-in camera?

Probably [this way]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight").

---

### Post by EvCrock on 2010-06-05
haha, it's looking more and more like I wiped my entire drive, seeing as when following those directions, I can't mount my MacOSX partition.

Now my question is how can we improve the instructions included on the ubuntu web page?  I'm gonna look around for some one to e-mail, because.... to be honest, this is easily the worst technical thing to ever happen to me.  I mean, sure, open source is great, but should it really be at the cost of all of one's information?  With no proper warning given?

I would love to thank everyone on this forum for all of your wonderful help and recommendations.  I've already learned a lot and will most likely be coming back for more questions as I desperately try to learn more.

---

### Post by towb on 2010-06-05
> **EvCrock said:**
> With no proper warning given?

Documentation like the web site doesn't matter, there has to be a message on screen. I'd ask in the non-Apple sections of this forum what might have gone wrong.

> I've already learned a lot and will most likely be coming back for more questions as I desperately try to learn more.

Of course you will, now that you went cold turkey ;)

---

### Post by ckoch on 2010-06-05
First piece of advice when trying anything like this is "Backup!!!" Especially when playing with your main drive.

If you are going to try this again I'd suggest you install rEFIt as somebody mentioned earlier, makes it alot easier to choose between OS X and Ubuntu. Then follow the instructions posted at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

It's not too complicated and is well worth the effort.

---

### Post by sha.goyjo on 2010-06-05
> **linuxopjemac said:**
> I think you did something very bad....

Yeah man. Differential diagnosis:

fdisk says it can't read your GUID (on account of it being fdisk

BUT.....

parted can't see your GUID (on account of something else)

Therefore the computer probably can't see it either.

Yeesh. Scary.

---

### Post by DoubleClicker on 2010-06-07
In the unfortunate event, that you don't have a backup; I would recommend that you turn you computer off and don't touch it until you can boot from a Mac OS X rescue CD ( such as DiskWarrior). Every time the computer writes anything to the hard disk, you could be overwriting files and  your chances of recovery do down and you

---

### Post by towb on 2010-06-07
> **DoubleClicker said:**
> Every time the computer writes anything to the hard disk, you could be overwriting files

He's only touching the last 10GB, and since it's ext4 without a swap partition, those are most likely a lost cause.

---

### Post by sha.goyjo on 2010-06-07
Is it possible that he could go over the drive with scalpel, put the files he scraped on an external, then reformat and rescue at least some of his stuff?

Any thoughts?

---

### Post by towb on 2010-06-07
Scalpel doesn't understand the Mac filesystem. We already mentioned DiskWarrior.

---

### Post by Neds Moar Salt on 2010-06-07
It looks like you deleted your mac partition.  Sorry.  Because of this I might write my guide on installing ubuntu and mac to a one-partition disk.  If you have a backup of your parition table, you can recover your map with only the loss of the last 10GB of your mac partition and your ubuntu installation.

---

### Post by philcolbourn on 2010-06-08
A colleague asked two of us at work to see if I could recover pictures in a hard drive that would not boot Windows anymore.

We worked on it but were unable to mount it.

We then formatted it.

I got the impression that even though he said to format the drive, he really wanted to get the pictures of it first.

So, I threw photorec at it. AMAZING! It recovered 18GB of pictures. He was a happy customer now, except that he had 18GB of photos to sort through.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

I later discovered testdisk.

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

It should be on the ubuntu liveCD, but could also install the package through synaptic.

You might want to consider a USB drive to store any recovered files so you can recover as much as possible.

---

### Post by sha.goyjo on 2010-06-08
philcolbourn brings up an interesting point. If we did a quick partition and then ran a disk recovery suite, would the headers still be intact? 

Maybe someone with more knowledge than me can comment.

---

