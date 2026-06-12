---
title: "Change USB disk's label"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Kulgan on 2006-12-21
Hi!

I just reformatted a usb hard drive to ext3 for linux permissions and such, and the name that pops up on the desktop has been set to usbdisk, when it was formerly DATA. I did not edit fstab, or indeed any other file, to get it to display this. 

If possible, how would I set about changing it back to DATA? I link to it in several places, so it would be nice to have it back rather than changing all of those... 

Thanks :D
-K

---

### Post by Medieval_Creations on 2006-12-21
You can set the label when you format the drive.  I am unaware of how to change it after that, though I'm sure there is a way.

But the command would look something like this 

$ mkfs.ext3 -L DATA /dev/sda

*edit*
Oh, don't forget that you will probably have to put 'sudo' in front of that command. :)

---

### Post by Kulgan on 2006-12-21
then I have to format the whole thing again, do I?

---

### Post by Medieval_Creations on 2006-12-21
Unfortunately that's the only way I'm aware of.  That's how I changed mine.

If there is another way I haven't found it yet.

---

### Post by Kulgan on 2006-12-21
bugger, I just deleted the backup I had of it! Now I'll have to copy it over again ](*,) 

oh well, thanks :D
-K

---

### Post by christhemonkey on 2006-12-21
You can change the label on an ext2/3 filesystem with this command:
```
sudo e2label /dev/sda1 new-label 
```

Where new-label is what you want your new label to be,
and /dev/sda1 is the location of your usb stick.

Also if you install mtools you will be able to change FAT partition labels.
```
sudo apt-get install mtools 
```

For the new label:
```
sudo mlabel /dev/sda1  new_label 
```

---

### Post by Medieval_Creations on 2006-12-21
Kool... Thanks for that command.  I've never come across e2label. That's definatly a lot easier that having to reformat.

---

### Post by Kulgan on 2006-12-21
Lovely! Worked a treat :D

---

### Post by Ubuntu Joe on 2006-12-29
what's the command that tells you what devices you have plugged in . . .??

---

### Post by cendant on 2006-12-30
type

df

---

### Post by fujikofujio on 2008-02-19
Couldn't get mlabel to work then I googled it and got this page:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

adding the "::" at the beginning of the label made it work.

BTW the simplest of things that I do on windows seems to take forever in ubuntu, why can't we just press F2 to rename that darn thing.
What if I had no internet connection and couldn't install mtools ...

---

