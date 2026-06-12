---
title: "Can't resize partitions?!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Morsolo on 2007-06-12
Hello,
I've got the Linux LiveCD (Ubuntu 7.04) running, I'm using it right now...
All seems well and good, systems runs fine, HOWEVER!

I cannot install Ubuntu due to the tiny fact that I CANT RESIZE MY PARTITIONS!
This is what pop's up in the Installation:
> /dev/sda1 (fat32) /media/sda1 [Size: 1998 MB | Used: 1600 MB]
/dev/sda2 (ntfs) /media/sda2 [Size: 52427 MB | Used: 31500 MB]
/dev/sda5 (ntfs) /media/sda5 [Size: 65604 MB | Used: 51200 MB]
[I][B]SDA1 is the recovery hidden directory thing...
SDA2 is for my Windows XP
SDA5 is for my Windows Vista[/B][/I]

Obviously, that isn't exactly what it says, I just made it easier to read...

When I try to RESIZE sda2 (my XP partition) from 52427 to 42427...I get an error, and I can't continue...
So, I use my Boot CD of GNOME Partition editor...

I get this...Or along the lines of...
> Cannot Shrink partition /dev/sda2 to 42427, error 1052 > 1024 not supported...
Try freeing less space
I try to shrink by 1000mb, 100mb, or 10mb, even 1mb... I still get the damn error!

Any ideas?

---

### Post by foxmulder881 on 2007-06-12
Have you tried the GParted LiveCD? I find it just works better than running GParted of the Ubuntu LiveCD.

---

### Post by drowner on 2007-06-12
Try defragmenting your windows drives, about 20 times, bfore you start.

That worked for me

---

### Post by Morsolo on 2007-06-12
GParted is GNOME Partition Editor

**_G_**nome **_Part_**ition **_Ed_**itor
I don't think that's how the name came aorund, but you get the idea...

Also, I'm not sure if this is related, but on the LiveCD (Which I'm still on) if I go "Computer" and select my VISTA or XP drives, it says:
> Vista selected: 0 bytes
or
XP selected: 0 bytes
I need some help as I really want to do this...

Can I defrag the drives while still on the livecd?

**EDIT:**
Oh sorry foxmulder, if you meant I should run it off it's own CD rather than from the LiveCD, that is what I have done...
... Oops...

---

### Post by foxmulder881 on 2007-06-13
Yes I know that GParted is GNOME Partition Editor.

Difference is GParted LiveCD runs entirely from RAM. I'm not so sure that the Ubuntu LiveCD runs entirely from RAM. I think it uses some hard drive space, therefore interfering with some Partition Editor operations.

---

### Post by Morsolo on 2007-06-13
Yeah, sorry about that Fox...

I know, I've tried both GParted's...LiveCD and it's own Boot Disc...Both return errors...
I've gotten it to work though, no idea why it started working, I didn't do anything...

Anyway, it's installing, I just hope I did everything correctly and it doesn't go and re-format my C or D drive...

---

