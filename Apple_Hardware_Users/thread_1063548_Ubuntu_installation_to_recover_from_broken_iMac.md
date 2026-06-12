---
title: "Ubuntu installation to recover from broken iMac"
date: 2009-02-08
forum: Apple Hardware Users
---

### Post by oneiric on 2009-02-08
my iMac is kinda messed up --- i'm posting here cause i'm not sure if there is anything else i can try?   My goal right now is to reformat and install Ubuntu 8.10 on an iMac 2007 with Intel.  I would install OS X if I were able to (i have the CD), but i can't select the harddrive as a destination to install.   

Here's a progress report of what I have done:

I am unable to boot in safe mode, or single-user mode, and I am unable to run Disk Utility from the mac os x installation CD. My harddrive appears in red letters when i run Disk Utility and the options to "repair disk" or "verify disk" aren't available.

From Ubuntu Live CD, I downloaded the tools, i ran fsck.hfsplus from the terminal.  fsck.hfsplus ran for about 20 minutes, and then said "Drive check failed".  I re-ran fsck.hfsplus a couple times, but it always ended in failure, and something about bad node structure.

Then I popped in the Ubuntu live CD, and tried to use gparted to reformat my drive, but gparted was unable to format the drive (i think that indicates that something is quite wrong). the saved details were: Input/output error during write on /dev/sda.   By the way, this is an internal drive that didn't sustain any physical damage, it was working perfectly 3 days ago (running OS X) until the problem started when i downloaded and installed a zip.dmg program for recovering files from the trash.

Is gparted unable to format my harddrive because journaling was probably turned on?  (i could never get far enough in disk utility to turn off journaling)  Or perhaps its just messed up?  


So is my computer toasted?  or there is something else i could try at this point?

---

### Post by mkvnmtr on 2009-02-08
As I understand you you are able to boot the apple install disk and the Ubuntu live disk. Is that correct? Do you know how to use the partition editor on the live disk? Do you have files on your mac os you need to save? Can you get those files from the live disk and transfer them to an external hard drive? If so you might use the partition editor to delete your partition where the mac os is and see if you can reinstall. Don't try it if you have things you need to save on your Mac os. If nothing works it might be a bad hard drive. That is not an costly replacement.
Try first to save your files and report back here on what luck nyou had.

---

### Post by oneiric on 2009-02-08
Hi - I have all my files backed up.   Which is good cause I can't get to them from the live CD. 

I'm not a linux expert, but I can boot the computer from the Ubuntu Live CD, and get to the Paritition Editor (System->Administration->Partition Editor).  However, no devices are detected by Partition Editor. Just yesterday Paritition Editor could detect one partition called /dev/sda1, but Partition Editor was unsuccessful when I tried to delete or reformat that drive. AT that time, I had the error details:

Create Primary Partition #1 (ext3, 465.76 GiB) on /dev/sda  00:09:18    ( ERROR )
     	
create empty partition  00:09:18    ( ERROR )
     	
path: /dev/sda1
start: 63
end: 976768064
size: 976768002 (465.76 GiB)
libparted messages    ( INFO )
Input/output error during write on /dev/sda

One more thing  - I ran the MemTest app from the Ubuntu Live CD and had a ton of errors.  

Is this a case where I might want to shred my drive? from ("http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html")

I thought it would be pretty easy to reformat to ext3, and then install Ubuntu.  So I may need a new harddrive at this point?  That's ok in terms of my data its ok, but I wondered if there is anything else I can try to force it to format the drive.

---

### Post by oneiric on 2009-02-08
UPDATE

I attempted to shred the drive, and it worked for about 10 minutes, but then I got an input/outpur error.

I think this indicates that my hard drive is actually broken.

---

### Post by cyberdork33 on 2009-02-09
> **oneiric said:**
> UPDATE

I attempted to shred the drive, and it worked for about 10 minutes, but then I got an input/outpur error.

I think this indicates that my hard drive is actually broken.
That is a good possibility...

It shouldn't matter what partitions are on the disc already, you should be able to use gparted to delete any partitions and create new ones. If that is failing as well, that is also a good sign that you have HD problems.

---

