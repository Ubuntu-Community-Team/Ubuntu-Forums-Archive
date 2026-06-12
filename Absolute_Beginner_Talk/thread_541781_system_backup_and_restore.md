---
title: "system backup and restore"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by occhiso on 2007-09-03
Hi,

I am new to linux, and have just installed feisty fawn on my laptop. 
I have had so many troubles getting it to work the way I want so far! (ati graphics card, network, vpn, etc.)

After alot of time with my local helpdesk, i eventually got everything working. This involved alot of new drivers and configuration changes. I tried doing this myself, but nothing would work, I couldnt even boot off the live cd without drivers and couldnt get them without network, etc.

I have read many threads on backing up and restoring ubuntu, but I am still unsure.
In [this]("http://ubuntuforums.org/showthread.php?t=81311") guide, it says I dont need software, and to restore, all i need is a few commands.

With windows, I format my drive, load windows & drivers, change some settings and make an image of it, then this gets put on a NAS or DVD and next time i need to format, I boot from a true image boot disk and reload my backup... easy!

With ubuntu, how do I get a linux command promt from a fresh format i order to restore (using the above guide), lets say new hard drive for example, no partitions, no OS?

Also, I know of some other apps that are supposable good for this sort of thing, they are "mindi" and "sbackup", would these be able to duplicate my windows backup method, or at least provide the same functionality with ease? Is this a better option than the guide above?

These questions might be basic, but im very new to linux.
After this long post, I only really have the three questions mentioned above, but I thought id explain my background, and why I need something simple.

Hope someone can (please) help me. :)

Thanks,
occhiso

---

### Post by Kobalt on 2007-09-03
My first advice would be to [make a separate /home partition]("http://www.psychocats.net/ubuntu/separatehome").
Then, if needed, use [Partimage]("http://www.psychocats.net/ubuntu/partimage") or [sBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite").

---

### Post by occhiso on 2007-09-03
Hi Kobalt,

Thanks for ur prompt reply.

Just curious, what advantage does making a seperate home partition have?
Wouldnt this mean there would be more to back up? keeping in mind, I had to install additional
drivers and things to get it working, I would need to back up more than just my home wouldnt I?

This backup is not just personal data, its to have an easy way to install, the ubuntu live cd will not work on my laptop without fglrx, etc.
The way I have ubuntu setup now, is the way I want to be able to restore it later.

sorry for the contradiction, just trying to learn,

thanks,
occhiso

---

### Post by Kobalt on 2007-09-03
Having a separate /home partition is very handy : you keep your personal files and application settings safe from a system crash or a distribution change/upgrade.
In your case, what you do need is more Partimage I believe, but I would also use a separate /home partition. You would have something like this : 
partition 1 : /
partition 2 : swap
partition 3 : /home
You would use Partimage to make a entire image (that would fit on a 4,7Gb DVD) of your first partition with your install as you like it, and your /home would be protected as well...
The second advantage of the separate /home partition here is to have everything you need to backup for a system image on your first partition.

PS: I use this partition scheme on my personal laptop.

---

### Post by edonia on 2007-09-03
With partimage you can make a image from the partition, similar to the partimge program from powerquest.

Partimage will be just a bootable CD, so you can restore a blank disk.

Making a separate partition for your /home directory, is useful. this partition you can backup with any tool, like tar or rsync or any thing else, because here are no special files, which needed to be saved as an image.

So you would have a image from your system with drivers, settings...
And another backup with your data, which will change mor often and needed to backed up all the time.

---

### Post by occhiso on 2007-09-04
Ok,

That sounds good, im looking into partimage now.

Just a couple of questions:
1. So I make an image of my system partition, using partimage, and put that on a dvd, is that just an image file, or is that dvd bootable, and have like a wizard to restore my system?
Basically, if I dont have anything on the harddisk, is it only the one dvd that i would need?
also, if this is the case, does it require X, as my laptop wont display any GUI without drivers, etc.
**edit:*** I think ill use SystemRescueCD as advised by that tutorial and my external HDD, but im still interested, is the above still possible to create, like the recovery disks bundled with laptops?*

2. How would I go about moving my home directory to a seperate parition now? I know how to use GParted to make the partition, but how do i redirect ubuntu to look there instead?

Thanks very much for your help, both of you,
much appreciated :)

occhiso

---

### Post by hyper_ch on 2007-09-04
there's a command line program called "dd" ... it can also make a complete image of your partition:

```

sudo dd if=/dev/hda1/ of=/home/USER/backup.dd

```

sudo --> dd must be run as root
dd --> the actual program
if --> "input file"
/dev/hda1 --> the partition you want to read from
of --> "output file"
/home/USER/backup.dd --> where you want to save to (must be on a different partition)

If you want to know more about dd just enter this:
```

man dd

```

---

### Post by logos34 on 2007-09-04
> **occhiso said:**
> Ok,

That sounds good, im looking into partimage now.

Just a couple of questions:
1. So I make an image of my system partition, using partimage, and put that on a dvd, is that just an image file, or is that dvd bootable, and have like a wizard to restore my system?
Basically, if I dont have anything on the harddisk, is it only the one dvd that i would need?
also, if this is the case, does it require X, as my laptop wont display any GUI without drivers, etc.
**edit:*** I think ill use SystemRescueCD as advised by that tutorial and my external HDD, but im still interested, is the above still possible to create, like the recovery disks bundled with laptops?*

2. How would I go about moving my home directory to a seperate parition now? I know how to use GParted to make the partition, but how do i redirect ubuntu to look there instead?

Thanks very much for your help, both of you,
much appreciated :)

occhiso

tar, dd, sbackup and partimage--a combination of these is probably your best strategy.  

1. I'd try Parted Magic livecd or liveusb.  It has a menu option to run on an 'XVesa' driver--might just work for you.  The livecd even runs completely from the ram (kicks out the cd after it loads), so you could easily do a restore from dvd.  If Partimage, you'll be creating an image (possibly gzip compressed), but you'll burn it as data--it won't be a bootable iso or anything.  To restore you'll have to use partimage program again, just the reverse.

2. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bean77 on 2007-09-04
I am using sbackup for the first time.  How long is it supposed to take?  And if I need to restore from the command line, what do I put in?

---

### Post by occhiso on 2007-09-07
Hi everyone,

A while ago, whilst trying to get ubuntu working on my laptop, I downloaded SystemRescueCD, and while X doesnt work, it still has some helpful software, like partimage. 
Following [this]("http://www.psychocats.net/ubuntu/partimage") link from Kobalt, I used systemRescueCD to start partimage, made a backup of my whole linux partition, and then burned the latest version of systemRescueCD along with my backup image onto a DVD. To burn my backup image on the systemRescueCD I followed [this tutorial]("http://www.sysresccd.org/Sysresccd-manual-en_How_to_burn_a_DVD_with_SystemRescue_and_4_GB_more_files").
So now if i want to restore, I can simply boot of my DVD version of systemRescueCD and recover my backup image straight from the disc!

In the future, one day when I get time, the systemRescueCD site has tutorials on how to make custom versions of the distro, to do automatic recoveries, etc. using scripts, which would be nice for this sort of thing.

Also, I havent separated my home directory into its own partition yet, but I will, it sounds like it is a very useful thing to do, and when I do, ill repeat this procedure with my new version. Bit busy at the moment to do anymore, as fun as it is :) but with the release of gutsy right around the corner, im going to have to make a new backup soon anyway.

Thanks for all this advice!
You've all been very helpful.

BTW, any comments/suggestions/information on this method of backing up is appreciated.
Seems to be a winner for me.

cheers,
occhiso

---

### Post by edonia on 2007-09-07
> **occhiso said:**
> Hi everyone,

A while ago, whilst trying to get ubuntu working on my laptop, I downloaded SystemRescueCD, and while X doesnt work, it still has some helpful software, like partimage. 
Following [this]("http://www.psychocats.net/ubuntu/partimage") link from Kobalt, I used systemRescueCD to start partimage, made a backup of my whole linux partition, and then burned the latest version of systemRescueCD along with my backup image onto a DVD. To burn my backup image on the systemRescueCD I followed [this tutorial]("http://www.sysresccd.org/Sysresccd-manual-en_How_to_burn_a_DVD_with_SystemRescue_and_4_GB_more_files").
So now if i want to restore, I can simply boot of my DVD version of systemRescueCD and recover my backup image straight from the disc!

Thats, what I told ;-)

And if you use partimage only, you need only a 2,8 MB boot iso, so can be emulated like any bootable CD

> **occhiso said:**
>  In the future, one day when I get time, the systemRescueCD site has tutorials on how to make custom versions of the distro, to do automatic recoveries, etc. using scripts, which would be nice for this sort of thing.

Also, I havent separated my home directory into its own partition yet, but I will, it sounds like it is a very useful thing to do, and when I do, ill repeat this procedure with my new version. Bit busy at the moment to do anymore, as fun as it is :) but with the release of gutsy right around the corner, im going to have to make a new backup soon anyway.


Very easy:
Create the patition with gparted and set the mount point to /home

---

### Post by occhiso on 2007-09-07
Yep!
Exactly, like I said, thanks to everyone, you all helped me. :)

much appreciated, and I will seperate my home as soon as I can,
Thanks again!

---

### Post by moldy on 2008-02-25
hi there

just trying to follow this post and back up my linux partition with partimage.

i've downloaded the sysreccd and burned it to cd. as i understand it, the next step is the generate an image of the partition.

here's where i'm confused. where must i create the image to? can it be to my windows partition (which has heaps of space), or must i create another separate partition just for it (which i don't really fancy doing)? or even better, can it be created directly to dvd?

any help you could give me would be appreciated.

cheers

moldy.

---

