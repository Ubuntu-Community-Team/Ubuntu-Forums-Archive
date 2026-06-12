---
title: "[SOLVED] Boot problems with ubuntu / windows"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jppk143 on 2007-11-21
Completly new to Ubuntu but used windows for years.

I have a laptop with a 120GB hard drive and i decided to partition 20gb for for Ubuntu just so i could test it out.  Ubuntu works fine and everything BUT I cant boot to the other 100GB of my hard drive with Windows Vista on it.  Not that its a huge problem if I lost all my data on Windows but there are a few files and things that i would like to retrieve.  The version of ubuntu is 7.10.  

Im a complete NOOB to ubuntu so im sorry if this question has been answered 1000 times but is there anyway i can access the other 100gb of my hard drive or boot to to windows from startup...any help or tips would be great.
Thanks

---

### Post by overdrank on 2007-11-21
> **jppk143 said:**
> Completly new to Ubuntu but used windows for years.

I have a laptop with a 120GB hard drive and i decided to partition 20gb for for Ubuntu just so i could test it out.  Ubuntu works fine and everything BUT I cant boot to the other 100GB of my hard drive with Windows Vista on it.  Not that its a huge problem if I lost all my data on Windows but there are a few files and things that i would like to retrieve.  The version of ubuntu is 7.10.  

Im a complete NOOB to ubuntu so im sorry if this question has been answered 1000 times but is there anyway i can access the other 100gb of my hard drive or boot to to windows from startup...any help or tips would be great.
Thanks

HI does the grub give you the options to boot to windows or does is boot straight to ubuntu?

---

### Post by jppk143 on 2007-11-21
when i turn on the laptop i get 4 boot options

1.Ubuntu
2.Other Operating systems
3.Dell Utility Partition
4.Microsoft Windows XP embedded


when i choose *2.Other Operating systems *and *4.Microsoft Windows XP embedded *nothing happens

The dell thing is just a system test and ubuntu works fine.

any ideas?

---

### Post by meierfra on 2007-11-21
open a terminal (Applications->Accessories->Terminal)

and type 

```

sudo fdisk -l

cat /boot/grub/menu/lst

```
(both l are lower case L, not the number 1)

copy the content of the terminal and post it here.

---

### Post by jppk143 on 2007-11-22
Cheers

No worries...i just formatted my hard drive and put Ubuntu on..its working fine..I'l prob install windows in the next couple of days or so.But thanks for the quick help guys.

---

### Post by overdrank on 2007-11-22
> **jppk143 said:**
> Cheers

No worries...i just formatted my hard drive and put Ubuntu on..its working fine..I'l prob install windows in the next couple of days or so.But thanks for the quick help guys.

HI when you install window you will have to reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Glad you have it working now and please mark the thread a solved under thread tools. :)

---

