---
title: "External Hard Drive"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Zelaznog on 2007-06-02
Hi, I'm really new at this. I just installed Ubuntu in my external HD but now I can't be starting anything without having the HD connected to my laptop, so I have to start the laptop with the external HD, start windows and then take the HD out... it tells something about a GRUB error... is there anyway to install UBUNTU in the external HD and when it is not connected the laptop won't mind and start Windows normally?

Thanks...

---

### Post by Inxsible on 2007-06-02
Thats because when you install Ubuntu, it also installs a Grub, which lets you select which OS to boot into, if you have multiple OSes installed. This is done prior to loading an OS of course. 

Since you installed Ubuntu on an external disk, the grub is also installed on that external disk. So your disk needs to be connected for the grub to show up.
There are ways to overwrite the grub with mbr again and then use UBuntu only when your external is connected, but I have never done it.

search the forums. I am sure you will find something

---

### Post by ugm6hr on 2007-06-02
A similar problem - with possible solutions
[http://ubuntuforums.org/showthread.php?t=459408](http://ubuntuforums.org/showthread.php?t=459408)

There are other options out there too.  But at least you will know what to search for.

---

