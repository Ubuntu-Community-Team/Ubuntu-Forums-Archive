---
title: "How do I make my NTFS partition writeable?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by newagelink on 2006-07-16
I did a search and found [a thread about ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS"), but it's "still in beta" and I don't want to mess with anything unless it's stable (as I'm still a great big newb.)

Thanks so much to aysiu for [the link for remounting the partition](http://www.psychocats.net/ubuntu/mountwindows); I also now have it mounted to "/windows", which makes much more sense than "/dev/hda1".

But NTFS is read-only? I want to be able to write to it! Then I'll *never* have to use Windows, except for iTunes, video games (or get [the emulators working in Linux]("http://home.no.net/qualrom/linuxemu.shtml")? but currently ZSNES, installed through the Add New Applications thing, has no sound), and webcam with my parents ...

What's the best way to go about doing that? Or do I have to wait? Why is NTFS read-only? And, why did it come like that (with Windows XP Home preinstalled), rather than FAT32, if FAT32 isn't read-only?

---

### Post by newagelink on 2006-07-16
> **newagelink said:**
> And, why did it come like that (with Windows XP Home preinstalled), rather than FAT32, if FAT32 isn't read-only?I think I just found the answer to that:
[quote=http://en.wikipedia.org/wiki/NTFS]NTFS replaced Microsoft's previous FAT file system, used in MS-DOS and early versions of Windows. NTFS has several improvements over FAT such as improved support for metadata and the use of advanced data structures to improve performance, reliability and disk space utilization plus additional extensions such as security access control lists and file system journaling. ... also the FAT32 formats to NTFS, but not the other way around.[/quote]That's weird; I thought I converted the C drive of our desktop (back home) to FAT32, so I could disable access to my profile's files from anyone else's ... maybe I got it backwards.

---

### Post by aysiu on 2006-07-16
I would make your shared partition Ext3 and then use [http://www.fs-driver.org](http://www.fs-driver.org) from Windows XP to read/write the Ext3 partition.

---

### Post by newlinux on 2006-07-16
I had some problems using fs-driver. Sometimes it would just crash Windows explorer (not hard to do) by just trying to copy some ext3 files. So I don't consider it safe enough for me - but that's my system. I mainly use an external FAT32 formatted drive for anything I need to write to from both OSs.

---

### Post by newagelink on 2006-07-16
Thank you once again for your quick replies (I am very impressed with this community, better than Mandriva's); I'd like to try that tomorrow afternoon... I gotta get to bed; I've still got 76% of [a US History 1 assignment](http://www.amazon.com/gp/product/1400040299/) to read (essay's due Thursday ](*,)), so I might not be able to mess with this until Thursday afternoon ... I've bookmarked everything.

G'night for now.:rolleyes:

---

### Post by newlinux on 2006-07-17
> **newagelink said:**
> Thank you once again for your quick replies (I am very impressed with this community, better than Mandriva's); I'd like to try that tomorrow afternoon... I gotta get to bed; I've still got 76% of [a US History 1 assignment](http://www.amazon.com/gp/product/1400040299/) to read (essay's due Thursday ](*,)), so I might not be able to mess with this until Thursday afternoon ... I've bookmarked everything.

G'night for now.:rolleyes:

I think this community is great too. I just hope to get to the point where I am helping even a half as much as I am getting help.;)

---

### Post by Medieval_Creations on 2006-10-01
I use ntfs-3g and have had no problems what so ever.  Everything out there for Linux that involves read/write permissions to NTFS partitions is all still labeled as &#8220;Beta&#8221; or &#8220;Testing&#8221; and I really don't see that changing anytime soon.

I would give ntfs-3g a try.  Set it up and move some test data around see if you like it, worst case you don't use it... 

Just a reminder that to copy things to an NTFS partition you have to have be root, so I just use a terminal to copy things over.

Here is the HOWTO: thread for ntfs-3g - [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

