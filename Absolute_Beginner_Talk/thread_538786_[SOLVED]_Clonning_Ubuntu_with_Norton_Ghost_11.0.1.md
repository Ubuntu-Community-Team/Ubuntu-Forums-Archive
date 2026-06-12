---
title: "[SOLVED] Clonning Ubuntu with Norton Ghost 11.0.1?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-08-30
I'm testing Ubuntu to install in 30 machines.
I've just finished one, and I wanted to duplicate it on a cd with norton ghost 11.0.1. All other PC's are exactly the same one,  

But once another PC is cloned, doesn't boot showing  GRUB 15 error.

What can I do?
There is any other program witch I can use to easily clone one HDD to a CD or DVD and then copy to the others?

Norton Ghost doesn't works at all with linux? 

Thank you guys

---

### Post by Hobo Joe on 2007-08-30
Why don't you just use the Live CD and install it on all of them?

---

### Post by julian67 on 2007-08-30
> **Kosimo said:**
> I'm testing Ubuntu to install in 30 machines.
I've just finished one, and I wanted to duplicate it on a cd with norton ghost 11.0.1. All other PC's are exactly the same one,  

But once another PC is cloned, doesn't boot showing  GRUB 15 error.

What can I do?
There is any other program witch I can use to easily clone one HDD to a CD or DVD and then copy to the others?

Norton Ghost doesn't works at all with linux? 

Thank you guys

The program you need is [Clonezilla]("http://clonezilla.sourceforge.net/")


> About Clonezilla

    You're probably familiar with the popular proprietary commercial package Norton Ghost®, and its OpenSource counterpart, Partition Image. The problem with these software packages is that it takes a lot of time to massively clone systems to many computers. You've probably also heard of Symantec's solution to this problem, Symantec Ghost Corporate Edition® with multicasting. Well, now there is an OpenSource clone system (OCS) solution called Clonezilla with unicasting and multicasting! With DRBL and network boot enabled client computers, the only thing you have to prepare is a Clonezilla server. You do not even have to prepare a bootable CD or floppy with Partition Image for every client computer.

    Clonezilla, based on DRBL, Partition Image, ntfsclone, and udpcast, allows you can massively clone many (40 plus!) computers simultaneously. Unlike G4U (Ghost for Unix) or G4L (Ghost for Linux), Clonezilla saves and restores only used blocks in the harddisk. This increases the clone effiency. At the NCHC's Classroom C, Clonezilla was used to clone 41 computers simultaneously. It took about 50 minutes to clone a 5.6 GBytes system image to all 41 computers via unicasting and only about 10 minutes via multicasting!


---

### Post by Kosimo on 2007-08-30
> **Hobo Joe said:**
> Why don't you just use the Live CD and install it on all of them?

Cuz I had to tweak lots of things, install other programs, updating etc...

So, I can't spend all this time for each machine.

That's why I just want a clone CD, to boot the computer from it and just copy all the information. All computers are exactly the same one. So, once you just tweak one like you want then the others can be just duplicated.

---

### Post by Kosimo on 2007-08-30
> **julian67 said:**
> The program you need is [Clonezilla]("http://clonezilla.sourceforge.net/")

Cooool!!

That's exactly what I need :)
Thank you mate.

---

