---
title: "reinstalling windows"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by davesec on 2008-03-26
hi!

i want to reinstall windows and keep ubuntu. this is what gparted looks like when i open it:

[img]http://i41.photobucket.com/albums/e260/davesecretary/gpart.jpg[/img]

can anyone tell me what if i need to do anything gparted before installing windows?

i read that after i install windows i need to reinstall grub, either by using super grub, or by opening terminal in ubuntu live cd and typing in some stuff?

when i installed ubuntu i accidently deleted windows (thankfully i backed everything up), but i'd like to keep ubuntu this time round.

thanks!

---

### Post by madara_sama on 2008-03-26
if you want to dual boot. You can create new partition for windows, then install it. Keep it. Or you just reinstall the grub, after installing windows.

---

### Post by barbedsaber on 2008-03-26
Same story here, ditched vista to go with xp (and managed to not touch my linux partion) now I just need grub back, because. well, I want to use linux again, how do I just install GRUB, because as much better as it is over vista, XP still loses to ubuntu.

---

### Post by sg1 on 2008-03-26
Another way round it is to install a second HDD into your machine and disconnect the power from the Linux drive.

Then with just the new drive connected, install windows to it(may require jumper setting if ATA).

When you're done, reconnect the power to the Linux HDD and use the BOOT menu(usually F11) to select the HDD containing the OS you want.

You can also change the boot priority in BIOS(usually F2) to boot up to the preferred OS from start up and just use the BOOT menu(usually F11) to select the alternative OS:)

This way it keeps the two OS's COMPLETELY seperate(no modified windows BOOT INI) yet still able to fully function together for file transfers from windows to linux(although windows cannot see the Linux HDD for files transfers, Linux CAN see and read the windows one(another PLUS for LINUX HOORAAHH!! ))

[IMG]http://www.fadzter.com/smilies/buttrock.gif[/IMG]

---

### Post by gary0 on 2008-03-26
SG1, That's exactly the way I do it. Keeps both os's separate from each other, and it's a breeze to reinstall either os just by disconnecting the relevant drive. No messing with grub required.

Gary.

---

### Post by sg1 on 2008-03-26
> **gary0 said:**
> SG1, That's exactly the way I do it. Keeps both os's separate from each other, and it's a breeze to reinstall either os just by disconnecting the relevant drive. No messing with grub required.

Gary.

PLUS it has the advantage of longer HDD life span due to a different drive being used for each OS and not spinning up the same drive for both all the time. 

I used to have two towers K.V.M'D together, one running Linux and the other M$ XP, but since the addition of the SKY box in the bedroom, I have run out of plug sockets LOL
[IMG]http://farm2.static.flickr.com/1011/894568292_94cde0919a.jpg[/IMG]

---

### Post by davesec on 2008-05-12
> **sg1 said:**
> Another way round it is to install a second HDD into your machine and disconnect the power from the Linux drive.

Then with just the new drive connected, install windows to it(may require jumper setting if ATA).

When you're done, reconnect the power to the Linux HDD and use the BOOT menu(usually F11) to select the HDD containing the OS you want.

You can also change the boot priority in BIOS(usually F2) to boot up to the preferred OS from start up and just use the BOOT menu(usually F11) to select the alternative OS:)

This way it keeps the two OS's COMPLETELY seperate(no modified windows BOOT INI) yet still able to fully function together for file transfers from windows to linux(although windows cannot see the Linux HDD for files transfers, Linux CAN see and read the windows one(another PLUS for LINUX HOORAAHH!! ))

[IMG]http://www.fadzter.com/smilies/buttrock.gif[/IMG]

jesus christ man, i just want windows back on my computer, i'm not trying to build a rocket ship!!

---

### Post by kirios on 2008-05-12
Boot from the XP CD, create a primary partition in the free space, then install Windows. This may not work if you have a System Recovery disk instead of an XP disk. Also, XP may tell you that it requires the *first* primary partition on your disk. 

If you manage to install Windows, boot from the Ubuntu live CD, mount the partition on your hard disk where Ubuntu is installed, then **chroot** to that partition and reinstall grub on the MBR.

---

### Post by davesec on 2008-05-16
kirios - can you elaborate a bit? how do i mount the ubuntu partition from ubuntu live CD - what program do i use? also, what exactly do i type in terminal to 'chroot'. lastly, what is an MBR and how do i reinstall grub?!

thank you!

---

### Post by davesec on 2008-05-16
also, i formatted the big partition i had set aside for windows and moved some random stuff in there.. here's what gparted looks like right now:

<img src="http://i41.photobucket.com/albums/e260/davesecretary/gpart1.png">

if i move the 5gb of files to my external harddrive, should i be able to set windows up in dev/sda3?

thanks!

---

### Post by davesec on 2008-05-16
let's try this image:

[IMG]http://i41.photobucket.com/albums/e260/davesecretary/gpartjpg.jpg[/IMG]

---

### Post by davesec on 2008-05-16
last try

[IMG]http://i41.photobucket.com/albums/e260/davesecretary/gpart1.png[/IMG]

---

### Post by kirios on 2008-05-17
If you install Windows, it will overwrite the Ubuntu bootloader (grub) in the MBR (the first sector of a hard disk that contains the partition table and the bootloader). The Windows bootloader doesn't give you an option to boot into Ubuntu. One way to get the Ubuntu option back is to boot from the live CD and create a mount point for the sda1 / partition: 

```
sudo mkdir /mnt/ubuntu 
sudo mount /dev/sda1 /mnt/ubuntu
``` 

You can then make the live CD use the /mnt/ubuntu partition as /: 

```
sudo chroot /mnt/ubuntu
``` 

Next, install the sda1 grub to the MBR: 

```
sudo grub-install /dev/sda
``` 

Note that the target is **sda**, _not_ sda1.

Reboot into Ubuntu and add an entry for Windows in the */boot/grub/menu.lst* file. 
  

> **davesec said:**
> kirios - can you elaborate a bit? how do i mount the ubuntu partition from ubuntu live CD - what program do i use? also, what exactly do i type in terminal to 'chroot'. lastly, what is an MBR and how do i reinstall grub?!

thank you!

---

