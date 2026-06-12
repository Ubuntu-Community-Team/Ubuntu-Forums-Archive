---
title: "File System Check every 30 Mounts"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by prodonjs on 2007-01-18
I run a dual boot with XP Pro and Kubuntu and today when I rebooted to leave Windows and start Linux, during bootup I got a message saying that the file system on /dev/hda2 which is my main Linux partition has not been checked in 30 mounts so it was checking. It went through fairly quickly and said it found errors but then restarted and everything was cool.

Is this a sign that there is corruption of my file system or is this just a commonality that occurs? My experience in Windows with programs like ScanDisk say that sometimes those errors are trivial and other times they indicate a failing hard-disk, which I had a few months back. 

Anyways, is it anything that I should be worried about?

---

### Post by zerhacke on 2007-01-18
Linux always fscks the disks every thirty mounts.  It doesn't mean you have any hard disk problems.

---

### Post by irish_flu on 2007-01-18
The 30-mount checking is normal, but wither or not the errors indicate a problem depends entirely on what those errors were.  :)

---

### Post by wpshooter on 2007-01-18
> **prodonjs said:**
> I run a dual boot with XP Pro and Kubuntu and today when I rebooted to leave Windows and start Linux, during bootup I got a message saying that the file system on /dev/hda2 which is my main Linux partition has not been checked in 30 mounts so it was checking. It went through fairly quickly and said it found errors but then restarted and everything was cool.

Is this a sign that there is corruption of my file system or is this just a commonality that occurs? My experience in Windows with programs like ScanDisk say that sometimes those errors are trivial and other times they indicate a failing hard-disk, which I had a few months back. 

Anyways, is it anything that I should be worried about?

I would get the drive diagnostic software from the drive manufacturer and run it on the drive to check for problems.  My **GUESS** is that if Ubuntu chkdsk is detecting error, you may very well have some disk problems.

---

### Post by prodonjs on 2007-01-18
I didn't get a chance to see what the errors were, was there a log saved somewhere?

---

### Post by TwistesdTexan on 2007-01-18
Every time you boot for the 30th time Ubuntu checks the disk. It doesn't mean there is or is not a problem It is checking to see how fragmented you disk is. If there is a problem the check wil let you know.:)

---

### Post by wpshooter on 2007-01-18
> **TwistesdTexan said:**
> Every time you boot for the 30th time Ubuntu checks the disk. It doesn't mean there is or is not a problem It is checking to see how fragmented you disk is. If there is a problem the check wil let you know.:)

I believe the poster said that it did indicate that the were errors/problems thus that is why I would recommend running diagnostic on hard drive.

---

### Post by prodonjs on 2007-01-18
Yeah so that is what I am wondering. Does fsck generate a log that I can view. It didn't pause at the screen for me to see anything but it did say that the drive was some percentage fragmented. It went fairly quickly so I can't see how the errors could have been serious unlike when I ran into trouble in Windows using chkdsk and it took well over a half hour to do checks and many physical errors were found.

---

### Post by RomeReactor on 2007-01-18
To view the logs type in a terminal:

```
cat /var/log/fsck/checkfs
```

and:

```
cat /var/log/fsck/checkroot
```

As has been said, Ubuntu does a fsck every 30 mounts; if, like you said, it found errors but corrected them, then i think you shouldn't worry about it. In my machine, more often than not, when the system does a fsck it usually finds errors (mostly due to fragmentation, i suppose) but corrects them and upon restart i have never had any trouble whatsoever...

---

### Post by louieb on 2007-01-18
I have Ubuntu installed on a 10+ year old 30 gig Western Digital. Every now and the I will get fsck errors during boot. File system is EXT3. From what I can tell fsck tries to fix the file system. When it can't, I get the CLI and the root prompt and a message to press control-d to continue boot. So far after I press control-d the computer boots normally and I am able to log on to Gnome. Everything works. The next time I booted had to wait and watch page after page of fsck errors, get the CLI, press control-d and it works.

I backed up the partition and reformatted it restored the data and that got rid of the fsck errors on boot.  I take it as a warning that the drive is probably nearing the end of its useful life. 
So I am backing up my system a little more often.

---

### Post by Marsolin on 2007-01-18
The logs won't necessarily tell you if the drive is starting to fail or not.  Errors can occur from a variety of ways, including the computer being powered down without doing it through software.

I'd suggest installing the smart-notifier package and see if it will work with your hard drive.  SMART keeps track of how your drive's health is doing and is intended to be an alter for impending failure.

---

