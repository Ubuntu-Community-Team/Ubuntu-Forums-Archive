---
title: "Recovering from NTFS disk with TestDisk"
date: 2013-02-19
forum: Any Other OS
---

### Post by bcm37 on 2013-02-19
I'm throwing myself upon the mercy of those who may know more about recovering data.

I've been following this tutorial with TestDisk on a 250 GB NTFS disk for a friend of mine.

I get "The harddisk (250 GB / 232 GiB) Seems too small! (< 1317 GB / 1227 GiB)
...
The following partition can't be recovered:
```

  Partition           Start        End    Size in sectors
> HPFS - NTFS    71284 189 15 160335 186 38 1428837000

```(The "S" in "Start" starts over the space between the 4 and the 1; the "E" over the 5 in 160335 and the "S" in "Size" over the 8 in 38)

Below "[ Continue ]" it says "731 GB / 681 GiB"

After I continue It's listed as the second partition (with the files in it when you press "P") and it says:
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
```
 D HPFS - NTFS          0   1  1  6373 254 63  102398247
>D HPFS - NTFS          0  32 33 30401  42 41  488392704
```I want that partition... but I'm stuck at what to do with these errors. I'm not really a disk expert.

I have to say there were some bad sectors on this disk, and a lot of reallocates in SMART, I just want the disk readable to get the files off it. Perhaps I'm using the wrong option and should try the copy feature? I don't think it copied anything when I tried it to another NTFS disk.

It's running off of a live CD with PartedMagic right now. It's a Western Digital WD2500js - so I'm sure it's a 250 GB drive.

(I've also given her a lecture or two on backup. ;) )

---

### Post by fedine on 2013-02-20
Check this:  [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Mark Phelps on 2013-02-20
> **bcm37 said:**
> ...I just want the disk readable to get the files off it...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by varunendra on 2013-02-20
> **bcm37 said:**
> I've been following this tutorial with TestDisk on a 250 GB NTFS disk for a friend of mine.

Since the HDD is physically only 250 GB, you should consider creating its image with testdisk and then working on the image instead - if the data is really important and if you can get 250 GB space somewhere.

The inconsistency in the reported partition size is a common issue with messed up partition table and testdisk can easily fix it, but you must be able to recognize and choose correct partition layout when suggested by testdisk. Any mistake, and the partition table will be further messed up!

On the other hand, if you can make a correct choice (by exactly remembering the correct partition sequence with correct sizes), then getting back your partitions may be just a matter of seconds!

The option is in the default selection path of testdisk, in **"Deeper search" > write**

It will help us a lot if you can post the link of the guide you are following, along with the screenshots or screen outputs of testdisk with your own attempts.

------------
[B]PS:

@ Mark,[/B]

I have a copy of GetDataBack, and have used it quite extensively. But now I prefer to use testdisk (especially on windows partitions) except in very rare cases where partitions can't be corrected and I need to recover files with their original filenames.

While it is more intuitive in 'some cases' and has other advantages like offering a list of detected files to choose from, or retaining original filenames with directory tree, I find it too slow and less capable than testdisk / photorec.

For example, I have more than once recovered more files (100% in each case) with photorec than with GDB (about 40 & 60% in the two cases I remember).

In the most recent case, I scanned a 320 GB HDD (connected via USB) in about 10 parts with GDB because it was too slow and the USB adapter was disconnecting every few hours probably due to heat up. At the end, it only recovered about 40% files that were lost in a crash.

Without much hope I tried PhotoRec, and in about half an hour, it recovered all the files from the HDD.

I must mention that the partitions were somehow intact, only files were missing (not deleted), and I chose to scan only 'Free' space. Don't remember if I chose the same thing in GDB, I guess I did. Regardless, it was nothing less than a miracle for me.

---

### Post by bcm37 on 2013-02-20
> **fedine said:**
> Check this:  [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I am using this guide.

---

### Post by varunendra on 2013-02-20
So did you do a deeper search? Can you post the screen output or screenshot 'after' deeper search?

---

### Post by bcm37 on 2013-02-20
> **varunendra said:**
> Since the HDD is physically only 250 GB, you should consider creating its image with testdisk and then working on the image instead - if the data is really important and if you can get 250 GB space somewhere.

The inconsistency in the reported partition size is a common issue with messed up partition table and testdisk can easily fix it, but you must be able to recognize and choose correct partition layout when suggested by testdisk. Any mistake, and the partition table will be further messed up!

On the other hand, if you can make a correct choice (by exactly remembering the correct partition sequence with correct sizes), then getting back your partitions may be just a matter of seconds!

The option is in the default selection path of testdisk, in **"Deeper search" > write**

It will help us a lot if you can post the link of the guide you are following, along with the screenshots or screen outputs of testdisk with your own attempts.


The output above in the code blocks is copied (by hand) directly from the screens. I guess I could connected it to the network and copy the terminal output over, but the contents would be the same.

I do have a second 250 GB drive of a slightly different model but same brand. What should I use to get a copy of the disk to work with? Would Clonezilla be appropriate?

Time is on my side, but not money; and I am uncomfortable with the description of a piece of recovery software with an "evaluation mode", it sounds like many pieces of spyware I've removed from computers over the years. I've also never heard of that company before. I know, things have changed since the days of Windows 3.1 and Norton. I'll have to research this company a bit first. TestDisk I've known of for years, despite never using it before.

(I am reminded, I do have an old copy of the Norton suite on self-booting CD somewhere. I believe it's early XP era. I may try that on a cloned disk.)

---

### Post by bcm37 on 2013-02-20
> **varunendra said:**
> So did you do a deeper search? Can you post the screen output or screenshot 'after' deeper search?

I wasn't very clear with it, but the output:
 ```
 D HPFS - NTFS          0   1  1  6373 254 63  102398247 
>D HPFS - NTFS          0  32 33 30401  42 41  488392704
```is the response after the deeper search. The "real" partition, number 2 on the list, is the item I want to recover.

I can attempt a screenshot this evening -- that's where I've stopped right now due to the errors in size. How do I do a screenshot in Linux? (It's probably not cmd-shift-4.)

---

### Post by varunendra on 2013-02-20
> **bcm37 said:**
> I do have a second 250 GB drive of a slightly different model but same brand. What should I use to get a copy of the disk to work with?
I'm afraid you may need a 'slightly' larger space (even if in a few MBs) to store the image as it would be an exact bit-by-bit copy of your hard disk + (maybe) some overhead. But you may try if it doesn't take too long. Yes, clonezilla would do that if you use Advanced mode and choose an uncompressed image copy (basically dd). But if you can see the acceptable partition structure (the one which shows your desired files), you can also create a partition image using testdisk itself.

The option is in testdisk Advanced menu. In the screen where you select the operation to perform (Analyse, Advanced, Geometry... etc.), instead of the default 'Analyse', select "**Advanced" > Image Creation**

However, if you can see 'all' the desired files in the 2nd partition you want to recover, just make it Primary or Logical as applicable in testdisk, and 'write' the structure to the partition table. No need to bother with image (although it does make you safer). Here's how -

In the [screen]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search") which you copied the output from -
> Using the left/right arrow keys, change the status of the selected partition to L(ogical) ... or Primary if you are sure it was Primary. Although yours looks to me a Logical one.

[How to recognise Primary / Logical partitions]("http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical").

Once the correct mode is set for the [partition]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery"), press Enter > select Write > Enter > y > Ok > quit testdisk and see if the partition has returned.

If not, don't worry, the data hasn't gone anywhere, just the partition table is more messed up :)


**PS:**
> I am uncomfortable with the description of a piece of recovery software with an "evaluation mode"
What Mark suggested is no doubt one of the best data recovery software out there. As one can easily guess from his bean count, he suggests that from experience, not from guess or googling.

In fact, what I mentioned in my previous post - GetDataBack - is another product from the same company and I have been using it for a long time and after testing many top ones. Mark also very often suggests that one.

It's just that in some recent experiences I found testdisk much more faster and more capable. That's my personal experience, not an authoritative fact. Different people may have different experience and thus different opinions. :)

---

### Post by Mark Phelps on 2013-02-20
Varun:  I readily admit, you've got me where TestDisk is concerned.  I tried it a few times and it didn't work well, so I quit using it. I switched over to using Runtime products and those worked a lot better. So, I stayed with the Runtime products (which I had to pay for) rather than going back to TestDisk and PhotoRec.  Maybe recent versions of those are better, I don't know.  I just offer up Runtime products as an alternative for recovering from NTFS problems -- if the Linux utilities don't work.

---

### Post by varunendra on 2013-02-20
> **Mark Phelps said:**
> So, I stayed with the Runtime products (which I had to pay for) rather than going back to TestDisk and PhotoRec.
..and there's no need to look back as long as the current one can do all you need. But if you ever get suspicious that it is loosing something, I recommend you try PhotoRec once more before giving up.

I myself tried GDB first simply because I trusted it more.

I don't fully understand how these software work, but one reason why PhotoRec is faster maybe because it doesn't attempt to build directory trees or retain filenames. It simply dumps everything it finds within the given scope in one sweep.

A disadvantage in terms of filenames/directory-structure, but a definite advantage in terms of speed of recovery.

I still can't explain or even understand why GDB dropped files that Photorec easily recovered. All I know is that GDB has more than twice failed to recover all files / correct partitions, while Testdisk & photorec have so far never failed me. And they are very quick at whatever they do.
:KS

---

### Post by bcm37 on 2013-02-20
Thanks for all your help. I'll try to clone the disk with Clonezilla then see if I can't just make the partition active -- if it will let me with the size error it gave me. I'm not sure how to get around that if I'm stuck. I could try 

I'm fairly sure it's primary, it contains the Windows folder and as far as I know (I could be wrong now) Windows must boot from a primary partition.

I'm not sure how I should be interpreting the numbers in TestDisk, but I think that the first partition listed isn't really a partition. It contains no files and won't respond in XP. I think it was an artifact of letting the recovery disk attempt to repair things before getting a bit more serious in my recovery efforts.

If TestDisk won't write the new partition, I guess I'll try the old Norton disk on the copy; I can recreate the copy later if it destroys everything.

I'll try that new program if everything else fails... maybe I can get my friend to buy it as payment for the work (and returning her data on my spare drive).

---

### Post by mips on 2013-02-20
If the HDD does not have bad sectors them clonezill is fine, else i would suggest gnu ddrescue

---

### Post by bcm37 on 2013-02-20
[IMG]http://imgur.com/npkEJPx.png[/IMG]

This is where I'm stopped at... It took a minute to find a screenshot tool on the disc. I'm downloading Clonezilla live CD.

---

### Post by varunendra on 2013-02-20
> **varunendra said:**
> ..Although yours looks to me a Logical one.
I must admit I didn't look at the outputs thorougly earlier. Now it seems more like a Primary partition to me.

Earlier, I was only considering the fact that it starts on a non-zero head (32). But now I notice two other facts (thanks to the more complete screenshot) which are more important -

First, it also starts at cylinder 0, which, if written clearly makes it a Primary partition.
Second, if created, the second partition in the screenshot is the only partition on that disk since it occupies almost all of the disk. So if you can confirm there was only a single 'windows' partition on the disk, I think we are good to proceed with making it P(rimary) > write the structure.

> Once the correct mode is set for the [partition]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery"), press Enter > select Write > Enter > y > Ok > quit testdisk and see if the partition has returned.

To understand it yourself (if you haven't already), here's what is noticible -
[INDENT]1) The entire disk has 30402 cylinders, 255 heads, 63 sectors (CHS = 30402 255 63)

2) The second partition in the list starts at the very first cylinder (0) and ends at almost the last one (30401)

3) The size of the partition also confirms that it is the only partition on the disk. The size in sectors (488392704), when converted to GiB gives 232.883789062 GiB = the total disk size.
[/INDENT]
With sector size = 512 bytes,
488392704 x 512 = 250057064448 bytes (/1024) = 244196352 KiB (/1024) = 238473 MiB (/1024) = **232.88 GiB**

Sorry for the slight confusion earlier, guess I was too tired to focus ;)

---

### Post by bcm37 on 2013-02-21
> **varunendra said:**
> 
To understand it yourself (if you haven't already), here's what is noticible -[INDENT]1) The entire disk has 30402 cylinders, 255 heads, 63 sectors (CHS = 30402 255 63)

2) The second partition in the list starts at the very first cylinder (0) and ends at almost the last one (30401)

3) The size of the partition also confirms that it is the only partition on the disk. The size in sectors (488392704), when converted to GiB gives 232.883789062 GiB = the total disk size.
[/INDENT]With sector size = 512 bytes,
488392704 x 512 = 250057064448 bytes (/1024) = 244196352 KiB (/1024) = 238473 MiB (/1024) = **232.88 GiB**


Thanks, that makes all the sense in the world. I have it copying in Clonezilla, using "q1" which I believe will do a sector-by-sector copy of the disk using "dd".

---

