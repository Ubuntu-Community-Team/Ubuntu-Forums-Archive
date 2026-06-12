---
title: "&quot;No Root File System&quot;"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by SolarusG on 2007-04-05
Hello. I am trying to install Ubuntu v. 6.10 (Edgy Eft). I have downloaded the LiveCD, and was following the instructions of **[this document.](https://help.ubuntu.com/community/GraphicalInstall)** I have already made partitions: 
1) 9 GB partition for the root "/".
2) 1 GB partition for swap
3) 52 GB partition for /home

Now, when I get to the partition selection step, I use the manual partitioner to select and mount each partition. I fill out the forms, with "/", "swap", and "/home" under the "Mount" column, and the appropriate partitions beneath their column. Upon clicking the forward button, the installer informs me that "No Root File System" has been accounted for. I am unsure of what to do. I have searched the forums, the help files, and Google, and these all provide me with results which don't have much to do with my problem. 

Any advice / assistance would be appreciated. Thank you in advance, and I apologize if I have missed some simple solution. If you would like more information regarding the problem, I will do my best to provide it for you.

---

### Post by Razorback on 2007-04-05
Is there a reason you are manually partitioning the drive?  If you are going to use the whole drive, specify that and the install will do the rest.  That works for me.

---

### Post by SolarusG on 2007-04-05
The drive is a 500 GB external hard drive, and I have about 50 GB of data stored on it already (which could be removed, but this is extremely undesirable, as my computer only has a 60 GB hard drive inside of it). I have had little luck using the options the installer gave in the past, although I have recently reformatted the drive from FAT32 to NTFS. I will try going back into the partition editor to remove the partitions I made and return the main partition to its original size. Hopefully the installer does its job nicely this time...

---

### Post by chalex on 2007-04-05
> **SolarusG said:**
>  I fill out the forms, with "/", "swap", and "/home" under the "Mount" column, and the appropriate partitions beneath their column. Upon clicking the forward button, the installer informs me that "No Root File System" has been accounted for. I

The error message usually means you didn't specify a "/" partition.  Are you sure you did it?  It sounds like you did. 

One possible (inconvenient) workaround is to install Ubuntu 6.06 then upgrade to 6.10.

---

### Post by SolarusG on 2007-04-06
> **chalex said:**
> The error message usually means you didn't specify a "/" partition.  Are you sure you did it?  It sounds like you did. 

I believe I did, or else that form means something completely different than what I took it to be.

> **chalex said:**
> One possible (inconvenient) workaround is to install Ubuntu 6.06 then upgrade to 6.10.

If this would require creating another CD to work off of, this is extremely inconvenient indeed. Thank you for the advice, though, I will try this after I try working through the partitions again.

---

### Post by loveshocked on 2007-04-06
I had the same experience once. 

i tried to manage the partition manually, n I did what it said, making / , swap, n such.
But it didn't work ! "No Root File System"

What i did just format the partition that I want to use as the linux partition (because, in that partition, i installed ubuntu breezy before) , and not setting it up anymore as a ntfs or such. Just an empty partition.
I reboot,n I choosed the second option (use the remaining free space), n somehow it works :-\"

goodluck :biggrin:

---

### Post by SolarusG on 2007-04-06
> **loveshocked said:**
> I had the same experience once. 

i tried to manage the partition manually, n I did what it said, making / , swap, n such.
But it didn't work ! "No Root File System"

What i did just format the partition that I want to use as the linux partition (because, in that partition, i installed ubuntu breezy before) , and not setting it up anymore as a ntfs or such. Just an empty partition.
I reboot,n I choosed the second option (use the remaining free space), n somehow it works :-\"

goodluck :biggrin:


Well, I will try that when I go into the partition editor. Thank you for your advice.

---

### Post by thefoolisme on 2007-04-06
I had the same problem when manually partitioning and trying to set up a home partition.  I bet you'll find if you just choose the 2nd option, use remaining free space, it will work, because it did on mine.  However, I wanted a home partition, and I wanted a FAT32 partition to share docs with XP, and I wanted to be able to mount the XP drive to get stuff off of it if I needed to.  So after I got it working using the "2nd install option" I went back and reinstalled it my way.  

I used the gparted manual installation, and deleted all the partitions except the XP one.  I created the various partitions in gparted listed below, and mounted the XP drive too.

Here's how I broke up my 80GB laptop HDD:

/windows 39gb Part1 IDE/ATA1 (primary) [hda1]
/boot 80mb ext3
/ 8gb Partition xfs
/home 12gb Partition xfs
swap 1gb Partition linux-swap
/documents 15gb Partition (this is the FAT32 partition so I can share documents)

Having the little boot partition made all the difference.  I've since installed other Ubuntu distributions on a different PC hard drive, using the manual partition and the boot partition, and haven't had a single problem.

---

### Post by SolarusG on 2007-04-06
I will try that next, then. 

As an update: 

I first deleted all of the partitions I made and tried to let the installer use the free space. Upon doing this, I got to the install menu, and began installation. The installer tried to create a "ext3" partition, and could not create the partition when it got to 15%. It shut down. I tried this twice.

So I tried to use the manual partitioning again, same as above, except this time I created a "ext3" partition for the root to use, so the installer didn't have to do it. It would not let me continue without using the reformat option on the "/" mount, and locked up again when it tried to reformat the "ext3" partition. I did this twice as well. 

I am currently using the live CD, so I will try the next tip now.


edit:

This is the error message I receive when it tells me it could not create the "ext3" partition:

"The ext3 file system creation in partition #5 of SCSI1 (0,0,0) (sda) failed."

---

### Post by thefoolisme on 2007-04-06
I just went back and read your original post.  Did you make the partitions with gparted, or something else like Partition Magic in Windows?  Just asking because I made my original ones with partition magic and then booted into ubuntu, but gparted wasn't happy until it could delete those partitions and make it's own.

---

### Post by SolarusG on 2007-04-06
I used Gparted.

However, I finally got the installation to work (and am now installing the 164 updates).I got rid of any partitions I made (aside from the one with data already on it, and I shrunk that one) and made a 70GB unallocated space, and told the installer to use that. This time, it went through the whole process nicely and installed Ubuntu. 

So, thanks for all the help, I'll be sure to come back here if I have any more problems or questions.

---

