---
title: "i shot my filesystem!"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by leader303 on 2008-04-08
(but i did not shoot the deputy)

impatiently, i cancelled some partition resizing stuff in gparted and now, what surprise, ubuntu won't boot due to inconsistent file system structure.

what can i do about it? is there some tool to repair it?

---

### Post by tamoneya on 2008-04-08
well it depends how badly you shot it.  Lets take a look at your disks with fdisk
```
sudo fdisk /dev/sda
p
```

This will all have to be done using the liveCD obviously since you cant boot ubuntu.  This is assuming that your harddrive is /dev/sda

---

### Post by Joeb454 on 2008-04-08
Just to help, from what I know

```
/dev/sda
``` is for SATA Drives
```
/dev/hda
``` is for PATA (IDE) Drives :)

Hope this helps :)

---

### Post by ShodanjoDM on 2008-04-08
Since he's using 7.10, both PATA and SATA drives are called /dev/sd*

---

### Post by Joeb454 on 2008-04-08
You know I've never ever noticed that before :)

---

### Post by ShodanjoDM on 2008-04-08
> **Joeb454 said:**
> You know I've never ever noticed that before :)

Yeah, it's quite confusing for me too :D I forgot when the changes were implemented. I think it was since 7.04 but I'm not so sure.

---

### Post by fela on 2008-04-08
> **Joeb454 said:**
> Just to help, from what I know

```
/dev/sda
``` is for SATA Drives
```
/dev/hda
``` is for PATA (IDE) Drives :)

Hope this helps :)

I have a IDE drive but it's at /dev/sda. I heard that /dev/sd* was for SCSI disks, and /dev/hd* was for IDE/ATA disks. So Linux must be reading my disk as SCSI?

---

### Post by Joeb454 on 2008-04-08
No - like was mentioned above, all of my disks appear to be read as /dev/sda however they are not SCSI drives, so it should read it as /dev/sda (I was thinking of the old way ;))

---

### Post by leader303 on 2008-05-30
so i'm back to the abandoned thread...

the concerned partition is called /dev/hda5. (i was just checking, this time i think i didn't destroy anything;) testdisk can't find any superblocks in that partition. tried running fsck, didn't run a complete check (but i can't remember the commands i used... if you know useful ones, hook me up!)

thanks for the replies so far!

---

