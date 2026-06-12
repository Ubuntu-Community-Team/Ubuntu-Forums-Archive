---
title: "I've erased the entire Hard Disk"
date: 2008-06-10
forum: Apple Hardware Users
---

### Post by Matodo on 2008-06-10
Hello

When I was trying to install Ubuntu 6.06 on my iBook G4, I chose to erase the entire Hard Disk. Therefore, the installation process never gets finished.
I get this error message while installing:
```
No NewWorld boot partition was found.
The yaboot boot loader requires an Apple_Bootstrap partition
at least 819200 bytes in size, using the HFS Macintosh
file system.
```
I tried to fix that problem by recreating the lost partitions manually, with no success. Here are all the existing partitions:
```

Partition     Filesystem     Size              Flags
/dev/hda1     unknown        0.03   MB       
/dev/hda2     unknown        0.95   MB         boot
/dev/hda3     ext2           27.59  GB
/dev/hda5     hfs            1.25   MB
/dev/hda4     linux-swap     361.24 MB         swap

```
*Now I'm downloading Ubuntu-8.04-alternate-powerpc, if only it could help.*

What should I do?
Please help.

---

### Post by stream303 on 2008-06-10
Ok, since you've chosen to wipe the whole drive, this should be a bit easier now. :)

It is odd that it wouldn't finish the install, unless your image is bad, or perhaps even a hard disk problem.

Now that you are downloading the 8.04 "alternate", I'd just try again letting guided partitioning use the whole disk.  It should wipe out those old partitions and do everything automatically.  Be very patient because at times it may appear that it isn't making any progress, when in fact you need to walk away and not stare at the blue/red gas gauge.  Sometimes it may look like it is hanging at 33% or some other figure, when in fact it is doing the partitioning and formatting.

Another option is to use the "go back" feature in manual partitioning.  You could manually delete all those old partitions that got messed up, and then TAB to the "go-back", and start fresh with using the whole disk.

---

### Post by avtolle on 2008-06-10
I cannot emphasize the "be patient" part of stream303's post enough. Walk away a bit, get a cup of coffee, whatever. If patience is a virtue, be virtuous! :-) and let things happen in their own good time.

---

### Post by hvc123 on 2008-06-11
hi mate,

i got hardy (eventually) to install on my christmas puddy G4.(imac g4)

it was a pain but well worth it.. i had to burn on an imation disc as the imac didnt like sonys, then i had to burn it at no faster than 16x.

boot from cd is the most annoying part of the process. it seems that its more luck than timing ( or maybe just me).

i did a full install(erase entire disk). then just use the guided partition. the install fails at the part where it trys to install the applications but you can skip that annyway. eventually completes the install.

when it finally boot into ubuntu i had to copy the sources from another file because it only had the cdrom in there. but after i installed ubuntu-desktop (had about a 1000 dependencies and was over 600 mb!) all is now good.

it took me weeks to figure out that the disk image was rubbish. i thought it was down to the bootloader or something. here is my fdisk -l after a 'Use entire disk - guided" selection.

        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           153287110 @ 2018      ( 73.1G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 3012360 @ 153289128 (  1.4G)  Linux swap

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0
.

it created the bootstrap partition for me :-D

---

### Post by Matodo on 2008-06-11
Thank you guys. I had no problems while installing Hardy, except the patience issue. :) However, it's better than nothing!

---

