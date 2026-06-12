---
title: "Error 25. hard disk damage??"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by kaplis on 2006-10-12
hey!

GRUB loading. please wait...
Error 25
(and including strange noises from box)

whats that? does my hard disk is dead??](*,)

---

### Post by whizbaby on 2006-10-12
How old it? Is it recognized by the BIOS?
Is very important data on it?
If not, can you see it from livecd?

---

### Post by Endwin on 2006-10-12
Well if it is making strange noises it is possible. If you download, and burn the [Ultimate Boot CD Basic]("http://www.ultimatebootcd.com/download.html") you can run a test on your hardrive to see if it is failing, and maybe fix it if there is nothing majorly wrong with it.

---

### Post by petri on 2006-10-12
I don't think so: 
```
Error 25 : "Unrecognized command"

This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a config file and that entry is selected.
```

You can boot with LiveCD? Do it and post your ```
sudo fdisk -l
``` and ```
gedit /boot/grub/menu.lst
```

Hm, you do have to mount the partition and adjust the command to that.


EDIT: typo :rolleyes:

---

### Post by whizbaby on 2006-10-12
> **petri said:**
> gedit /boot/grub/menau.lst
Typo!
gedit /boot/grub/**menu**.lst
(your finger has to be quite big for that one...;) )

---

### Post by petri on 2006-10-12
> **whizbaby said:**
> Typo!
gedit /boot/grub/**menu**.lst
(your finger has to be quite big for that one...;) )

No, I have beatifull thin long fingers.... No, I'm just a Finn living in Sweden and writing in English while thinking about last weekends trip to Paris... :mrgreen:

---

### Post by encompass on 2006-10-12
I had the same problem... ends up I could mount the drive be eventually I heard a lound bang where the HD is and then it would freeze.  Hope your problem isn't EXACTLY like mine.  I am getting the drive fixed under wauranty.

---

### Post by bulldog on 2006-10-12
According to to this link the fault should be,```
25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 
```

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

---

### Post by petri on 2006-10-12
> **encompass said:**
> I had the same problem... ends up I could mount the drive be eventually I heard a lound bang where the HD is and then it would freeze. Hope your problem isn't EXACTLY like mine. I am getting the drive fixed under wauranty.
> **bulldog said:**
> According to to this link the fault should be,```
25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 
```

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

Autsch, well I hope I'm right. :rolleyes: :(

---

### Post by whizbaby on 2006-10-12
> **petri said:**
> No, I have beatifull thin long fingers.... No, I'm just a Finn living in Sweden and writing in English while thinking about last weekends trip to Paris... :mrgreen:
Try meneaux.list ,then.
EDIT:
BTW where is kaplis?

---

### Post by bulldog on 2006-10-12
I should try to mount the disk like someone  allready said,with the live cd.

Then try to mount the disk and copy my data to another disk.

I hope I'm wrong but the chance your disk is gonna die is eminent.

You can run a diagnostic tool which you can download from the website of the manufacturer.

---

