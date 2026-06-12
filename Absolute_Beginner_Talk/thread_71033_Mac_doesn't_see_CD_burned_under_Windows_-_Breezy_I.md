---
title: "Mac doesn't see CD burned under Windows - Breezy Install"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by breakdaze on 2005-10-02
Hi, I downloaded the Ubuntu 5.10 Preview Install image for PowerPC, used Nero on a Windows 98 box to burn it at 32x, disk-at-once, iso image writing method. The ibook G3 300 won't read the CD, but Windows will read it just fine. Did I do something wrong? Should I burn it at 16x? Should I select "finalize CD"? Should I use disk-at-once/96? UltraISO under windows shows that the ISO is a Hybrid HFS / Rock Ridge image. It doesn't think it is bootable, but maybe it can't detect whatever makes a Mac CD bootable.

Thanks for any info.

---

### Post by aysiu on 2005-10-07
What are you doing to get the iBook to read the CD? Do you know that most Macs do not look to the CD-ROM drive for a bootable CD? You usually have to hold down the C key during bootup to get it to try to boot from CD.

---

### Post by breakdaze on 2005-10-08
Yes, I should have clarified. When I insert the CD-R into the drive with MacOS 9.22 booted, the CD drive makes seeking sounds then presents a dialog window that it is unreadable and do I want to Initialize or Eject it. If I reboot and hold "C" it just boots through to 9.22 and gives me the same message. If I put yaboot and related files in the root of the Mac hard drive, I can run yaboot from open firmware, but it says that the CD device has a problem. I did notice that the files on the CD-R got burned in all uppercase and in the 8.3 filename format. So, obviously the images are getting burned using the strict ISO 9660 conventions even though Nero recognized that the image was a Hybrid.

OKAY, so all of that is moot now, because I utilized my DSL router and Windows 98 computer to serve the install files and do a media-free net install of Hoary. I am impressed with open firmware now.

It installed beautifully and easily. I like Ubuntu Hoary.

I just hope Macromedia compiles a flash plugin for Mozilla under Powerpc architecture. I know there is a package available, but that only covers Flash 5 and under. There is some work being done on a second version of the plugin for 6 and above, but one has to go way upstream and compile it.

Thanks for the reply anyway.

---

