---
title: "Ubuntu, MacBook Pro and external hard drives"
date: 2006-06-22
forum: Apple PPC Users
---

### Post by pauljcg on 2006-06-22
Hi

I was wondering if anyone could help me. I've installed Ubuntu on a USB 2.0 Hard Disk drive and I wish to boot it on my MacBook Pro (15"). I've done this so that I wouldn't have to worry about formatting or partitioning my computer's hard drive (I've got OSX and Windows set up how I like) but still get to play with and learn more about linux.

I've set up rEFIt and it 'sees' my USB hard drive with Ubuntu on it. However when I select it to boot, Windows starts instead! I've tried following the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=198453"), replacing "/dev/sda4" with "/dev/sdb2" (since this is where the unbuntu CD identifies my USB disk) but this didn't change anything. I was hoping that somebody might have an idea. I understand what I'm proposing to do is not very usual and that BootCamp/rEFIt are relatively new technologies but if anyone can help, I thank them in advance!

Paul

---

### Post by phico on 2006-06-22
Did you sync partitions in rEFIt menu ?

---

### Post by entangled on 2006-06-22
Pauljcg
Due to the way BootCamp works (assuming you have used that to get Windows running) I think you will need to put the mbr from your external usb disk onto your windows partition.

You have run lilo and put the mbr onto your external disk.
Now mount the windows partition (sda3? Hope it's not NTFS!), cd to the windows partition, and type
sudo dd if=/dev/sdb2 of=Linux.mbr bs=512 count=1

This should copy the sdb2 mbr to a file on the windows partition (C drive).

Now tell windows what to do with it. 
Edit the windows file boot.ini and make the last line read
Linux=C:\Linux.mbr

cd back to home and umount windows. Reboot.
Now you should select Windows when rEFIt offers it, then choose Linux at the next menu to boot off the usb disk.
Hope it works for you.

---

### Post by Ray-T on 2006-08-09
Did anyone succeded in doing that?

I'm about to install ubuntu on my macbook and I'm faced with the decition to either put it in the windows partition (replacing windows) or on a usb disk.

Andrea

---

