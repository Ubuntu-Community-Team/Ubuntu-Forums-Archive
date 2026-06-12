---
title: "disk mount issue"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-07-19
so have this problem with my dvd drive. I often forget to eject/unmount it, and just push the button on the drive (a habit i'm trying to break). when i do this, the disk still seems to be mounted. so, i unmount it, then try to put in a new disk. ubuntu refuses to mount or read the disk. when i try mounting it, the image of PREVIOUS disk shows up, and it's unreadable.

the only way i've found to fix this is to reboot.

any ideas?

---

### Post by sailor2001 on 2007-07-19
behave yourself..........you can lose data by trying to eject before being unmounted

---

### Post by colddayinapril on 2007-07-19
I'm aware of that sailor,and i never make the mistake with any other media - thumb drive, backup hardrive, est... just dvd's. And, like i said, i'm ttying hard to get used to not just hiting eject, but the buttons right there in front of me, and after years of working with windows, it's like getting pavlovs dogs not to spit when they hear a bell.

I am working on reconditioning myself, but untill then, is there anyone able to answere my actual question?


I'll tell you what, i'li rephrase my question in self depreciating fasion, so as not to invite further condesention:

After I royaly f*%k up and, like a windows using idiot, hit the button to eject my dvd, how do i fix the issues that arise there after?

---

### Post by koganinja89 on 2007-07-19
Gnome should automaticly unmount it for you but if it doesn't just try to break the habbit and if you do it not on perpose restart you machine.

---

### Post by deadlikeoscar on 2007-07-19
Open a terminal and type 
```
sudo umount /media/cdrom0
``` (assuming this is your drive)

Put the new disc in and close the drive. It may automount, if not:

```
sudo mount /media/cdrom0/ -o unhide
```

---

### Post by colddayinapril on 2007-07-19
i tryed that dead, but without the "-o unhide"... you think that's the problem?
what exactly dose that do?

---

### Post by davidjmayo on 2007-07-20
> **colddayinapril said:**
> i tryed that dead, but without the "-o unhide"... you think that's the problem?
what exactly dose that do?

for your future reference 

```
man commandname
```

man is for the manual and shows everything possible.

so in your case 
```
man mount
```

-o is options
>  unhide Also  show  hidden and associated files.  (If the ordinary files
              and the associated or hidden files have the same filenames, this
              may make the ordinary files inaccessible.)



in your case start at line 754 which is for CD  unhide is at line 780-784 (use page down to get here)
you can see the line number at the bottom of the terminal. As you can see man tends to be very long.

---

