---
title: "Undoing USB Stick"
date: 2012-07-23
forum: Apple Hardware Users
---

### Post by 15tigers on 2012-07-23
So I recently put ubuntu onto my 1TB hard drive which also had my time machine backups and other files on it. I didn't know putting ubuntu onto this hard drive would erase everything else and make the drive unreadable to my computer. Is there anyway to revert my hard drive to how it was before?

---

### Post by na5h on 2012-07-23
You "put Ubuntu onto the hard-drive"? Could you give some more details on how you did this? Did you install it onto the hard-drive or were you attempting to make a bootable USB-stick?

---

### Post by 15tigers on 2012-07-23
Yes I was trying to make a bootable "USB stick" using my hard drive.

---

### Post by 2blue on 2012-07-23
lost data is lost I suppose, but you could always delete it and reformat to what ever filesystem you had. If you installed to a partition on the usb harddrive, it might be worth reading the usb harddrive from a running linux system. I know Windows often doesn`t read anything where ext4 is involved, I`m not sure about osx in general.

---

### Post by na5h on 2012-07-23
Data can be recovered from a hard-drive that has been formatted...it is very important that you DO NOT WRITE to the hard-drive as this may overwrite data that could otherwise have been recovered!

Edit: What operating system are you using (Windows, Ubuntu, Mac)?

---

### Post by 15tigers on 2012-07-23
And how do i do this? I'm using mac btw.

---

### Post by na5h on 2012-07-24
[QUOTE=15tigers]Hi, can you please explain what you mean by formatting my drive and recovering the data? I've read about formatting it but no one else has mentioned recovering my old data.

[http://ubuntuforums.org/showthread.php?p=12125579&posted=1#post12125579](http://ubuntuforums.org/showthread.php?p=12125579&posted=1#post12125579)[/QUOTE]

I'll reply to your private message here so that others may be able to help you as well.

When you copied Ubuntu onto the hard-drive, it might have been formatted (in other words, the program you used to create a bootable USB-stick erased the contents of your hard-drive and replaced it with Ubuntu). Even if the hard-drive has been formatted, it might still be possible to recover the old files.

Hopefully, the program you used to "copy" Ubuntu onto the hard-drive didn't erase the old contents of the hard-drive, but rather create a new partition for the new data.

I'm not too knowledgeable about file recovery, especially not on Mac, but I will try to get back to you with some answers...perhaps someone else has got a suggestion?

---

### Post by na5h on 2012-07-24
I managed to find a few links on the subject...I haven't read through them thoroughly though...

View information about partitions and volumes:
[http://www.dummies.com/how-to/content/how-to-view-information-about-partitions-and-volum.html](http://www.dummies.com/how-to/content/how-to-view-information-about-partitions-and-volum.html)

File recovery from unmounted volumes (not free software, but it has a demo mode so that you can see whether it is working or not):
[http://www.mac-file-recovery.net/unmounted-mac-volumes.html](http://www.mac-file-recovery.net/unmounted-mac-volumes.html)

Recover files from an external hard drive (not sure if free or not):
[http://www.applexsoft.com/howto/recover-files-from-external-hard-drive.html](http://www.applexsoft.com/howto/recover-files-from-external-hard-drive.html)

---

