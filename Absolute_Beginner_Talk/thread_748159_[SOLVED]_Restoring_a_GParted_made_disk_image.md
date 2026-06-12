---
title: "[SOLVED] Restoring a GParted made disk image"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-04-07
Hi,

I'm about to reinstall XP and overwrite my whole int.HD.  I then plan to reinstall Gutsy - using the live CD - and then hopefully restore a disk image I made using GParted.  The disk image was only made of Ubuntu and I have about 20 files called Backup 001, Backup 002 etc.  I plan to have a windows partition of about 10GB and the remainder of my 74GB will be given to Ubuntu.  

However, I'm unsure of how to write the 20 backup files to Gutsy (once I've reinstalled it) to restore the settings I had when I made the disk image.  It's taken me ages to get Ubuntu how I want it so would prefer to restore the disk image, over doing a complete fresh install and going through the various time consuming processes to get it back to what it is now.  Any ideas gratefully recieved.  Thanks.

---

### Post by neurostu on 2008-04-07
What you are going to need to do is to copy the disk image as a FILE to your new ubuntu install. Then you can mount the image (like how you mount an external HDD or a CD) then you can copy files from the image to your HDD.

---

### Post by Berean on 2008-04-07
neurostu,

Will that also be all my configuration files for wifi, printer etc.?  It was difficult getting this all running and I simply want the easiest option.  I think I copied all the files on my hard drive so will they simply overwrite the ones installed with the live CD?  Thanks.

---

### Post by neurostu on 2008-04-07
Well that depends... the best option will be to copy your /home directory from your image to your HDD.  That will take care of a lot of things that you have customized.  However some programs that don't save customizations in the /home directory will not be fixed.  

I would advise against just copying everything over... that might work but I would bet that it will not work. 

I've never tried it; however, things might not end up working the way you think they might.  

For example: The file that ubuntu uses to mount your HDD and its partitions will be different. Every time you edit your HDD with GParted the partition ID's change. The old install you have will have the old partition IDs and where as your new install has the file that points to the correct partition id's. Copy over this new file will really break things, and could possibly make ubuntu un bootable.

I would suggest just copying over your /home folder and nothing else.

Again this _will_ move a lot of customizations over but not all of them.

---

### Post by Berean on 2008-04-07
You're giving me alot of help today, neurostu: thanks.  I'm investigating all avenues available to me at present and one is the external booting of either a windows system (XP) or Ubuntu, so I don't have to play around with another internal HD (to run XP from) as I can't get the iPod to work in Ubuntu (from my other thread).  I didn't think I could do this, but when I look at the BIOS setup it states;

Boot device Priority
1st boot device [Removable Dev.]
2nd boot device [CD/DVD]
3rd boot device [Hard Drive]
4th boot device [Network: On board]

and so - I assume - I can boot from an external HD or USB.  Is this correct?  If so, I have a 4GB flash drive and wondered if I can boot Windows from that?

---

### Post by neurostu on 2008-04-07
I don't know about booting windows from a flash drive? but I have ubuntu installed on an external HDD and I can boot to that when it is plugged into a usb port.

---

### Post by Berean on 2008-04-08
I've tried it - Ubuntu on an external HDD - and it works fine: maybe I'll do this.  Thank you for your help.  Regards,

---

