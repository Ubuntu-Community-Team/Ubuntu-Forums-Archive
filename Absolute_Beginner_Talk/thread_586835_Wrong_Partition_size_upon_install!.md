---
title: "Wrong Partition size upon install!"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by dbrooke on 2007-10-22
Hello, I just installed ubuntu 7.1x *server* on my old Dimension 4100... I made a couple errors... first in the partitioning:

I wanted to keep a Windows ME partition and use Grub to choose what OS to use upon startup. That all went fine, but I accidentally gave ME too much disk space!  I wanted linux to have most of the space! ;-)  So, now I have 15GB's for old windows ME, and only 5GB's for my brand new shiny gutsy gibbon server install!  *crap* 

So, anyone know what I can do to switch that?  I want ME to have the 5GB's and Linux to have the 14GB's. 

Oh, and I'm posting on the noob forum for a reason. :)  Please be clear. Thanks! 

Donovan

---

### Post by SOULRiDER on 2007-10-22
Well, fgirst of all I suggest you get the gParted disc, its a Live CD with tools to manage hard drives. 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Just burn the disc, reboot and boot from CD. Once it finished loading just resize the partitions. If you have any other questions just post.

---

### Post by dbrooke on 2007-10-22
Thanks... can I just use the "parted" command?.. or will that overwrite data?

Donovan

---

### Post by Irony on 2007-10-22
First copy your ubuntu partition to an external drive like I describe here;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

Then resize your ME ntfs partition which is a 2 stage process of resizing the filesystem and then resizing the partition, which I outline here (is ME ntfs, I'm not sure?);

[http://ubuntuforums.org/showthread.php?t=575047](http://ubuntuforums.org/showthread.php?t=575047)

Then copy back the backed up ubuntu to the new bigger partition.

I'm afraid its all command line based - there maybe some gui programs that can do the ntfs resizing but I couldn't find any when I last did it.

Of course backup everything and defrag your windows partition a couple of times to get it nice and small.

You'd do this from a live CD, so you might have to install ntfsresize on it for it to work.

---

### Post by dbrooke on 2007-10-22
irony, thanks.

I attached my 250GB firewire/usb drive to my old 4100 (<-- donovan thinks that funny) (connected via USB).  I then checked out your reference link about coping to an external drive... however,
I have a question first.


This is my back-up drive. I'm not going to write over anything am I?

When I execute the command:

sudo mkfs.ext3 <path> 

I get a warning message:
"/dev/sdb is entire device, not just one partition!"
"proceed anyway?"

I just want to make sure I'm not writing over anything!

Thanks,
Donovan

---

### Post by Irony on 2007-10-22
The command;

[PHP]sudo mkfs.ext3 <path>[/PHP]

Will format (it means make filesystem into ext3) anything on that path as ext3 so if there is anything in that path it will wipe it.

If your backup drive doesn't have a spare partition then you will need to make a spare partition on it (using say gparted you can create a partition at the end of the drive of say 5 GB).

On the other hand if you drive is ext3 already and you have enough space on it then create a folder called say ubuntu and simply copy your ubuntu into it - you won't have to format anything.

---

### Post by dbrooke on 2007-10-22
its HFS+... I suppose I will have to create a partition...

I dl'ed LiveCD (gparted) and am currently resizing the ME partition!... (I think.. it says 1 opertion pending, but I don't hear any HD noises??).


Thanks.


Donovan

---

### Post by Irony on 2007-10-22
I tried the gparted live cd a couple of years ago and it didn't resize ntfs partitions despite saying that it did - it uses ntfsresize which is what the instructions I outlined use but in command line manner.

---

