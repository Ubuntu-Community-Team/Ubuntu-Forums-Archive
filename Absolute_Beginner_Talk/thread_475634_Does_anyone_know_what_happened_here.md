---
title: "Does anyone know what happened here ?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Kari_Juhani on 2007-06-16
I have 2 blocks of 1GB RAM, and my bios finds them both. _One at time or together_. My motherboard has support for 4GB of RAM.

But...  Ubuntu Feisty says i have only 986,5MB of memory ( .. and 2.8 GB swap : im running a  32bit version on a 64bit AMD )

My 7.04 is a distro downloaded from Ubuntu site, and i have updated it with aptitude when ever there has been new upgrades.

I also have dualboot to Windows XP pro , and now it gets weird....
----------------------------------------

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Kari>mem
    655360 bytes total conventional memory
    655360 bytes available to MS-DOS
    626944 largest executable program size

   1048576 bytes total contiguous extended memory
         0 bytes available contiguous extended memory
    941056 bytes available XMS memory

MS-DOS resident in High Memory Area

------------------------------------------------------------

Windows has also missed another memorystick ???

Have anyone a clue what happend here ? BIOS finds all RAM, but both operatingsystems missed ½ ?
How to repair this ?

Kari


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>><

Reason for this behavier is memorys dualchannel - option. For some reason it's not working anymore, so memoryblock's in 1+2 are not regonized after bios.

When i put blocks on 1+3 , i get singlechannel memory ( and as it should be 1=100%+3=50% of original value ).. and Windose + Linux are seeing it right as it should be = 1,5GB of memory !

Thanks fo help to everyone..
Kari
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>><

---

### Post by AlexenderReez on 2007-06-16
if both windows and ubuntu partition give same error...then it is not software problem...it is hardware problem....check back how to you plug your ram........

---

### Post by hoges on 2007-06-16
run the memcheck option in the grub bootloader overnight. This will check the ram for any hardware errors.

---

### Post by Kari_Juhani on 2007-06-16
> **reez0105 said:**
> if both windows and ubuntu partition give same error...then it is not software problem...it is hardware problem....check back how to you plug your ram........

Well .. if RAM would be plugged wrong, BIOS wouldnt find it ?

It does.

I'm gonna try to change slot in motherboard.. using now 1+2 , 3+4 are empty...  

Kari

---

### Post by bigken on 2007-06-16
try 1 chip at a time

---

### Post by AlexenderReez on 2007-06-16
> **Kari_Juhani said:**
> Well .. if RAM would be plugged wrong, BIOS wouldnt find it ?

It does.

I'm gonna try to change slot in motherboard.. using now 1+2 , 3+4 are empty...  

Kari

hm...just try...by the way...i never believe there would be anybody who will use a lot of space for swap......it is such a waste of space.....for using that much.......2 gig of ram?....usually...i don't really sure whether you are going to use your swap or not.......

---

### Post by Kari_Juhani on 2007-06-16
> **reez0105 said:**
> hm...just try...by the way...i never believe there would be anybody who will use a lot of space for swap......it is such a waste of space.....for using that much.......2 gig of ram?....usually...i don't really sure whether you are going to use your swap or not.......

Do you know how to reduce size of swap in ubuntu ?

it's a default value that was there when i installed feisty..

Kari

---

### Post by AlexenderReez on 2007-06-16
just resize it...using gparted.....make it about 500mb..(your ram is really ore than enough....).....change the rest to other kind of partition.....default...no!default swap is 256mb......all ubuntu that i used to install give that value...

---

