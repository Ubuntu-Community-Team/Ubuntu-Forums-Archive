---
title: "how to  partitions for 2 distro's"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by brash_vs on 2007-11-12
how should i partition my 40g hd for 2 distro's i've been using mainly ubuntu and just dl another distro (fedora). i would like to dual boot. its ok to wipe everything coz i have to upgrade anyway so not a problem. 
here is what i thought will it work, will i need two of everything except swap?
/ 8 gig
/home 10 gig
/swap 1 gig
be easy to understand coz i am a BEGINNER.

---

### Post by kellemes on 2007-11-12
> **brash_vs said:**
> how should i partition my 40g hd for 2 distro's i've been using mainly ubuntu and just dl another distro (fedora). i would like to dual boot. its ok to wipe everything coz i have to upgrade anyway so not a problem. 
here is what i thought will it work, will i need two of everything except swap?
/ 8 gig
/home 10 gig
/swap 1 gig
be easy to understand coz i am a BEGINNER.

There are a million options, but this is one..

1 swap-partition (2x memory with a maximum of 2Gb) .. both dists will use this swap.
2 /(root)-partitions (one for each dist)
2 /home-partitions (one for each dist)
2 /boot-partitions (one for each dist) .. about 500 Mb

If you make the /-partitions about 8 (as you wish) that's fine.. you can devide the rest between the /home-partitions, /boot and swap.

---

### Post by mikewhatever on 2007-11-12
That should work. I think you are right about sharing swap and **not** home sharing /home.

---

### Post by kellemes on 2007-11-12
> **mikewhatever said:**
> That should work. I think you are right about sharing swap and home sharing /home.

Maybe I misunderstand but I would not share /home
unless.. you use unique usernames for each distro.
I would just separate the lot.

---

### Post by brash_vs on 2007-11-12
if i name each of the partitions the same how will the 2 os know which one to use? 
do i just insert is cd and format the whole disk to start. 
then tell ubuntu  what partitions to make
then when its all done installing
insert the other cd (fedora) and tell it which partitions to use and let it install itself.

---

### Post by rsambuca on 2007-11-12
> **kellemes said:**
> There are a million options, but this is one..

1 swap-partition (2x memory with a maximum of 2Gb) .. both dists will use this swap.
2 /(root)-partitions (one for each dist)
2 /home-partitions (one for each dist)
2 /boot-partitions (one for each dist) .. about 500 Mb

If you make the /-partitions about 8 (as you wish) that's fine.. you can devide the rest between the /home-partitions, /boot and swap.

You definitely do not need two /boot partitions.  Total waste.

---

### Post by kellemes on 2007-11-12
> **rsambuca said:**
> You definitely do not need two /boot partitions.  Total waste.

It really depends on how you want to setup your bootloader..
I have my Grub bootloader setup on dist-1 pointing to the Grub-setup (menu.lst) on dist-2.
This way you can configure Grub on dist-2 without having to configure your active Grub on dist-1.
I don't want dist-2 to touch my Grub-setup! And so I use nesting menu's..
Like I said, there are other options but this is the easiest and safest..

---

### Post by Duck2006 on 2007-11-12
I would load fedora first and ubuntu second and let ubuntu's grub loader load for both.
partition the drive for two / root and one swap and if you like one home, but use two different users names.

---

### Post by rsambuca on 2007-11-12
> **kellemes said:**
> It really depends on how you want to setup your bootloader..
I have my Grub bootloader setup on dist-1 pointing to the Grub-setup (menu.lst) on dist-2.
This way you can configure Grub on dist-2 without having to configure your active Grub on dist-1.
I don't want dist-2 to touch my Grub-setup! And so I use nesting menu's..
Like I said, there are other options but this is the easiest and safest..

I do that too, but you don't need separate partitions for that!

---

### Post by kellemes on 2007-11-12
> **rsambuca said:**
> I do that too, but you don't need separate partitions for that!

I stand corrected..
The question may be if you want a /boot-partition at all.. that discussion is never ending :popcorn:
There are situation you may want to.. but for the average user it is not be useful anymore.
I just happen to be a sucker for this..

Indeed it doesn't matter for this particular setup since from Grub you can simply point to (hd*,*)/boot/grub/menu.lst instead of (hd*,*)/grub/menu.lst

---

### Post by mikewhatever on 2007-11-12
> **kellemes said:**
> Maybe I misunderstand but I would not share /home
unless.. you use unique usernames for each distro.
I would just separate the lot.

Typing mistake, sorry. Edited in my original post.

---

