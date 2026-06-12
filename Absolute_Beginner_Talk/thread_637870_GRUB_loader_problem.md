---
title: "GRUB loader problem"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by coltman90 on 2007-12-11
I installed Ubuntu a little while back when I tried to dual boot vista and xp and it didnt go so well, so i found out that it came with a bootloader hoping it would allow me to boot into windows again, and it did, its been working fine but lately when i restart the computer it brings up a screen 

GRUB loading stage 1.5
please wait...              
or something simliar to that, i have waited over 10 mintues on a few occasions but eventually just shut it down and try again.  Eventually after a few tries it does work and goes to the GRUB loader like normal... this is pretty annoying though so anyway to fix it? reinstall grub...? thanks

---

### Post by Don1500 on 2007-12-11
> **coltman90 said:**
>  reinstall grub...? thanks


That would be a good place to start.
Let us know what happens then.

---

### Post by coltman90 on 2007-12-11
how exactly would i do that? just put in the original ubuntu cd?

---

### Post by Don1500 on 2007-12-11
Use your ubuntu live cd to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by conehead77 on 2007-12-11
I googled your error message and it seems that it is probably a hardware issue. There are some solutions though like switching a bios entry or check the cables on the hd.

If reinstalling grub doesnt solve your problem take a look at these links:
[http://forums.gentoo.org/viewtopic.php?p=586004](http://forums.gentoo.org/viewtopic.php?p=586004)
[http://www.ocforums.com/archive/index.php/t-508788.html](http://www.ocforums.com/archive/index.php/t-508788.html)
[http://ubuntuforums.org/archive/index.php/t-8499.html](http://ubuntuforums.org/archive/index.php/t-8499.html)

Somebody with the same error also found that he had a corrupt partition. Good luck!

---

### Post by coltman90 on 2007-12-11
I'll try it, im just afraid im gonna mess something up. I have ubuntu installed to a partition so would i want to write GRUB to the MBR or to the partition?

---

### Post by ronmarley1 on 2007-12-11
Another option to restore GRUB is the SuperGrubDisk.  You can download the iso here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
It has helped me a few times.

---

### Post by coltman90 on 2007-12-11
> **conehead77 said:**
> I googled your error message and it seems that it is probably a hardware issue. There are some solutions though like switching a bios entry or check the cables on the hd.

If reinstalling grub doesnt solve your problem take a look at these links:
[http://forums.gentoo.org/viewtopic.php?p=586004](http://forums.gentoo.org/viewtopic.php?p=586004)
[http://www.ocforums.com/archive/index.php/t-508788.html](http://www.ocforums.com/archive/index.php/t-508788.html)
[http://ubuntuforums.org/archive/index.php/t-8499.html](http://ubuntuforums.org/archive/index.php/t-8499.html)

Somebody with the same error also found that he had a corrupt partition. Good luck!

alright i'll check those out too, and corrupt partition? great... lol

---

### Post by OffAxis on 2007-12-11
To run a check on the hard drive boot from the live cd and
```
e2fsck /dev/hda1
```

---

### Post by coltman90 on 2007-12-11
ok i burned supergrubdisk iso file to a blank disc, booted from it, but it said loading stage 2.... and would just sit there, so i decided i would just reinstall the entire ubuntu on the same partition it was on now because there is nothing on that partition that i would want to keep. So i did that and went through the entire install process and such. Once I rebooted it went to the grub loader on the first try, but the next time I rebooted it did the same thing as before, so I'm guessing it must be a hardware issue. Ill look at those link's from earlier see if i can find anything out.

---

### Post by coltman90 on 2007-12-18
well its working now, just all the sudden everytime i boot it goes to the grub loader which is good. another question i have is about triple booting. would it be possible to have the option to boot ubuntu, windows home basic 32bit and windows ultimate 64bit. If i were to make a new partition and install 64bit windows on that would the grub loader automatically recognize that or would i have to make a new entry in the .lst file or w/e it is.

---

### Post by Duck2006 on 2007-12-18
> **coltman90 said:**
> well its working now, just all the sudden everytime i boot it goes to the grub loader which is good. another question i have is about triple booting. would it be possible to have the option to boot ubuntu, windows home basic 32bit and windows ultimate 64bit. If i were to make a new partition and install 64bit windows on that would the grub loader automatically recognize that or would i have to make a new entry in the .lst file or w/e it is.

No you would have to reinstall grub.

---

### Post by coltman90 on 2007-12-18
Ok i see. If i were to install 64bit though, once it was installed would it overwrite the mbr no longer booting into grub?

---

### Post by Duck2006 on 2007-12-18
> **coltman90 said:**
> Ok i see. If i were to install 64bit though, once it was installed would it overwrite the mbr no longer booting into grub?

Yes it would, so you would have to reinstall grub, and add the new windoze line  to it so you can boot to it.

---

