---
title: "Ubuntu is not user friendly? Dual Boot Problem"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by synergy99 on 2007-05-15
Partition 1:  XP NTFS 25gigs
Partition 2: DATA NTFS 200 gigs
Partition 3: Ubuntu 
Partition 4: Ubuntu swap

I've successfully installed Ubuntu from the LiveCD onto my 3rd and 4th partition. I'm trying to keep my XP system and partitions 1 and 2 unaffected. I think its installed properly, but theres no way for me to check because it wont boot into Ubuntu off the hard drive.. it goes straight to XP.  Clearly I need a bootstrap program or to edit my boot.ini file or whatever the Linux equivalent is...

So i start googling and all I can find is GRUB... So I've downloaded grub and I'm trying to compile the thing but it wont work. Compile error. 

Do I seriously need to be dealing with this crap? Is there a version of Linux that is friendly to dual boot noobs and has this stuff built in? Forcing me to deal with GRUB on my first day... boooo.... 

Is there a better way?

---

### Post by Billy McCann on 2007-05-15
Better way = re-install GRUB to your MBR using the LiveCD.  

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by synergy99 on 2007-05-15
> **Billy McCann said:**
> Better way = re-install GRUB to your MBR using the LiveCD.  

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

When I do sudo grub, then find /boot/grub/stagel it says Error 15: File Not Found

Maybe I missed something during install and it skipped GRUB? I didnt see anything about GRUB or the MBR when I was installing. By the way I am using _Kubuntu_, perhaps this version is different?

---

### Post by overdrank on 2007-05-15
> **synergy99 said:**
> Partition 1:  XP NTFS 25gigs
Partition 2: DATA NTFS 200 gigs
Partition 3: Ubuntu 
Partition 4: Ubuntu swap

I've successfully installed Ubuntu from the LiveCD onto my 3rd and 4th partition. I'm trying to keep my XP system and partitions 1 and 2 unaffected. I think its installed properly, but theres no way for me to check because it wont boot into Ubuntu off the hard drive.. it goes straight to XP.  Clearly I need a bootstrap program or to edit my boot.ini file or whatever the Linux equivalent is...

So i start googling and all I can find is GRUB... So I've downloaded grub and I'm trying to compile the thing but it wont work. Compile error. 

Do I seriously need to be dealing with this crap? Is there a version of Linux that is friendly to dual boot noobs and has this stuff built in? Forcing me to deal with GRUB on my first day... boooo.... 

Is there a better way?


Hi and welcome, I am assuming that you did not install the grub during installation so the previous post should help you. Good luck and again welcome and keep the boos down to a minimum until you have tried ubuntu for a little longer! Thanks ;)
And Kubuntu would be the same on the grub except for the fact of KDE.

---

### Post by bobplano on 2007-05-15
it looks like in your post that you typed in an L or capital i. it looks like in the link its a one, for stage1(one)

---

### Post by overdrank on 2007-05-15
> **bobplano said:**
> it looks like in your post that you typed in an L or capital i. it looks like in the link its a one, for stage1(one)

Great catch !!!!!=D>

---

### Post by Billy McCann on 2007-05-15
> **synergy99 said:**
> When I do sudo grub, then find /boot/grub/stagel it says Error 15: File Not Found
stagel or stage1? 

It's a "one", not an "el".  Just copy and paste to be sure.  :) 

Oh yeah.  Welcome to Ubuntu.  The cool thing about ubuntu is the support group.  You can also try the Ubuntu IRC chat.  The folks there are always helpful.

---

