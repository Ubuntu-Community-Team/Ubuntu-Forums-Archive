---
title: "[SOLVED] Partimage: disk full when not!"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-03-21
I'm trying to make a disk image using partimage (GUI) in terminal.  I've formatted my external HD to 135GB FAT32, and 80GB ext2 (or poss.3).  I've inputted all the details (I've typed "partimage" at the terminal prompt, and just filled in the required info) but once it starts copying it soon says disk full, or something similar!  When I mount the external HD - because of the 2 partitions - it shows up on the desktop as Disk and Disk-1.  Disk-1is something like 78GB with 4GB used, but I can't copy more than a couple of GB's from my internal HD (which is also approx.78GB, with about 40-45GBs used).  I'm pulling my hair out!  As I said, the external HD has just been formatted, and when I look in properties for Disk-1 it has a folder called Lost+ Found with the emblem "unreadable" attached.  I assume this is the 4GB that's been used, but why can't I image the whole of my internal HD to my external HD when clearly there is enough space?  Your help is appreciated: thanks.

---

### Post by Midahed on 2008-03-21
I've had a similar problem once or twice.  In each case it was because the image wasn't being written to the intended external device - usually because I omitted to specify it properly..

It might help if you show exactly what you are doing on a line by line basis and chuck in the output of the mount command for good measure.

[Edit]...  One other point...  Are your trying to image your 'live' system partition?  What do you boot off when you want to image the system?  A Linux rescue CD or the Ubuntu installation CD?

Just checking....

Mike

---

### Post by ByteJuggler on 2008-03-21
FAT32 has a filesize limit of 4GB (or is it 2GB) so you need to ensure, when writing to FAT32 partitions, that the filesize of a single file never exceeds this limit.

Edit: It appears that partimage will by default split into files of 2GB in size, so I'm a bit puzzled.  (In any case, you can set the split up under "Image split mode" on the second partimage screen.)  However, please note, there's also a limit on the number filesystem entries you can use on the root directory of FAT32, so it's advisable so always save into a subfolder, as they don't have such restrictions.

---

### Post by Berean on 2008-03-21
Sorry guys, baby needed feeding!  Okay, I'm not trying to write to the FAT32 partition, I'm trying to write to the ext2 (or 3).  I go to terminal and simply input "partimage" which brings up the GUI.  I then use the up,down,left/right keys to specify what I'm copying and to where.  I'm not able to change any of the pre-loaded options, highlighted by an asterix.  I save sda2 (I have no sda1) and attempt to save it to "disk-1".  I cannot do anything if I specify "/media/disk-1" or "/media/disk-1/": it just won't even start!  But to be clear, it is a disk image to ext2 (or 3) on an external HD, and not FAT32.

I'm obviously doing this with the live CD, with sda2 unmounted.

---

### Post by ByteJuggler on 2008-03-21
It almost sounds like you're trying to write the backup to the raw disk device.  You should instead make sure the partition/filesystem you're trying to write to, is mounted someplace suitable (/media/ is good, or /mnt), then input /media/disk-1/backup (to create a file called "backup" on te backup partition root).  I presume you're running partimage with "sudo" in front?  (Otherwise it won't work either.)

edit: to manually mount sda2 on a folder, try

```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
```

Then when you enter a location to save to in partimage it should be "/media/sda2/backup"

---

### Post by ByteJuggler on 2008-03-21
somehow managed a duplicate post... meh

---

### Post by Midahed on 2008-03-21
> **Berean said:**
> ....I'm obviously doing this with the live CD, with sda2 unmounted.

Good - but it wasn't obvious - and it's safer to check these things ;-)

Without being able to see exactly what you're providing in the partimage dialogue, I'm a bit stumped for further ideas.  I still suspect that partimage is actually buffering the image and fails when it runs out of memory.

When I use partimage I use a rescue CD and have to change the permissions to my backup drive before I manually mount it.  Having done that, I need to specify the image file as something like /mnt/backup/image-hda1

What are you specifying to partimage as the target for the image?

Rather than firing up partimage, can you use terminal commands to create a file on the target drive - just to test that you have access to it.

Mike

---

### Post by Berean on 2008-03-21
Aaargh!  These are the screenshots I'm getting (I'm hoping they'll be included!) but I still don't understand what I'm doing wrong.  Is anyone the wiser?

---

### Post by Berean on 2008-03-21
> **ByteJuggler said:**
> It almost sounds like you're trying to write the backup to the raw disk device.  You should instead make sure the partition/filesystem you're trying to write to, is mounted someplace suitable (/media/ is good, or /mnt), then input /media/disk-1/backup (to create a file called "backup" on te backup partition root).  I presume you're running partimage with "sudo" in front?  (Otherwise it won't work either.)

edit: to manually mount sda2 on a folder, try

```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
```

Then when you enter a location to save to in partimage it should be "/media/sda2/backup"

Can I clarify that I should sudo mkdir /media/sda2 and NOT sudo mkdir /media/sdb1! and then sudo mount /dev/sdb1?  Sorry, I'm new and don't want to complicate matters.  Regards.

---

### Post by Midahed on 2008-03-21
The clue is in the 4th image.  When you specify the 'image file to create/use'  you need to include a filename as well.  At the moment you are just specifying the device.

Can you also run the command..

mount

... in a terminal session and post the results.

---

### Post by Berean on 2008-03-21
Image 6 is a follow on from the previous screenshots, and screenshot7 is what you've requested.

---

### Post by Midahed on 2008-03-21
The mount command shows that your ext2 partition on /dev/sdb1 is mounted on /media/disk

From the earlier screenshots it looks like at one time you were trying to save the image on your fat32 partition....

If you specify /media/disk/backup as the file that partimage is to use, it should create the image OK.  If you want you can choose a name other than 'backup' for the filename.

Mike

---

### Post by Berean on 2008-03-21
Okay, I'm where I was before (see image) and have used your suggestion and renamed the file /media/disk/totalbackup so I don't get confused with my files stored on the FAT32 partition which are called backup.  Please don't leave me!  I feel it in my waters: something good may be about to happen........

---

### Post by Berean on 2008-03-21
This is what I'm seeing at present (but I've been here before!).  I'll post again in a couple of minutes in case it stops again.......

---

### Post by Midahed on 2008-03-21
That looks more hopeful.

When you do this in future, you shouldn't assume that your ext2 partition on /dev/sdb1 will always be mounted in the same place.   it's an idea to run the 'mount' command each time just to check  in case some other system change has resulted in it being somewhere other than /media/disk

Mike

---

### Post by Berean on 2008-03-21
Mike, you're very kind: thanks so much!  The irony is that I've actually done this before and even installed the image onto another laptop.  Therefore, I was either lucky, and now am very stupid to have forgotten how I did it, or not to see my basic error.  However, as mentioned, I'm a newb so this has been a fantastic - albeit, frutstrating - learning experience.  Once again, thank you.  Incidentally, the final screenshot is showing the furthest I have got.  If this doesn't complete can I come back to you?  Regards.

---

### Post by Berean on 2008-03-21
Sorry, wrong image.  It's looking even more promising!

---

### Post by Midahed on 2008-03-21
No problem, but it **will** work this time.  Have some confidence ;-)

The key is in that last screenshot where it says the 'available space for image' is over 70 gig.  I'll bet whatever you like that you weren't getting that before.  The reason is, as I suspected in my first post, that you were not correctly specifying the mount point and filename for the image.  It's the same mistake that initially tripped me up a couple of times.  As you say, it works for a second or two and then complains that it has run out of space.

Mike

---

### Post by Berean on 2008-03-21
Due to the progression of Partimage (see screenshot) I think I can post this thread as being solved!  Once again, thank you Mike, and to the others who have posted.  Regards.

---

