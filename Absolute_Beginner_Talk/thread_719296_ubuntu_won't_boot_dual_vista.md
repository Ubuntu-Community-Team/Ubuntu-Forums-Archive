---
title: "ubuntu won't boot dual vista"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by THe.Conundrum on 2008-03-09
i've tried to install ubuntu about 10 times now. tried 7.10 and the new 8.05 and i keep getting this error when i boot up and select it using the windows boot manager. vista boots fine but not ubuntu. i have 4 hard drives and i think that might be part of the problem. i've tried it so many ways and keep getting this error not sure where to go from here. when i do the grub in the advanced i set it to (hd4,2) as the partition is on dev/sdd2 i recently tried booting the live cd and installing grub with the terminal and that didn't work either same error when i tried to boot. also when i did "find /boot/grub/stage1" from the live cd it told me it was on (hd2,1) or something that wasn't 4,2 so i tried to do root with that hd and partition and it seemed to work but still i get the same error. vista was already installed. i've tried easybcd and it didn't work for me.


Bootpart 2.60 Boot sector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
loading new partition
bootsector from C.H. Hochstatter
Cannot load from hard disk
insert systemdisk and press anykey

(when i push a key)
GRUB GRUB

and then it restarts, all of this is displayed in dos

---

### Post by logos34 on 2008-03-09
> **THe.Conundrum said:**
> when i do the grub in the advanced i set it to (hd4,2) as the partition is on dev/sdd2...i did "find /boot/grub/stage1" from the live cd it told me it was on (hd2,1) 

You made a common mistake--grub starts counting from zero.  So if you have 4 drives there's no '(hd4)'...it's either hd0, hd1, hd2, hd3.

If it's the second partition (sdd2), then the find command sounds right--(hd2,1)--meaning third hard drive in Bios boot order, second partition.

Try reinstalling once more but this time get the grub location right...Use either (hdx,1), or easier still **/dev/sdd2**.  With the latter grub will definitely go on the bootsector of the root partition.

---

### Post by SloYerRoll on 2008-03-09
Confused 57 (that's a username her ein the forums) has done all the heavy lifting for you!

Check these out...

[Dualboot]("http://users.bigpond.net.au/hermanzone/")
[UbuntuTutorials]("http://www.psychocats.net/ubuntu/index.php")
[Dualboot 2 HD]("http://www.ubuntuforums.org/showthread.php?t=179902")

---

### Post by THe.Conundrum on 2008-03-21
i would like to note that the hard drive i'm trying to do this on is a sata drive... would that make a difference?

---

### Post by THe.Conundrum on 2008-03-21
well i may have solved my problem.... not sure tho. i removed all my hard drives except the one i wanted to install kubuntu on and then installed it and you'll never believe it but it booted. how exciting!!! now all i need to do is figure out how to use it LOL

---

### Post by sandysandy on 2008-03-21
> **THe.Conundrum said:**
>  you'll never believe it but it booted. how exciting!!! now all i need to do is figure out how to use it LOL

hi Conundrum

great u could boot it up.

here are some linux tutorial links

[http://lowfatlinux.com/](http://lowfatlinux.com/)

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)


regards

---

