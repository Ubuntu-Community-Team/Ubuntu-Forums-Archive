---
title: "Live cd and file saving"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by mikemwa on 2006-03-09
Is there a way to save files etc. and do other things you would normally do while running Live CD? I'm new to this and I'm probably missing something

---

### Post by aysiu on 2006-03-09
Yes, some sort of external device (blank CD, iPod, external hard drive, floppy disk).

You can also mount your hard drive, and if it's not NTFS, you can save files there, too.

---

### Post by mikemwa on 2006-03-09
As I said I am brand new to this and not sure how to do most things. My hard drive is NTFS but I don't know what you mean by mounting it. When I try to access the cd or floppy it says it cannot mount it. I also have a thumbdrive i could use too if that would work. Is there any online or downloadable documetation for this live cd?

---

### Post by Brunellus on 2006-03-09
the thumb drive should work.

trust me, you don't want to mess with mounting your NTFS hard drive if you intend to write to it.  NTFS writing is highly experimental still under Linux--so you'd risk irrepareable filesystem harm.  (reading is OK, though).

---

### Post by aysiu on 2006-03-09
The floppy doesn't surprise me.

The CD-ROM does. I'm assuming, of course, that you have two CD-ROMs--one you're running the live CD off, and another you're trying to mount?

A thumb drive should work. Just plug it in. If everything's working well, it should appear on your desktop and open.

*Mounting* basically means *making accessible*. If you have a partition, it's not necessarily accessible. If you "mount" the partition, you're creating something like a Windows shortcut or Mac alias to the partition from a folder--so when you go to that folder, you'll see the partition.

For example, your Windows partition might be /dev/hda1. You can't just navigate to /dev/hda1, because /dev/hda1 isn't a folder--it's the device. You have to mount /dev/hda1 to a folder. So you would create a folder called /windows and then mount /dev/hda1 there. Once you do that, you can go to the /windows folder and see your Windows partition.

Unfortunately, since your Windows drive is NTFS, it will be read-only, so you can't save anything there, but if you want to mount it just to see the files, follow these instructions:
[http://www.psychocats.net/linux/mountwindows](http://www.psychocats.net/linux/mountwindows)

---

### Post by mikemwa on 2006-03-09
As long as the thumb drive will work by itself thats all i nned. I just want to be able to save some files if i run accross them while using the Live cd and then be able to transfer them when I get back into windows.
I do have 2 cdroms and I havent tried to mount it yet, it just says something like it needs to be or can't do it. This is when I try to view the floppy or cdrom drive.
Thanks a lot for the help/

---

### Post by mikemwa on 2006-03-09
OK it seems to be working with the thumbdrive. I cant download directly to it but if I open 1 window for the desktop and 1 for the thumbdrive I can drag the files to the thumbdrive.
Just a couple more questions.
Are the files going to my hard drive when I download them?
Using the live cd is there any chance od getting viruses or any bad things on my computer?
Is there anything I need to watch out for while I'm using the live cd?

---

### Post by aysiu on 2006-03-09
[QUOTE=mikemwa]
Are the files going to my hard drive when I download them?[/quote] Anything you download to your desktop (or anywhere except the thumb drive) during the live session will be gone once you reboot. The live session "saves" files and runs completely off RAM.

> 
Using the live cd is there any chance od getting viruses or any bad things on my computer? No, not unless you mount your Windows partition.

> 
Is there anything I need to watch out for while I'm using the live cd? Don't use *sudo* in front of any command you don't understand. Don't mount your Windows partition unless you know what you're doing.

---

