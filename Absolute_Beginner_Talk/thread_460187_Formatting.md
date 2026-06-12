---
title: "Formatting"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by michael08 on 2007-05-31
Ok, I messed up everything, and I can't even install XP again. I can't boot it from the cd either... all that works, it Ubuntu.

So I need to know how I can format my entire hardrive and start over.

I can't even access the hd from Ubuntu. It says Disk Read Error when I try to boot XP, and when I pick the harddrive in ubuntu, it says "Cant display all contents."

So how can I format everything? Or is that even the way to go?

---

### Post by lazyart on 2007-05-31
with the live cd you can blow everything away and reinstall-- is that what you want?

---

### Post by Inxsible on 2007-05-31
Can you post the output of 
```
sudo fdisk -l
```

-l is lowercase L

before you try and format everything ?

i think you probably installed Ubuntu over XP !!

---

### Post by Inxsible on 2007-05-31
to nuke everything put in your live cd
and go to 

System-->Administration --> GParted

---

### Post by michael08 on 2007-05-31
No, I didnt install Ubuntu over XP because the dual boot was working fine for a while... then all of a sudden, i tried it and it just stopped working.

But I probably will reinstall.

Is there a torrent program for Ubuntu?

---

### Post by Inxsible on 2007-05-31
> **michael08 said:**
> No, I didnt install Ubuntu over XP because the dual boot was working fine for a while... then all of a sudden, i tried it and it just stopped working.
 
But I probably will reinstall.
 
Is there a torrent program for Ubuntu?
 
Torrent programs :
Deluge
KTorrent

---

### Post by az on 2007-05-31
> **michael08 said:**
> 
So how can I format everything? Or is that even the way to go?

First, rule out hardware failure.

---

### Post by pappapump on 2007-05-31
IF you need to format and nothing else works then you can either use your hard drives setup CD or download freedos or any other dos based startup disk and start from there.

If you cant get to part-ed then you will have to use something like f-disk from a floppy and the command line and wipe out all existing partitions.

Also try tapping the F8 key repeatedly when you boot up to see if your PC has a bios based boot selection screen, then choose boot from CD and use the partition manager located on the LiveCD.

ONLY choose the Dos method if none of your linux options works since linux has it's own type of partition and filing system.

And last but not least, you MAY have a hardware failure with your Hard Drive, where only the non-damaged part of your physical disk is usable.

In which case, hard drive replacement is the only option.

---

### Post by michael08 on 2007-05-31
How would I know if I have a hardware failure? I didn't drop it or anything. It just stopped working. I logged out of Ubuntu, then I tried to log into XP again, and I didn't work.

Is there some sort of test to see if it is broken?

---

### Post by SteveN84 on 2007-05-31
if you have a dell, their driver cd comes with a diagnostics tool...if not, try...[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by michael08 on 2007-05-31
I do have a dell... but I don't know where any of my discs are. If I push F12 i can get to a boot menu that gives me the option

Internal Hard Drive
Cd Rom

Diagnostics
Bios something

so yeah.. diagnostics?

---

