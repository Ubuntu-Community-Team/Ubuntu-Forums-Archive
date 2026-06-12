---
title: "recognizing 200 gig hard drive as only 30 gigs"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by akba0012 on 2007-11-03
Hello,

I have a hard drive, ( Model Number ST3200822A) Seagate Barracuda 200 gigs. QTparted only recognizes it as only 30 gigs...  I'm not sure what to do at this point. This is the hard drive that Ubuntu is installed on. 

I've had this hard drive for a few years. I believe I originally formatted for 30 gigs for the operating system and applications, and then 170 gigs for storage... 

Can someone help recover this 170 gigs?

Thanks!

---

### Post by overdrank on 2007-11-03
> **akba0012 said:**
> Hello,

I have a hard drive, ( Model Number ST3200822A) Seagate Barracuda 200 gigs. QTparted only recognizes it as only 30 gigs...  I'm not sure what to do at this point. This is the hard drive that Ubuntu is installed on. 

I've had this hard drive for a few years. I believe I originally formatted for 30 gigs for the operating system and applications, and then 170 gigs for storage... 

Can someone help recover this 170 gigs?

Thanks!

Hi have you tried the live cd with gparted? You can find gparted under system, administration, gparted, to see if it will help.

---

### Post by akba0012 on 2007-11-03
> **overdrank said:**
> Hi have you tried the live cd with gparted? You can find gparted under system, administration, gparted, to see if it will help.

gparted is not finding it either. I'm guessing that it is formated in NTSF or other windows variety. Can these pick up the NTSF formatted partitions?

Whats the best way to access this unseen partition? Maybe I can mount it somehow

---

### Post by overdrank on 2007-11-03
> **akba0012 said:**
> gparted is not finding it either. I'm guessing that it is formated in NTSF or other windows variety. Can these pick up the NTSF formatted partitions?

Whats the best way to access this unseen partition? Maybe I can mount it somehow

That is strange, yes gparted can see the ntfs and fat file systems. That one has got me :confused:
Gparted only shows the whole drive as 30gb and no other partitions or unpartitioned space?
Would you mind trying to post a screen shot of gparted on that dive?

---

### Post by insane_alien on 2007-11-03
tried fdisk? command line and old school but it often shows up stuff that gparted has went 'Nothings there' on like old depreciated partition types.

---

### Post by akba0012 on 2007-11-03
> **overdrank said:**
> That is strange, yes gparted can see the ntfs and fat file systems. That one has got me :confused:
Gparted only shows the whole drive as 30gb and no other partitions or unpartitioned space?
Would you mind trying to post a screen shot of gparted on that dive?

sure here you go... 

[[IMG]http://img469.imageshack.us/img469/8775/gpartedpp7.th.png[/IMG]](http://img469.imageshack.us/my.php?image=gpartedpp7.png)

---

### Post by linuxlizard on 2007-11-03
What do you mean by it's only recognizing it as 30 gigs? Does gparted show the rest of the drive as unformatted or just not there at all?

---

### Post by akba0012 on 2007-11-03
> **insane_alien said:**
> tried fdisk? command line and old school but it often shows up stuff that gparted has went 'Nothings there' on like old depreciated partition types.

i'm not very good with fdisk... i know the hard drive is hda1... 
i tried 
```
fahim@Central:~$ fdisk /dev/hda1

Unable to open /dev/hda1

```
not sure extacly what to do with fdisk...

---

### Post by akba0012 on 2007-11-03
> **linuxlizard said:**
> What do you mean by it's only recognizing it as 30 gigs? Does gparted show the rest of the drive as unformatted or just not there at all?

its showing up as not there at all... i posted a screenshot.... yea i totally forgot that this hard drive was 200 gigs until i was doing some cleaning inside the computer and looked at the hard drive. Sure enough it says 200 Gigs right on there, wrote down the model number and confirmed it on line that it should be 200 gigs. Then I remembered the partition scheme I used, 30gigs for the OS/Apps, and the rest for storage... but it shouldn't just disappear like that.

---

### Post by overdrank on 2007-11-03
> **akba0012 said:**
> its showing up as not there at all... i posted a screenshot.... yea i totally forgot that this hard drive was 200 gigs until i was doing some cleaning inside the computer and looked at the hard drive. Sure enough it says 200 Gigs right on there, wrote down the model number and confirmed it on line that it should be 200 gigs. Then I remembered the partition scheme I used, 30gigs for the OS/Apps, and the rest for storage... but it shouldn't just disappear like that.

Hi and please post the output of this command in the terminal
```
sudo fdisk -l

```

---

### Post by akba0012 on 2007-11-03
Here you go

```
fahim@Central:~$ sudo fdisk -l
Password:

Disk /dev/hda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3937    31623921   83  Linux
/dev/hda2            3938        4111     1397655    5  Extended
/dev/hda5            3938        4111     1397623+  82  Linux swap / Solaris

```

---

### Post by overdrank on 2007-11-03
> **akba0012 said:**
> Here you go

```
fahim@Central:~$ sudo fdisk -l
Password:

Disk /dev/hda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3937    31623921   83  Linux
/dev/hda2            3938        4111     1397655    5  Extended
/dev/hda5            3938        4111     1397623+  82  Linux swap / Solaris

```

Ok the only thing I have left in my bag of tricks is that some drives allow you to use jumpers to regulate the size of the drive. You may look at the manufactures website and see if that applies. :-k

---

### Post by mdpalow on 2007-11-03
Just a thought, but in the top right corner of 'gparted' where it says /dev/hda1 - if you click there, does it show you anything else?

Also, I've noticed during install, the partition part's first option is to use a percentage of a currently existing partition. That's why I always do a MANUAL partition when installing. I can delete everything and create new partitions based on the full size of the drive.

You could put the live cd back in and boot from it and simulate a new installation and when you get to the partition part click on MANUAL and see what it shows you. Don't go too far past that screen or you might end up formatting/partitioning again when you didn't want to.

gparted will see NTFS and FAT32, so that's not an issue.

let us know what you find...

---

