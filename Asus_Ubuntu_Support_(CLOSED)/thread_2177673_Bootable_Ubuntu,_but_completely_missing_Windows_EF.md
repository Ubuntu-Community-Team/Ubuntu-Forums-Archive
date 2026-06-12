---
title: "Bootable Ubuntu, but completely missing Windows EFI files"
date: 2013-09-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by AuP%*qb!# on 2013-09-29
Hi, I have an Asus Vivobook s200e i3 notebook.

I tested out Android on it, which worked really well (I installed to a USB), and then I decided to try installing it to the HDD next to windows 8...

BIG mistake!

It half installed to the EFI partition obviously wiping the Windows EFI files. I've got Ubuntu 12.10 up and running on the partition I meant for Android.

I thought that having grub would be a solution and let me boot into windows again, but it says invalid EFI path when I try booting into both the windows 8, or recovery partitions. If I have worked out correct, what is needed is the bootmgfw.efi file in the EFI/Microsoft/Boot/ directory on the EFI partition.

Is that correct, and if so, how can I obtain it?
I do not have a recovery media at hand. I did create one (a DMG image of the recovery partition to store on my Mac which did work when I tested it, but I obviously have corrupted it as it comes up with a blue "you need to repair your PC" screen or something like that with an error code 0x000000f.

I do have an upgrade Win 8 disk that I used for Win 8 in bootcamp on my iMac, but I have no clue where it is.

All my partitions are there, its literally just the EFI partition that it messed up.

Thanks for any help :)

Really thankful that I use Skydrive for my work and stuff, or that'd of been a big Oops lol.
Why I always have to have myself causing something like this to happen with each PC I have I don't know lol.
But as long as it ain't my Mac xD

Thanks
Jase Wolf

---

### Post by AuP%*qb!# on 2013-09-30
Well having windows 8 on my mac was a life saviour, because I was able to just create a recovery drive (startup repair drive) from on my mac and just put it into my laptop, go to the command prompt, and type in this...

bootrec /rebuildbcd

All done! :D

So now I have a bootable windows 8 and!!!!! A bootable ubuntu :D

Yay

---

### Post by AuP%*qb!# on 2013-09-30
I've got a Sandisk Cruzer Fit 32gb now, (it's so dinky), and it runs android x86 4.3 flawlessly. It's just so so fast!

i just wish that I was able to set the usb to ext3 rather than fat32 so I can root it, but the UEFI (CSM enabled) just won't boot it. But with fat32 it works perfectly (just no root access).

---

