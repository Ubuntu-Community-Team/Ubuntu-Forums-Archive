---
title: "can't copy files to usb mp3 player in gutsy"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by shikeb on 2007-11-13
Hi, I have a 1GB mp3/mp4 player which I connect to my PC, running gutsy, via USB. The device shows up alright when I connect it but when I try to copy files to it, I get an error message that I dont have permissions to write. It used to work with Feisty. Any clue??

Thanks.

---

### Post by Inxsible on 2007-11-13
you need to assume ownership of the mount point
```
sudo chown -R *your-username:your-group* /path/to/mount/point
```

---

### Post by philinux on 2007-11-13
> **shikeb said:**
> Hi, I have a 1GB mp3/mp4 player which I connect to my PC, running gutsy, via USB. The device shows up alright when I connect it but when I try to copy files to it, I get an error message that I dont have permissions to write. It used to work with Feisty. Any clue??

Thanks.

In a terminal just type gksudo nautilus and then use the root browser to copy your files.

---

### Post by Inxsible on 2007-11-13
> **philinux said:**
> In a terminal just type gksudo nautilus and then use the root browser to copy your files.
That would not be very safe. You can do a lot of harm when you assume the root role, especially, if you are new to Linux.

---

### Post by philinux on 2007-11-13
Yes but permissions only work on ext format drives.

---

### Post by shikeb on 2007-11-13
I tried both ways but it doesn't seem to be working. chown says 
```
chown: changing ownership of path/to/file read-only file system
```

---

### Post by timcredible on 2007-11-13
what mp3 player is it?

---

### Post by philinux on 2007-11-13
when its mounted and the icon is on your desktop, right click on it and select properties. Then select the tab labelled permissions and see if you can change any to read/write.

---

### Post by shikeb on 2007-11-13
It's some chinese thingy, and I am also not able to change to permissions using the right click menu.

---

### Post by steve.horsley on 2007-11-13
Type **mount** and see if it has been mounted read-only. 

If it has (and it sounds like it has), I have no idea what to do about it, but at least you know why. You can start debugging the mount process, or manuallu unmount it and remount it rw.

---

### Post by philinux on 2007-11-13
With the device plugged in have a look in the /media folder and see what the system calls it. Maybe print screen and include it in your next post.

you will then need a command like this

sudo chown yourusername /media/whattheplayeriscalled

---

### Post by nynoah on 2007-11-13
I have had the same problem too.  I found the easiest thing is to  just hit ALT-F2 and then type gksudo nautilus.  But make sure you do nothing else with Sudo Nautilus because it is like playing with fire.  Just do what you have to do copying files or deleting files on that drive and then exit Sudo Nautilus.  This makes every command you do in Nautilus as root, so you are at risk of doing the wrong thing with no recovery.   So just deal with the MP3 files and backups and that alone.

Hope that helps

---

