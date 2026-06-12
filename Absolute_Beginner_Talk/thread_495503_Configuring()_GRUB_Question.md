---
title: "Configuring(?) GRUB Question"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by drafael on 2007-07-08
Repost of: [http://ubuntuforums.org/showthread.php?p=2983501#post2983501](http://ubuntuforums.org/showthread.php?p=2983501#post2983501)
Just in case someone in this forum can help:

> I started out installing ubuntu with a 10GB partition. I have today decided that's not enough, as I'm going to switch over to ubuntu completely, with the dual boot to windows only for games etc.

Anyway, so I edited the partitioning using my livecd. What I did was shrink the windows partition further, and then copy the ubuntu partition so it's just after the windows partition, which will allow me to expand it - though I haven't done this yet. I then deleted the original ubuntu partition.

What this amounts to is my ubuntu install being on /dev/sda3, as opposed to /dev/sda2, which is what the GRUB bootloader points to. How do I change it so that it'll point to /dev/sda3, and so boot ubuntu properly?

Thanks in advance for any help ^^

Sorry for posting in two forums, but I really need to get this sorted out, and no replies so far in my other thread...

Thanks again.

---

### Post by Malta paul on 2007-07-08
Hi,
Your boot sequence is probably set to (0,02) try (0,03)
When you boot into grub, you con press 'e' and change these settings. Then boot again, this is only temporary for the settings you have just made.
When you have the correct settings you need you can change the settings permanent by editing the grub menu list. Using terminal  <sudo gedit/boot/grub/menu.lst > In fact you can get some good information from this list. the # marks are the same as rem in Ms Dos.
good luck;)

---

### Post by Malta paul on 2007-07-08
This reference may also help you: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu)

---

### Post by drafael on 2007-07-08
Thanks for your help, got it sorted ^^

What I did:
sudo mkdir /mnt/tmp && sudo mount -t ext3 /dev/sda3 /mnt/tmp
sudo gedit /mnt/tmp/boot/grub/menu.lst

Change all (0,1) to (0,2), save, reboot and it's going well (though on bootup, filesystem got fixed apparently).

---

