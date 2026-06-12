---
title: "Need help recovering lost files from corrupt Macbook hard drive"
date: 2012-03-19
forum: Apple Hardware Users
---

### Post by sheft on 2012-03-19
Hello. It seems that one way or another, my Macbook Pro hard drive has failed, or at least the file system is corrupted. My computer locked up a few days ago, and I impatiently forced it to shut down by holding the power button. I have been regretting that decision ever since, because I can't boot it normally anymore.

It's important to note that I had been using Snow Leopard, not Linux, before this problem occurred. I'm posting on this forum because my only success in accessing the hard drive has been by using a Xubuntu boot disc, so that's all I have to work with so far.

When I tried to repair using Disk Utility from the OS X install DVD, it gave me a lot (hundreds) of complaints about invalid nodes, and then finally said that "the hard drive could not be repaired".

Now, when I boot in Linux, I can see the hard drive mounted on my desktop, and I can actually access some of the folders like dev, bin, Library, etc. but when I go to Users/MyUsername, the folder appears empty (there is supposed to be several hundred GB of crap here). When I try to do "ls" in the folder, it gives me "Input/output error".

Based on this vague information (I can provide more), does it seem like there is any possibility of being able to recover anything? There is a lot of **** on this hard drive, but there is one directory that is VERY important, and I need to try every avenue to get it back before I wipe the hard drive.

---

### Post by MisterGaribaldi on 2012-03-19
Personally, my go-to utility of choice for this on a Mac is Disk Warrior by Alsoft. Comes on a Intel- and PPC-Mac supporting bootable DVD. I've used it over the years and it's always worked for me, assuming data wasn't completely corrupted or overwritten, or there was actual "physical" damage to the hard drive.

---

### Post by skullmunky on 2012-03-19
Seconded.  Disk Utility is pretty weak and gives up very easily so don't be discouraged just because it can't handle its job.  

Diskwarrior is a good next thing to try.  I've used it to recover data off a number of Macs that were in pretty bad shape.  It can sometimes take a long time - I used it on a G4 a while back and the recovery literally took weeks - but that's extreme.  

Good luck! 

I'm gonna go back up my drive right now ... this just made me think again about how out of all the computers in my life, the HFS and HFS+ drives are the ones that have the most catastrophic failures.  Hm.  wonder why that is.

---

### Post by varunendra on 2012-03-20
You may try [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") (part of TestDisk) which is the hottest choice for data recovery around here. Don't know about DiskWarrior so can't say which one would be better.

However, the "Input/Output error" part is something alarming. I believe it usually indicates a physical damage on the area where the reading attempt produces this error. If so, I'm afraid any software can't do much about it.

If you have an external drive with at least as much space as the failing disk size is, I'd strongly recommend to install [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") on Xubuntu, run it and create an 'Image' of the failing disk. You can later mount this image as a disk and run any recovery-software of your choice to attempt file recovery. This is very helpful in case of a failing disk or where there is physical damage that gets worse everytime you try to 'read' it. In comparison, the image is 'freezed', so doesn't get worse when you mount or read it.

To use TestDisk/PhotoRec, install it with:
```
sudo apt-get install testdisk
```
assuming you can connect to internet from the live session. If you can't, you can download its .deb package from [here]("http://packages.ubuntu.com/search?keywords=testdisk&searchon=names&suite=all&section=all") (along with dependencies if required) and install it manually.
To run testdisk (to create image):
```
sudo testdisk
```
Image creation option is found in [Advanced] option.

To run photorec (to recover files either from the mounted image, or directly from the disk):
```
sudo photorec
```

PhotoRec Step by Step: [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Once again, I'd strongly recommend to create an image of the disk if you can, then work on it instead of the failing disk itself.

---

### Post by sheft on 2012-03-20
Thanks so much for the advice guys. I ran DiskWarrior last night and it actually only took about an hour (I was expecting several days). It was unable to repair the disk, but it allowed me to recover pretty much everything I needed, so I dodged the bullet.

Now here's another question: will this hard drive be OK if I wipe it and re-install the OS? I'm assuming since it was just a self-inflicted corruption of data, and not an actual hardware failure, that I won't need to buy a new drive?

---

### Post by varunendra on 2012-03-20
> **sheft said:**
> will this hard drive be OK if I wipe it and re-install the OS?
If you can, just do it. But either don't put any important data on it, or only put those which you have already backed up (regular-backups is a good practice anyway, for any storage device..). Trust it only if it performs well long enough to deserve so.

By the way, congratulations for the recovery!

---

