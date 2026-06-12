---
title: "MP3 Player Troubles"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by justinlb on 2006-11-09
I have a Medion MDJUKE220 MP3 player and I can't mount it properley. Whenever I plug it in the computer recognizes it and I can view the files on it but I can't copy any on, I also can't dismount it properley and I think I have an idea what the problem is but I have no idea how to change. The MP3 player says USB 2.0 MSD when it is mounted but on the computer it says MTC, I have no idea what this means but I hope someone can help me.

---

### Post by Ecthelion on 2006-11-09
What kind of partition is there on your disk?

You can try to write to is as root...
```
sudo nautilus
```
Then go to your disk and try to write....

What kind of error does it give when you try to write to it?

---

### Post by justinlb on 2006-11-09
It worked for transfering songs onto there and deleting them, so thanks alot for that, but I've still got the problem of it not dismounting properley.

---

### Post by 3rdalbum on 2006-11-09
Okay. Open up Nautilus, and move to the /media directory. You'll see some directories there, which correspond to the possible disk drives. One of them will "contain" your MP3 player's contents. Find which one it is (it's probably /media/usbdisk)

So you would do:

```
sudo umount /media/usbdisk
```

You didn't mention if you get an error when unmounting. If it just seems to be "writing data to the device" for ages when you select Eject, then that's because it's still writing your files to the MP3 player in the background. If you get an error message like "Unmount failed - device is busy", and you can't figure out what program is still using the disk, then try the following in a terminal (after saving all open documents):

```
fuser -k /media/usbdisk
```

That kills all programs that are using the disk, allowing you to unmount it.

---

