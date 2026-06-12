---
title: "Wiping, Partitioning &amp; Reinstalling OS X"
date: 2007-11-25
forum: Apple Intel Users
---

### Post by 3nigma on 2007-11-25
Hey guys =)

I had OSX and Ubuntu installed on my MacBook, and my OS X got corrupted.  I recovered the data, and I am now trying to reinstall OS X.

I tried to boot from the OS X install DVD, but the Disk Utility wasn't able to work with the hardrive.  I know there isn't a hardware problem, because Ubuntu booted fine and Apple said that it was probably fine.

Disk Utility wasn't able to partition, giving me the error "Input/Output error."

I decided to try and use the Ubuntu disc to try and partition the drive.  It worked totally fine, in contrast to the Mac Disk Utility, and so I partitioned the entire drive as an "Auto" partition, with the whole disk EXT3 and a small one as swap space.

Afterwards, I confirmed the new Ubuntu worked great.  Then, I tried to boot from the OS X install DVD again, and try Disk Utility.  Disk Util could repartition the disk only enough to destroy the Ubuntu install, but it wasn't suitable to install OS X onto it for some reason, input/output error.

Finally, I reinstalled Ubuntu with the entire disk as EXT3 this time, instead of an additional small one for swap space.

Is there any way to get my Disk Utility to partition the disk, or any other way to partition it in a way that Tiger can be installed?  It needs to be Mac Extended (Journalled), and GUID for Intel Macs.

What do you guys think?  Ubuntu is working in the meantime...

Thanks again.

---

### Post by 3nigma on 2007-11-26
bump 0=\

---

### Post by Grey Box on 2007-11-27
> I had OSX and Ubuntu installed on my MacBook, and my OS X got corrupted. I recovered the data, and I am now trying to reinstall OS X.
I am just wondering if your OS X got hosed in the most recent update which [ killed a few other people's machines]("http://apple.slashdot.org/article.pl?sid=07/11/27/0040206") who had their macbooks set up with BootCamp and were still running Tiger. 

But to answer your post, I haven't tried your exact scenario, but I have used gparted successfully to resize the HFS partition that OS X is on. gparted is also able to create HFS partitions. Any honest OS installer would let you install on it, but of course that doesn't mean OS X will. Also I suspect OS X doesn't expect to find other OS's in partitions having a greater rank than itself if you know what I mean. perhaps the HFS partition has to be in /dev/sda1 or /dev/sda2. 

I am not sure if you need the EFI partition there or not, either. Maybe if it's missing then the installer gets a hissy fit?

Am glad this hasn't yet happened to me, but I don't think I'd be breaking down in tears, I'm hardly using OS X now. Reminds me of my last computer with XP on it *grin*.

---

### Post by 3nigma on 2007-11-27
Hey dude,

Thanks for the insight.

I called Apple, and the dude said that I need to just format the entire disk and then do the partition/install.  However, I'm getting the same input/output error even in trying to wipe the disk.

What he said was to find a utility that can just wipe the disk.  He said even using a Windows install disk ought to have it on it, and wipe the disk.

Any other insight that this adds to people?

Thanks again!

---

### Post by cyberdork33 on 2007-11-27
> **3nigma said:**
> Hey dude,

Thanks for the insight.

I called Apple, and the dude said that I need to just format the entire disk and then do the partition/install.  However, I'm getting the same input/output error even in trying to wipe the disk.

What he said was to find a utility that can just wipe the disk.  He said even using a Windows install disk ought to have it on it, and wipe the disk.

Any other insight that this adds to people?

Thanks again!

Boot a Live CD. Start Partition Editor. Delete all partitions. Create 1 large Fat32 partition and try again.

---

### Post by 3nigma on 2007-11-27
Thanks very much for the help =D

When I'm in the Live CD, how do I access the partition editor?  I am using Ubuntu installed on my HDD now, and I couldn't find it in the System menu (just to learn where it is, in preparation for using the LiveCD).

Mac OS X uses the "Extended (Journaled)" partition format.  Will it still work with Fat32?  Or do you think Fat32 might be readable by the OSX install DVD and Disk Utility, so I can then reformat it as Extended(Journaled)?

Thanks again, this helps me much more than the Windows CD.  I sincerely appreciate all the help.  I can't wait to have a need for a standalone desktop computer, because I fully intend on making it a dedicated Ubuntu machine.

Thanks again.

---

### Post by cyberdork33 on 2007-11-27
> **3nigma said:**
> When I'm in the Live CD, how do I access the partition editor?  I am using Ubuntu installed on my HDD now, and I couldn't find it in the System menu (just to learn where it is, in preparation for using the LiveCD). It is not installed by default, but is on the Live CD. You have to use it with the cd anyway as you would be deleting the Ubuntu partition as well. It is under the admin menu, I believe.

> Or do you think Fat32 might be readable by the OSX install DVD and Disk Utility, so I can then reformat it as Extended(Journaled)?exactly. The OSX filesystem format is really called HFS+ by the way.

---

### Post by 3nigma on 2007-11-27
Thanks dude =D

I'll try it out and let you know how it goes!

---

### Post by 3nigma on 2007-12-04
Thanks again for the help guys!

I just finished writing my term papers and finally got a chance to test this out.

I loaded the Live CD and opened partition editor.  I had a big Ubuntu partition and a small swap one.

I managed to destroy my Ubuntu install, but not format/erase the disk.  Whenever I try to run the Partition Editor at the final steps of actually executing the changes, it gives me an errer report and crashes the editor.

I tried the Mac install disc again for another try and it didn't work.  Also, when I put the Live CD back in, this time it showed the hard disk as a clean slate that needed a diskabel (I have tried the e"mac" option and the default "msdos"), and nothing works.

Even trying to "refresh" the partition menu by scanning for all devices (hard disks), it crashes.

Any ideas? Thanks again!

=\

---

### Post by tiiim on 2007-12-05
So have you tried just to delete all partitions and leave it as blank disk with no file system on? then try and run OS X?

---

### Post by 3nigma on 2007-12-06
You got it.  I try and delete the partitions, and the partition editor crashes.

Thanks again

---

