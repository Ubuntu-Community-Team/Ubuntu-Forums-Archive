---
title: "[SOLVED] new installations"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by TimCor on 2008-01-07
Good day all
I am a first time user of UBUNTU and have obtained a CD with all the required data. However I have several problems when trying to set up the systems and would be grateful for any assistance.
On one PC I wish to load the UBUNTU OS onto Drive D (Windows runs on Drive C) and do not seem to have a facility to select the destination for the OS ? (I have edited the Boot menu in Windows to give me a choice of C or D with a nominal delay. Can UBUNTU be loaded onto D without any hardware changes ?

I also have a laptop (Dual core, 2gb ram, 160gb HD) and have DUAL BOOT installed UBUNTU with Win XP home but I selected 30% of the free space during installation but UBUNTU used nearly 90% leaving nothing left for Windows. I also cannot edit the bootloader file menu.lst

Using "Terminal" the command sudo gedit/boot/grub/menu.lst does not find the file. 
When going through file system and opening menu.lst i cannot save the new file (read only).

I also cannot get the Wireless network to connect allthough UBUNTU says that it is connected OK

So 
1. How to load UBUNTU on a second hard drive without hardware changes ?
2. how to use "Terminal" to find/edit a file ?
3. How to save an edited system file ?
4. What is wrong with the wireless connection ?
5. When first installing what "Amount of free space" should I select to get Windows in 70% and UBUNTU in 30% on one hard disk

Lots of questions, but I need all the help that I can get please

Many thanks
Tim

---

### Post by techno-mole on 2008-01-07
i dont know about your other issues, but i use 2 hard drives, one for xp and one for ubuntu, and all i have to do when installing is to make sure i put the right os on the right had drive, ive got a western digital and a samsung (both sata drives) and when i get to the partitioning section of the ubuntu set up it asks me where i want to put it, and seeing as i normaly install ubuntu on the western digital drive i select the the drive that starts wd.

---

### Post by hyper_ch on 2008-01-07
Ubuntu doesn't use "drives". You will need to alter your boot settings and allow to boot from cd/dvd. Once that is done, insert the cd into the drive and boot from it.

Also have a look here: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

That should answer some questions.

---

### Post by Samhain13 on 2008-01-07
It would also be good to remember that Ubuntu doesn't name your drives **C** or **D**. It has a different naming scheme (if that is at all the right term) which looks something like: **/dev/hda**, **/dev/hdb**, **/dev/sda**, etc.

[edit]
There's always someone hitting the Post Reply button faster. :)
Anyway, yeah, Psychocats.net is a very good resource apart from these forums.

---

### Post by stalker145 on 2008-01-07
> **TimCor said:**
> I also cannot edit the bootloader file menu.lst

Using "Terminal" the command **sudo gedit/boot/grub/menu.lst** does not find the file. 

I don't know if you typed the command the same here as you did into the terminal, but there needs to be 1) a space between the program you're running (gedit) and the file you're opening (/boot/grub/menu.lst) and 2) if you're already in the terminal, it's just easier to run nano instead of gedit. ```
sudo nano /boot/grub/menu.lst
```

> **TimCor said:**
> When going through file system and opening menu.lst i cannot save the new file (read only).

You are probably running your file manager as a normal user. ```
gksudo nautilus
```This will open up Nautilus as root (BE CAREFUL WHAT YOU DO!!).

---

