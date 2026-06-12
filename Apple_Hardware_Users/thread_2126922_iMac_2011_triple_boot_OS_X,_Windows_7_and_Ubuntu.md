---
title: "iMac 2011 triple boot OS X, Windows 7 and Ubuntu"
date: 2013-03-18
forum: Apple Hardware Users
---

### Post by Yoshi2889 on 2013-03-18
Hello! :)

I'm very sorry if there are like a gazillion similar threads out there, I have googled around for quite some time now and found nothing really relevant.

I want to triple-boot OS X 10.7 Lion, Windows 7 and Ubuntu 12.10.
What is the best, the easiest and the least painful way for me to try, which works?

I have Windows 7 installed as a Boot Camp partition right now, and 10.7 Lion along with the Recovery Partition. I don't have external recovery media for OS X Lion.

Can I keep my Boot Camp partition, and can I install Ubuntu in a safe and reliable way?

System specs:
CPU: Intel Core i5 2400S
GPU: AMD Radeon HD 6750M
RAM: 4 GB
HDD: Original 500 GB HDD
It's the 21.5" model.

I downloaded and burned the 64-bit Mac image from here: [http://releases.ubuntu.com/quantal/](http://releases.ubuntu.com/quantal/)

---

### Post by rmorr on 2013-03-22
Short answer: no. It's because Bootcamp uses a GPT/Hybrid-MBR scheme. You might be able to get away with shrinking the bootcamp partition in Windows 7, and using GPT fdisk to add a new partition for Ubuntu in the freespace and reconstruct the hybrid-MBR table. It'd be much safer to delete your bootcamp install, set up your partitions and then use GPT fdisk to create the hybrid table before reinstalling Windows and installing Ubuntu.

I've been through several rounds of setting up the triple-boot recently trying to get Windows to behave nicely w/ EFI boot [not successfully, so I went back to the hybrid-MBR scheme]. If you start with OS X and use disk utility to add a Windows, Linux and Linux swap partition and use GPT fdisk to add hybrid mapping for the OS X, Windows and main Linux partition and use something like rEFInd to manage your boot you can triple boot OK.

---

### Post by este.el.paz on 2013-03-22
> **rmorr said:**
> Short answer: no. It's because Bootcamp uses a GPT/Hybrid-MBR scheme. You might be able to get away with shrinking the bootcamp partition in Windows 7, and using GPT fdisk to add a new partition for Ubuntu in the freespace and reconstruct the hybrid-MBR table. It'd be much safer to delete your bootcamp install, set up your partitions and then use GPT fdisk to create the hybrid table before reinstalling Windows and installing Ubuntu.

I've been through several rounds of setting up the triple-boot recently trying to get Windows to behave nicely w/ EFI boot [not successfully, so I went back to the hybrid-MBR scheme]. If you start with OS X and use disk utility to add a Windows, Linux and Linux swap partition and use GPT to add hybrid mapping for the OS X, Windows and main Linux partition and use something like rEFInd to manage your boot you can triple boot OK.

@rmorr & Yoshi:

I'll add my $.02 to agree with rmorr that the Bootcamp option is not the best way to go . . . I followed, was it "rodbooks" online instructions on using Bootcamp to set up a dual boot OSX & Linux system . . . and, as far as that goes it's OK.  The problem is that now I can no longer partition the disk in disk utility, Bootcamp appears to lock the disk.  I wanted to have a dual boot 10.6.8., LinuxMint, and then later I wanted to add a third 10.8+ partition . . . but can't do it now without erasing the whole disk and starting over, rather than being able to re-format the partitions "on the fly" as it's possible to do before going the Boot Camp route.  If I get around to it, I would go the OSX DU to do the rough partitons, install OSX first in a HFS+ format, set the other partitions as "Free space" and then use GParted or the Linux installer to format the boot, home and swap partitions to install Linux into.  Or sometimes the Linux "guided" install works and it does the formatting for you.  As far as Windows goes I really don't know much about it, spent my computer life avoiding it.  Somebody mentioned on one forum that Windows could be run in OSX using VMfusionware or Parallels, and if I needed to run Windows I think I might do that rather than setting up a separate partition for it.  Apparently there are issues that come up the more you cut up a disk??  And, it seems like Linux can get you just about anything that you might need vis Windows . . . like OpenOffice or LibreOffice can open .docx and about 50 other formats.  

Good luck,

e.e.p.

P.S.:  [Next day] Up most of the night thinking that the rmorr reply was to this thread, where I didn't specifically say that the "rodbooks" instruction for dual or triple boot includes installing either rEFIt or rEFInd (probably didn't exist at the time he wrote his thing) to syncronize the partitions.  It is my understanding that once that is done the application isn't needed anymore, but I have kept mine, so it's a bit cumbersome as there are two boot windows, the rEFIt one, and then the GRUB one . . . .  I believe rEFIt can smooth over the differences between Windows requirements and other systems, have no experience with rEFInd, but it's supposed to be an update.

---

