---
title: "dual boot without dual boot (clip frame)"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-28
Hello people,

I use Ubuntu now for my working environment, but I keep an additional drive with XP just for gaming. I have a clip frame (is taht the right word) in my PC which allows me to change the hard drive in 30 seconds without opening the case, that's what I do instead of dual boot. Not long ago I dropped one of the drives and it broke so I'm looking for a better solution. However I still don't want to have both drives fixed inside the case. I want only the Ubuntu drive fixed in and the game drive in the clip frame...or nothing in the clip frame. If the game drive is in the frame, the PC should boot XP from there, if it's not in the frame, the PC should boot from the fixed Ubuntu drive, which can be IDE or SATA (I would prefer SATA). How can I accomplish this?

Thanks
Cruz

---

### Post by Bachstelze on 2006-09-28
Just configure your BIOS to boot from the gaming drive first, and then the Ubuntu one. If the frame is not present, your BIOS will skip to the second choice (ht EUbuntu one) automagically.

---

### Post by bernied on 2006-09-28
I don't understand your 'clip frame' but if both drives are treated as hard drives by the bios, then maybe you just need to adjust your bios boot order. This is usually done by hitting the 'Delete' or F5 key (or some other) as soon as the machine powers up. Which key you hit depends on your hardware.

---

### Post by bernied on 2006-09-28
snap

---

### Post by Cruz on 2006-09-28
OK I will set up an experiment but I have a bad feeling in my guts. When I remove the game drive BIOS can't see it and it could delete it from the boot order.

---

### Post by xhaan on 2006-09-28
I think you could use a bit of GRUB trickery to do this, using the grub fallback system.

[http://www.gnu.org/software/grub/manual/grub.html#Booting-fallback-systems]("http://www.gnu.org/software/grub/manual/grub.html#Booting-fallback-systems")

You would have to have grub on the drive that stays in though, with the boot partition with menu.lst on it.

---

### Post by Cruz on 2006-09-28
Thanks for the grub hint, I'm looking into it as I type. heehee
But I will only try it when the BIOS approach has failed. It just doesn't feel right to have my main everyday system configured as a fallback.

---

### Post by gn2 on 2006-09-28
> **Cruz said:**
>  When I remove the game drive BIOS can't see it and it could delete it from the boot order.

BIOS won't permanently remove it from the boot order, but if it's not present it won't be given as a boot option.
When it's plugged back in BIOS will restore it to the list.

I swap drives regularly and have never had a problem doing so.

Have you got external SATA?

That's high on my wish list for next build...

---

### Post by Cruz on 2006-09-28
> **gn2 said:**
> BIOS won't permanently remove it from the boot order


OK thanks for the reassurance. I will pursue this solution. It takes some time to set up a testing environment though. No my SATA is internal. So far I'm not friends with external drives, why would you want one?

---

### Post by gn2 on 2006-09-28
> **Cruz said:**
>  So far I'm not friends with external drives, why would you want one?

External drives are superb.

Quick and easy file transfer (backup) and OS changing.

If you back up to a removeable drive then remove it, if your PC goes totally t*** up you've still got all you're valuable stuff saved.

---

### Post by Bachstelze on 2006-09-28
That's what separate partitions are for ;) Personnally, I only use removable drives to transfer stuff between an internet connected PC and one that is not connected. Between two connected PCs, I always use FTP or SSH.

---

### Post by gn2 on 2006-09-28
> **HymnToLife said:**
> That's what separate partitions are for ;) Personnally, I only use removable drives to transfer stuff between an internet connected PC and one that is not connected. Between two connected PCs, I always use FTP or SSH.

I also like to have a separate partition for documents etc, but I like duplicates on another drive because separate partitions won't protect your data from hardware failure.

Hard drives are more likely to fail while in a working PC than sitting on a shelf.

---

### Post by Cruz on 2006-09-28
> **gn2 said:**
> BIOS won't permanently remove it from the boot order


It woooorks! It's like a dream come true. Thanks for the help.

---

