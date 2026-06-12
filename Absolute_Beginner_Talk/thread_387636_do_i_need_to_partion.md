---
title: "do i need to partion"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by n1ght28 on 2007-03-18
I am planning on making my currently windows based system into a dual boot system running ubantu off a usb hard drive (70Gb) and windows off the internal hard drive I have various media and text documents on the external drive and was wondering do I need partion this usb drive and if not will my media and text files be accesssble through linux and windows.

---

### Post by sad_iq on 2007-03-18
Yes you need to partition the drive...just shrink the one it has and install ubuntu in the free space that remains. 
 Also..not sure though...wont installing to a usb hard drive make ubuntu slow (usb connections aren't that fast are they?)..just want to know that myself.

---

### Post by floke on 2007-03-18
Installing it on an external HDD will make it run slower. Also, better make sure that you write grub to the external device and NOT your internal drive, else your MBR will be buggered. As to whether both Ubuntu and Wins can read the files - this depends on the filesystem you are using on the external. You will have to partition the USB as the previous post stated. 

[EDIT] You'll also need to set the boot sequence to look for the HDD first.

But why are you wanting to install to an external? Why not dual boot off the internal?

---

### Post by n1ght28 on 2007-03-18
i just didnt want to go throught the hassle of partioning my internal, backing up everything and all that, there is nothing on my external i would be bothered about if i lost it.
whats a good program for backing up the internal then, also any tip on what i should use for the partion,or is going the virtual machine route a better one,

---

### Post by annda on 2007-03-18
ubuntu install will partition the drive for you. it is really very safe, but in case your power goes off (pr something like that) while partitioning, back up your documents etc. to the external drive.

make sure you have enough space for ubuntu und defragment your drive at least once. then boot from the cd and install (choose "use free space" in the partitioning dialog).

ps. a virtual machine will probably be slower than an usb disk.

---

### Post by floke on 2007-03-18
For a dual boot I would do this:

(1) Backup all Windows files you need - put on USB, cd whatever
(2) defragment windows and run a scandisc (VERY IMPORTANT STEP)
(3) Work out how much space you're going to give to Windows and Ubuntu
(4) Load in the LiveCD (do not use Feisty LiveCD for this, since the partitioner's a bit flaky IMO)
(5) Use GParted (System/Admin/Gparted) to resize/shrink the Windows partition
(6) Double click the 'Install' icon on the desktop, follow the options, and use the 'use largest available free space' option.
(7) Have a coffee while Ubuntu installs.
(8) When finished. Restart PC.

Note (a): The first time you go into Windows after this it will chuck a load of grumpiness at you about needing to check discs etc. Do not touch anything. Just leave it to do its business - it won't take very long.

Note (b) Every 30 or so times you boot into Ubuntu it will automatically check the disc - you will usually get a message about non-contigous files. Just ignore it - its not an error.

Good luck

---

