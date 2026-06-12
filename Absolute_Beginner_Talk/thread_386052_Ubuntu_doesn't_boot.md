---
title: "Ubuntu doesn't boot"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Awesome_Joe on 2007-03-16
A couple of days ago, I downloaded the desktop version of Ubuntu.  I used InfraRecorder to do a checksum on it and to burn the iso image.  Everything seems fine with the cd.  Unfortunately my computer doesn't want to boot off of it, even though my BIOS is set to boot from the CD drive first.

How come I can't boot from the CD?

---

### Post by mrmonday on 2007-03-16
Is your disk bootable? in windows can you see one big file or some folders and files?

---

### Post by taurus on 2007-03-16
Do you have a Windows on your machine?  Insert the CD and you should see a bunch of files and directories on the CD.  If you only see one large file, then you have burnt it wrong.

---

### Post by mahy on 2007-03-16
Are you sure your computer boots other systems off a cd? Can it boot windows? (just a proof of concept)

---

### Post by Awesome_Joe on 2007-03-16
When I burnt the iso image, it created several folders and files on the CD.

I'm currently using WinXP.

I don't know if my system can boot other system CDs.  I never tried.

---

### Post by Najand on 2007-03-16
What do you mean by?
> When I burnt the iso image, it created several folders and files on the CD.
When you boot your computer by pressing one of Del/F2/F12 or something like these you can go to the BIOS configuration and can see if you have enabled booting from CD or if it does it before other Hard Drives.

---

### Post by natman on 2007-03-16
Try buring the image to a different disc ( some discs can just be bad and may not be bootable, this happened to me before ).
So get a new blank or reformat the old ( if its a CD/DVD RW) the re burn and try again.

Good Luck

---

### Post by joeylq on 2007-03-16
Microsoft has just released their virtual pc as free.  I mention this because you can read the pc as if it was a disk in the cdrom drive and can boot off the image.  It is an awsome tool, and is verry useful.  You can install an entire operating system in to a virtual pc and use most of the operating system's functions as normal.  It would have saved me hundreds of disks a few years ago.  Cds dont always burn perfectly so chances are the image may be slightly defective on the cd.  If the imgage boots up nicely in virtualpc the cd itself is probably defective.  I also heard that dual layer dvd's are not bootable, not that you did that....

---

### Post by Awesome_Joe on 2007-03-16
What I meant by "When I burnt the iso image, it created several folders and files on the CD." is that I didn't just copy the iso file to the CD.  Some of the folders on the cd are .disk, bin, casper, etc.  There is also a start application file, md5sum text file, and several other files.

My computer is set up to boot off of the CD drive first.  I put the CD in before I boot up, but my computer still boots up in Windows.  When Windows sees the CD, it starts the DiscTree program that is on the CD (basically showing me what is on the CD).

I don't think the CD is bad.

---

### Post by Najand on 2007-03-16
If you have Virtual Machine like: vmware, MS Virtual PC, etc, try to see if it can boot the cd or not.

---

### Post by dstew on 2007-03-16
What computer do you have? Some BIOSes want you to first enable boot from CD/floppy, then change the boot order, so you might have to do two things. Also, I seem to remember a problem similar to yours that ended up the computer needed a BIOS update, and it worked fine after that. A lenovo PC, I believe.

I found the thread:

[http://ubuntuforums.org/showthread.php?t=379387](http://ubuntuforums.org/showthread.php?t=379387)

---

