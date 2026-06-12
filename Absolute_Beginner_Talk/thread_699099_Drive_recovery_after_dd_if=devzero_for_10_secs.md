---
title: "Drive recovery after dd if=/dev/zero for 10 secs"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by lucasl on 2008-02-17
I am such an idiot.
I was trying to overwrite my flash usb with zeros, so I used the command dd if=/dev/zero of=/dev/sda
The only problem was, the flash drive is sdb, and sda was my hard drive.
I quickly cancelled, but not before 200mb+ of zeros had been copied.
Not suprisingly, I can no longer boot.
My first partition was Windows NTFS with about 3-6 GB of used space, then I had (don't remember the order) a home partition, root partition, both XFS and a boot partition (ext3). Hopefully my Ubuntu partion(s) are still intact, and most of my windows. Is there a way for me to recover my data?

Thanks *cry*

---

### Post by spiderbatdad on 2008-02-17
There is a nasty little utility called Photrec, but beware it can potentially fill your home folder will 1000's of files. By default you wont have permission to access them.  You couldn't repair a broken operating system with this program, but you could recover lost data.

---

### Post by spiderbatdad on 2008-02-17
There is also testdisk in synaptic...never tried it.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by lucasl on 2008-02-17
It doesn't really do the formats I need it to. Damn.

I was smart enough to backup my most vital files before restarting,, so I guess ill just have to work with it and reinstall. sigh.

---

### Post by teknosexual on 2008-02-17
You can probably salvage your data using the Ubuntu Live CD. Copy to external drive.

Once you've done that...

Try using the TestDisk utility on the GParted Live CD
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You'll want to read up a little on how to use it. I'd recommend reading through here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
in order to familiarize yourself with it.

Then you can go in and see if your partitions are still in tact (it sounds like they should be).

You will probably want to rebuild the boot sector. After doing that, reboot, see what comes up (we hope GRUB!). If still nothing, try repairing the MFT through TestDisk.

If Windows boots but there is no way to get to Ubuntu, then you'll need to reinstall GRUB. There is another tool I would recommend called Super Grub Disk. It is able to rebuild GRUB for you. It's a Live CD or Live USB.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Well, I hope some of that helps! Definitely try to get your data before you do anything else.

---

### Post by lucasl on 2008-02-17
How would I copy the data to an external drive? Would I use dd?

---

### Post by polmir on 2008-02-17
Try this from liveCD (knoppix)
[http://wiki.linuxquestions.org/wiki/Dd_rescue]("http://wiki.linuxquestions.org/wiki/Dd_rescue")

---

