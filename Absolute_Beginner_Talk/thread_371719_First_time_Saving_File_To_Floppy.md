---
title: "First time Saving File To Floppy"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-27
Greetings to you!

I am needing to save a GRUB file to a floppy disk to do an emergency boot up when I need it.
I need to "compress" the GRUB file because it is near the same size as the floppy disk (1.4 MB) or a tad bit larger.

1. How do I compress the file? What program do I use?

2. How do I save the file from my HDD to the floppy? Do I use Nautilus?

3. Is there some program in Dapper 6.06 that will allow me to format the floppy disk in a:\ drive?

Thanking you in advance for all the help. :) 
KH

---

### Post by Tomosaur on 2007-02-27
Just pop in your floppy :P

Depending on your configuration, the floppy may be automatically mounted. If it isn't, click Places, then Computer, then right click your floppy drive and select Mount or Format. After it's mounted, you should be able to explore it and copy files to it etc. If your click Format, the formatting program will pop up.

To compress a file, just right click it and select 'Create archive'. Choose a format, then select ok.

---

### Post by Maestro23 on 2007-02-27
Are you trying to do this?

Grub Floppy: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

---

### Post by kittyhawk63 on 2007-02-27
> **Tomosaur said:**
> Just pop in your floppy :P

Depending on your configuration, the floppy may be automatically mounted. If it isn't, click Places, then Computer, then right click your floppy drive and select Mount or Format. After it's mounted, you should be able to explore it and copy files to it etc. If your click Format, the formatting program will pop up.

To compress a file, just right click it and select 'Create archive'. Choose a format, then select ok.

Thanks Tomosaur. Gud day to ya! :)

---

### Post by ljpm on 2007-02-27
> **kittyhawk63 said:**
> Greetings to you!

I am needing to save a GRUB file to a floppy disk to do an emergency boot up when I need it.
I need to "compress" the GRUB file because it is near the same size as the floppy disk (1.4 MB) or a tad bit larger.

1. How do I compress the file? What program do I use?

2. How do I save the file from my HDD to the floppy? Do I use Nautilus?

3. Is there some program in Dapper 6.06 that will allow me to format the floppy disk in a:\ drive?

Thanking you in advance for all the help. :) 
KH

I don't know if you can use the floppy to boot if you have compressed the files on it. Some one with more experience want to verify that for me.

---

### Post by RedSquirrel on 2007-02-27
> **kittyhawk63 said:**
> Greetings to you!

I am needing to save a GRUB file to a floppy disk to do an emergency boot up when I need it.
I need to "compress" the GRUB file because it is near the same size as the floppy disk (1.4 MB) or a tad bit larger.

1. How do I compress the file? What program do I use?

open up a terminal and type:

```
tar cjf filename.tar.bz2 files
```*filename* can be whatever you want, but you have to specify the ".tar.bz2" suffix.

*files* is the list of files you want to go into the archive (the file with extension .tar.bz2)

> 
2. How do I save the file from my HDD to the floppy? Do I use Nautilus?
Put a floppy in the drive. Open Nautilus. Right-click on the icon for your floppy drive. There should be an option to "Mount Volume" or something similar.

Once the floppy is mounted, you can copy files to it just like you would with a folder (directory).

> 
3. Is there some program in Dapper 6.06 that will allow me to format the floppy disk in a:\ drive?
Once the floppy is mounted, you can right click on the icon and there should be an option to format it.

---

### Post by kittyhawk63 on 2007-02-27
> **Maestro23 said:**
> Are you trying to do this?

Grub Floppy: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

Gud day to ya, Maestro23.

I've downloaded Super Grub for a floppy boot up just in case I ever need it. Tomosaur has answered my questions previous to your reply.

Thanks for the inquiry.
KH

---

### Post by kittyhawk63 on 2007-02-27
> **RedSquirrel said:**
> open up a terminal and type:

```
tar cjf filename.tar.bz2 files
```*filename* can be whatever you want, but you have to specify the ".tar.bz2" suffix.

*files* is the list of files you want to go into the archive (the file with extension .tar.bz2)

Put a floppy in the drive. Open Nautilus. Right-click on the icon for your floppy drive. There should be an option to "Mount Volume" or something similar.

Once the floppy is mounted, you can copy files to it just like you would with a folder (directory).

Once the floppy is mounted, you can right click on the icon and there should be an option to format it.

Thanks RedSquirrel!

---

### Post by kittyhawk63 on 2007-02-27
> **Maestro23 said:**
> Are you trying to do this?

Grub Floppy: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

Maestro23,
This is the same file that I had downloaded off the Internet from another web page. I like the instructions better on the one you gave me. I still am not clear about this line: ***Put your sgd_0.9575_english_floppy.img.bz2 file in your home/username directory if it isn't there already.***
Does that mean open terminal and place the file name at the end of the "~$"?

Thanks for the assist.
KH

---

### Post by Maestro23 on 2007-02-27
> **kittyhawk63 said:**
> Maestro23,
This is the same file that I had downloaded off the Internet from another web page. I like the instructions better on the one you gave me. I still am not clear about this line: ***Put your sgd_0.9575_english_floppy.img.bz2 file in your home/username directory if it isn't there already.***
Does that mean open terminal and place the file name at the end of the "~$"?

Thanks for the assist.
KH

I figured this what you were trying to do when I read the post. Should have just stated "Hey, I got super grub and I'm trying to put it on floppy." lol

Yes, that file needs to go in your /home/username directory.  In terminal get to the directory that you downloaded the file to.  Then:

> cp sgd_0.9575_english_floppy.img.bz2 /home/username

Just follow the directions from the page, they are pretty straight forward.

---

### Post by RedSquirrel on 2007-02-27
> **kittyhawk63 said:**
> Thanks RedSquirrel!

My pleasure. :)

By the way, in addition to bzip files (.bz2 suffix), you will often see gzip files (.gz suffix). bzip is usually a better compression scheme to use because it makes the file even smaller than compression using gzip.

And just to add a note to what Tomosaur wrote:

> **Tomosaur said:**
> Just pop in your floppy :P

Depending on your configuration, the floppy may be automatically mounted. 

the floppy will not be automatically mounted if you're using a standard floppy drive. If you're using a USB floppy drive it might be automatically mounted. With the standard floppy drive, when you insert a floppy, the computer doesn't have any way to recognize that you've done that (unlike inserting a CD-ROM, for example).

---

### Post by kittyhawk63 on 2007-02-27
> **RedSquirrel said:**
> My pleasure. :)
By the way, in addition to bzip files (.bz2 suffix), you will often see gzip files (.gz suffix). bzip is usually a better compression scheme to use because it makes the file even smaller than compression using gzip.
And just to add a note to what Tomosaur wrote:
the floppy will not be automatically mounted if you're using a standard floppy drive. If you're using a USB floppy drive it might be automatically mounted. With the standard floppy drive, when you insert a floppy, the computer doesn't have any way to recognize that you've done that (unlike inserting a CD-ROM, for example).

Yes, I noticed that. I figured out to first "unmount" the drive. I then formatted it. That worked. Then I "remounted" the drive. Now Nautilus recognizes it. Thanks for the good input.
KH

---

