---
title: "Right after installing ubuntu"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Siimu on 2005-10-30
Hei hei,
finnaly decided to switch from win to Ubuntu. But ive worried about will the operating system run on a laptop? and can i log on to the net right after installing the new operating system..

Thanks for your fast replies.
Siim

---

### Post by aysiu on 2005-10-30
Depends which laptop.

---

### Post by ubuntumaneh on 2005-10-30
It can be used in laptop (Im in one right now). Even some old ones. And the installation goes just like you are dreaming. However, it may have some problems. So, it will depend on you laptop. There are lists of laptops in the net. Try google: ubuntu laptop (and your specific model). Or say in this forum which is your laptop. Maybe someone is using it, and can describe her/his experience.

---

### Post by Siimu on 2005-10-30
Hei,
I downloaded the install file and burned it on a cd. I tried to boot the computer and see if the program starts to open itself. Tried it twice and i didnt so i clicked it while Windows was active but i tried to auto burn it? What should i do... help please?

---

### Post by ubuntumaneh on 2005-10-30
Some things:

1) Have you copied (or burned) an iso image of Ubuntu to your cd?

2) See at the BIOS (when you start your computer press del, and see if appears a coinfiguration menu) the order of the boot devices. You should boot first from cd/rom.

---

### Post by Siimu on 2005-10-30
Yes its an ISO image that i burned on the cd. Ill try the second thing.
By the way do you know how to separate my hard drive in to 2? one for windows and the other for linux and other files.

---

### Post by ubuntumaneh on 2005-10-30
This process is know as dual boot. It is fairly easy to do. Usually, the first thing is to make partitions. For this use a programm called PartitionMagic. Now, I advice you to look for an "how to" dual boot. There are many in this forum. Try search here in the forum and look alsoi in google.

---

### Post by Siimu on 2005-10-30
I tried to enter BIOS but i failed tried 4 or 5 times... the del button didnt work :(

---

### Post by ubuntumaneh on 2005-10-30
Which is you computer?

Try:

1) When you boot, usually appears a message on how to enter the BIOS configuration. Read it.

2) If it is a laptop, maybe you have to use a disk to change the BIOS settings.

3) Dou you have a manual of your computer with you? Look there for the boot section and see how to change the boot device order.

4) You may try to look for the manual of your computer in the web. Try google.

---

### Post by Siimu on 2005-10-30
Well I found out that i shouldnt burn the file as a regular ISO fail.
But if i would like to install linux on one of my new partition then should i do it as a Linux systam type or still NFTS system type?

---

### Post by ds[de] on 2005-10-30
[QUOTE=Siimu](..)i would like to install linux on one of my new partition then should i do it as a Linux systam type or still NFTS system type?[/QUOTE]
I don't think you can use an NTFS partition to install Linux since writing to NTFS isn't supported by Linux yet (afaik).
Just use the ext3 filesystem for your ubuntu installation.

Regards,
ds[de]

---

### Post by erikpiper on 2005-10-30
NTFS is horrible and is useless for linux-- Use ext3. (Or reiserFs or something. I like ext3) 
For your swap partition, use linux-swap. Make your swap at least as big as you ram, unless you have over 512MB- Then I make it half.

---

