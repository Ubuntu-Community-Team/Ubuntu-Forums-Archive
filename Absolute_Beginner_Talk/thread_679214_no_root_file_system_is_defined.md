---
title: "no root file system is defined"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Binary is Better on 2008-01-26
OK I've read the other threads titled the same, but would like to start from scratch.  Here's where I'm at.  I have begun the process of installing Ubuntu, with Windows XP on the system already.  I am in the "prepare partitions" portion of install, and it looks as such:

/dev/sda
  /dev/sda1       fat16      /media/sda1   49MB         33MB
  /dev/sda2       ntfs        /media/sda2   75006MB   18200MB
  free space                                            81199MB
  /dev/sda3       fat32      /media/sda3   3742MB     3300MB

I've tried a few times and backed up.  I have run into the same issues as others, about "no root file system is defined", and was not able to fix things by adding the "/" partition and "swap" partition.  It told me that something was not expected so I backed up to start all over with help.

Anything but Windows is totally foreign to me, but I must learn Ubuntu.

Somebody who wants to adopt an Ubuntu NOOB, please help out.

Thanks

---

### Post by logos34 on 2008-01-26
You've reached the limit of four primary partitions.

Select manual partitioning and create an **extended** partition out of the free space.  Then put root (ext3, mounting at '/') and swap ('/swap') inside as **logical **partitions.

---

### Post by Binary is Better on 2008-01-26
Ok, and since I have pleanty of space on this partition, is there a particular size I should allott for each?

And should I select "primary" or "logical" for each? Or is that what you meant by extended?

---

### Post by Binary is Better on 2008-01-26
OK perhaps I misread.  How do I create an "extended" partition?  I see options of "primary" and "logical".

---

### Post by logos34 on 2008-01-26
> **Binary is Better said:**
> OK perhaps I misread.  How do I create an "extended" partition?  I see options of "primary" and "logical".

then choose logical...maybe it automatically wraps it in an extended, I forget

---

### Post by Binary is Better on 2008-01-26
I should have looked at this as well.  For this "extended" partition, what do I select in the "Use as:" option?

---

### Post by drowner on 2008-01-26
I'm not exactly sure what you mean, but we can work through it.

I'm going to guess that little Fat16 partition is a 'recovery' partition. That will be primary partition number one.

The NTFS windows partition will be primary number 2.

Then, I would put "/" (the root filesystem) on another primary partition. Thats 3.

The fourth primary partition should be an extended partition - this can contain numerous 'logical' partitions. On these you can put swap, a shared partition, and a seperate home if you like.

What is on that FAT32 partition? what do you intend to do with it?

Also, leave your EMPTY space *within* the extended partition - or you may find it difficult to get to it later. Or, alternatively, format it as something.

---

### Post by Binary is Better on 2008-01-26
> **drowner said:**
> What is on that FAT32 partition? what do you intend to do with it?

The fat16, fat32 and ntfs were all 3 on there before I started this.  I have no idea what they are, and have been so inclined to leave them as they are.  I am not ready to abandon Windows yet, so do not want to mess with what is working now. 

The question now is how big the "/" and "swap" files should be, and what "use as:" to label the swap.

---

### Post by drowner on 2008-01-26
/ can be as big as you like it! If you are NOT going to have a seperate home, make it a bit bigger, so you have space to save files. If you ARE going to have a seperate /home, then you could get away with 6-10gig. You got plenty of space, so its up to you

the swap partition should normally be 2x the ram of your computer - but if you have 2 gig of ram, then making a 4gig swap is probably unnecessary. But if you have 512mb of ram, 1gig of ram is a bit more important.

What options does 'Use as' give you?

---

### Post by drowner on 2008-01-26
Oh, and if you are going to keep 3 primary partitions on your drive, you will need to put ALL your partitions as LOGICAL partitions within an EXTENDED partition, because you can only have 4 primary partitions.

---

### Post by Binary is Better on 2008-01-26
Not sure what you mean about having a separate /home.  I fully intend that the entire 81G available fo free space will be set aside for Ubuntu somehow or another.  I  have 1G of ram, so should I make the swap 1G or 2G?

The Use as options are as follows:

ext3
ext2
reiserfs
jfs
xfs
fat16
fat32
swap
efi
dont_use

---

### Post by drowner on 2008-01-26
Ok, Cool!

Seperate /home means having your /home partition on a seperate partition. You can do this if you want. If you don't do it now, you can change it after, if you so choose.

So if you want the 81gig available to Ubuntu, thats awesome.

Next question is do you want a partition available  to windows?

Some people put a partition for data, like music or documents, that can be easily read by both windows and linux.

---

### Post by Binary is Better on 2008-01-26
a partition available to both windows and ubuntu might be convenient, but as far as for windows itself, I'm assuming that the 75G partition with 18G used leaves enough for Windows.  

I think I'll forgo the /home for now then, since I do not totally understand it.

---

### Post by drowner on 2008-01-26
Cool!

What I was asking (I know windows has MORE than enough space!) is that Windows has difficulty reading Linux filesystems (ext3 by default). Infact, it CANT read them, unless you install spcial drivers in windows.

As a result, some people like to keep information that they would want to share between Windows and Ubuntu (like music, data, etc) on a seperate partition, with can be formatted FAT32, which is totally read/writable to both systems.

I will give you both options anyhow.

First BACK EVERYTHING IMPORTANT UP TO A SEPERATE DRIVE

Without a 'shared' partition:

partition that 81gig free space as a primary 'extended' partition

Within that extended partition, make a logical partition for '/'. You can make it as big as you want. (eg 79 gig). 'Use as' ext3, and make sure it is bootable.

Also within that extended partition, make another logical partition for swap. Make it 2gig, and 'use as' Swap.

(If you want to make a 3rd FAT32 partition, you can do that as well - make another one, and 'Use as' FAT32).

---

### Post by Binary is Better on 2008-01-26
Sorry but I still seem to be stuck.  I understand to partition the 81G as a primary 'extended', but what "use as" should I use for it?  Should I use the defaulted "ext3"?  Sorry but like I said at the beginning, I'm totally lost.

---

### Post by drowner on 2008-01-26
Change it from 'primary' to 'Extended'

Do you still get the 'use as' options?

Sorry, not used gparted for ages.

---

### Post by Binary is Better on 2008-01-26
With either primary or logical it still gives "use as" options.  there is no "extended" option.

---

### Post by drowner on 2008-01-26
could you take a screen shot? I have a feeling something is already formatted there....

---

### Post by Binary is Better on 2008-01-26
ok I have a screen shot on my flash drive, but not sure how to post it in here

---

### Post by drowner on 2008-01-26
Cool, you've saved it to a flash drive. You will need to upload it to an image server like photobucket... do you know how to do that? Do you know where the image is saved, in linux talk?

---

### Post by Binary is Better on 2008-01-26
Im pathetic.  I can't find the file on the thumbdrive, perhaps it's not recognizing the format from ubuntu

---

### Post by Binary is Better on 2008-01-26
it's saved as a .png

---

### Post by drowner on 2008-01-26
heh, i'm not sure i can help you with that!

---

### Post by Binary is Better on 2008-01-26
I'm at a loss

---

### Post by Binary is Better on 2008-01-26
This is what it looks like now.  Can anyone help me at all please?

/dev/sda
/dev/sda1 fat16 /media/sda1 49MB 33MB
/dev/sda2 ntfs /media/sda2 75006MB 18200MB
/dev/sda5 swap                                    18200MB
/dev/ext3  /                                           69997MB
free space                                             9204MB
/dev/sda3 fat32 /media/sda3 3742MB 3300MB

---

### Post by drowner on 2008-01-26
> **Binary is Better said:**
> This is what it looks like now.  Can anyone help me at all please?

/dev/sda
/dev/sda1 fat16 /media/sda1 49MB 33MB
/dev/sda2 ntfs /media/sda2 75006MB 18200MB
/dev/sda5 swap                                    18200MB
***/dev/ext3  /                                           69997MB***
free space                                             9204MB
/dev/sda3 fat32 /media/sda3 3742MB 3300MB

This is not right. It has to be in the form /dev/sda...... 

Did you copy this out yourself? I think you did - i can't tell if you've made an extended partition or not from this.

How big is your pen drive? 4 gig? Is it plugged in at the moment?

---

### Post by Binary is Better on 2008-01-26
the flash drive is not plugged into the system i'm working on, it's now in the laptop i'm using for posting here.  The swap, ext3, and free space can be reconfigured to free space again.  I do know I need a "/" partition and a "swap" extendion somehow though.

Oh...and the dev/ext3 should have read   
" /dev/sda6    ext3    /    69997MB"

---

### Post by drowner on 2008-01-26
Thats right - you need to get rid of the swap and the 'ext3' partition.

My only concern is that i dont know what '/dev/ext3' means.... it should be something in the format of the other listings.

---

### Post by Binary is Better on 2008-01-26
I entered it incorrectly......

/dev/sda6   ext3  /    69997mb

---

### Post by drowner on 2008-01-26
Beautiful! Its a root partition! (/)

You also have a swap, now, and you've left your windows partitions intact.

it looks like you've done it!

---

### Post by drowner on 2008-01-26
Hang on - is says your swap is 20gig! Is that an error in typing?

---

### Post by bren on 2008-01-26
if you want to understand more about this stuff

2 independent but very good set of web pages

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  (briefer simpler)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) (almost all config options covered)

later will tell about about separate /home etc

bren

---

### Post by Binary is Better on 2008-01-27
LOL, of course I'm not done yet.........

Warning!
File system doesn't have expected sizes for Windows to like it.  Cluster size is 2k (1k expected); number of clusters is 24026 (47959 expected); size of FATs is 94 sectors (188 expected).

Options to "ignore" or "cancel"

---

### Post by dcstar on 2008-01-27
> **Binary is Better said:**
> LOL, of course I'm not done yet.........

Warning!
File system doesn't have expected sizes for Windows to like it.  Cluster size is 2k (1k expected); number of clusters is 24026 (47959 expected); size of FATs is 94 sectors (188 expected).

Options to "ignore" or "cancel"

Get rid of the USB while you are installing.

---

### Post by Binary is Better on 2008-01-27
> **dcstar said:**
> Get rid of the USB while you are installing.

The USB flashdrive was only used for an attempt to get a printscreen.  If you will read above it is not connected to the computer at this time.  The warning above is what I'm concerned with.  Since I have an option to ignore, and since this partition will not be used by Windows, I'm guessing all is ok.  However, I'm hoping to get some confirmation from someone more familiar.

---

### Post by Binary is Better on 2008-01-27
OK, lastnight I took the plunge and installed anyway, which appeared to be fine untill about 51-55%, i don't remember exactly.  Then it locked up saying there was a problem with the hard drive or cd drive or disc.  I had read how others had this problem and tried again, and it was successful so I tried to run the installation again.  When I did this the partition was half the size it was before, but I figured I'd just use the remaining part as a shared partition between Ubuntu and Windows.  But....as the second attempt failed at about the same time, I am now stuck.  Windows will no longer boot either, as my  hard drive does not appear to be an option in the boot menu any longer.  I don't want to have to reformat, but I guess it wouldn't be the end of the world.

Any suggestions now?

---

### Post by orthenstein on 2008-01-29
Really sorry to hear about loss of your Windows partition; hopefully, you can recover your critical files.  While you are getting Windows reinstalled, may I suggest reading the following link:

[[COLOR="Blue"]Linux System Adminstrators' Guide: Partitions[/COLOR]]("http://www.linuxhq.com/guides/SAG/x885.html")

The information is old ( Copyright 1998 ), but I believe that it is fundamentally correct.  I don't believe Linux has changed significantly in how it creates partitions.  In my opinion, this link provides the best conceptual explanation for primary, extended, and logical partitions that I've seen so far on the Web.

To give you a quick answer to what is the difference between the partition types (and hopefully, clear up some of your confusion):
[LIST=1]
[*]A **[COLOR="Red"]primary[/COLOR]** partition is a partition that has a boot sector that is tied to the *Master Boot Record*, and as previously stated, you can only have a maximum of four primary partitions.
[*]An **[COLOR="Red"] extended[/COLOR]** partition **IS** a **[COLOR="Red"]primary[/COLOR]** partition with the main difference being that this **[COLOR="Red"]primary[/COLOR]** partition is sub-partitioned into **[COLOR="Red"]logical[/COLOR]** partitions.
[/LIST]

This past weekend, I built a brand-new system with a 250 GB HDD, and my intention is to dual-boot it with Windows.  As I was starting my Ubuntu installation, I encountered the same questions that you have with primary and logical partitions when I used the Ubuntu Live CD Partitioner.  I've been using Linux for a couple of years now, but I've taken for granted these details since I've been running Linux and Windows on separate HDDs on my other computer; the default partition settings were suitable for my needs, but not any more.  

As I've learned this evening from reading this information and installing Ubuntu, whatever freespace you have after getting Windows reinstalled, you need to make it an **[COLOR="Red"] extended[/COLOR]** partition as was originally suggested by *logos34*.  This will be achieved by selecting *logical partitions* within the Ubuntu Live CD Partitioner for the root "/" and the swap partition.  The "/home" partition that the others were mentioning is just another **[COLOR="Red"]logical[/COLOR]** partitions within the **[COLOR="Red"] extended[/COLOR]** partition.  By selecting these different partitions as logical partitions, the Ubuntu Live CD Partitioner will know that you mean **[COLOR="Red"] extended[/COLOR]** partition.

During my installation, I saw no explicit mention of "*extended*" partition within the Ubuntu Live CD Partitioner. You will know indirectly that an **[COLOR="Red"] extended[/COLOR]** partition is created by the numbers associated with each partition.  Specifically, for a SATA drive, the primary partitions are designated by sda1, sda2, sda3, sda4 since only four primary partitions are allowed.  The logical partitions will be designated by the number five or greater (e.g., sda5).  The only time I saw "extended" was after the installation was finished, and via the command line, I typed **[FONT="Courier New"]fdisk -l /dev/sda[/FONT]** to see what the partition tables looked like.  As an example, this is what my HDD looks like according to the partition table:

[FONT="Fixedsys"]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       30401   223713157+   5  Extended
/dev/sda5            2551        4982    19535008+  83  Linux
/dev/sda6            4983        5955     7815591   82  Linux swap / Solaris
/dev/sda7            5956       18243    98703328+  83  Linux
/dev/sda8           18244       24322    48829536   83  Linux
/dev/sda9           24323       30401    48829536   83  Linux
[/FONT]

To summarize:  
[LIST]
[*]sda1 is my Windows partition.
[*]sda2 is my overall "extended" Linux partition.
[*]sda5 is the logical partition containing "/".
[*]sda6 is my logical swap partition
[*]sda7 is my logical "/home" partition
[*]sda8-9 are just extra logical partitions just to break up my HDD even more.
[/LIST]

In reading this post, I hope I didn't insult your intelligence by belaboring certain points.  It was my intention to provide a cohesive answer instead of a mish-mash answer that needs to be deduced from various posts.  Hopefully, a clearer picture of what's going on is forming.

---

