---
title: "dual booting question."
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by wsantoso on 2006-03-23
I have windows xp installed on my main hdd and ubuntu on my old hdd (two separate disks). So far I have been switching the boot via the bios menu device boot priority. How do I edit the grub configuration to be able to boot windows from the linux drive? At the same time how should my windows boot.ini look like if I want to be able to boot linux from the windows drive? Would like to be able to boot either systems regardless of which hdd is set as the main boot device in bios. Thanks.

---

### Post by tommy1987 on 2006-03-23
you can edit all of that in the following location: /boot/grub/menu.1st   provided grub is installed..
Simply type: sudo gedit /boot/grub/menu.1st

---

### Post by OffHand on 2006-03-23
I don't know much but I do know you shouldn't randomly start editting the grub list if you don't know what you are doing. Wait till someone comes along that can help you with it. If you mess up the grub it can lock you out of your compu.

---

### Post by mumushi on 2006-03-23
Im not sure if you can do that with the operating systems installed on different hdd. I had also the same problem before and the only sollution made was to install ubuntu and windows on the same hard drive which is partitioned. i installed windows first then ubuntu. ubuntu lets u configure the grub during installation. it detects previously installed operating systems. 

I am not sure if this help but i do hope it gives you a little bit of idea. Good luck.

---

### Post by akiro.yamamoto on 2006-03-23
[quote=wsantoso]I have windows xp installed on my main hdd and ubuntu on my old hdd (two separate disks). So far I have been switching the boot via the bios menu device boot priority. How do I edit the grub configuration to be able to boot windows from the linux drive? At the same time how should my windows boot.ini look like if I want to be able to boot linux from the windows drive? Would like to be able to boot either systems regardless of which hdd is set as the main boot device in bios. Thanks.[/quote]

When you installed ubuntu where did you install grub , did you install it at all???
Since you seem to be using the bios as your boot loader it appears that GRUB
was not installed!!! :-k
If grub was installed to mbr of the master hard drive (hda) and Win is installed to
that drive (hda1) edit the menu.lst as follows (See PIC):

Then set the bios to boot the Win hard drive.

---

### Post by wsantoso on 2006-03-23
GRUB is installed on my secondary hard drive where Ubuntu is installed but obviously not on my windows drive. I got the press esc to go into GRUB menu when I boot from my linux drive and can see the different kernel options there but there is no windows option in the menu. Will edit the menu.lst file to add the windows entry when I get home tonight and see how I go. Thanks.

---

### Post by confused57 on 2006-03-23
I have dual boot with 2 hard drives, Ubuntu is the master drive and WindowsXP is on the slave drive. When my system boots up it enters the grub menu and automatically boots to windows unless I specify it to boot to Ubuntu. I was able to do this using the following thread(lha is the expert on dual-booting using 2 hd's):

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

---

### Post by wsantoso on 2006-03-24
Thanks guys. The following lines from the above link worked for me. It wouldn't work without the two map statements. It's booting fine now. 

> 
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


---

