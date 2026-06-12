---
title: "[SOLVED] Removal of a partition: will I lose GRUB?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-02-23
Okay, I'm new to this but having been dallying around trying to make a decision to remove XP I've finally done it!  I'm now officially Windoze free - yippee!  I've resized my Ubuntu partition to 53.41GB (/dev/sda2) having an extended of 1.44GB (/dev/sda3) and Linux-swap of 1.44GB (/dev/sda5), leaving 19.68GB unallocated.  Whilst doing this resize I deleted all of XP, intentionally but in a spur of the moment decision (I'm really glad I did as my learning with Ubuntu is growing exponentially) but I now wonder if I resize /dev/sda2 to include the unallocated space whether I will have any problems with starting Ubuntu because I've lost GRUB?  Hope this hasn't been rambling, but I want to be completely Ubuntu sufficient and not make extra work for myself.  Your advice and help is appreciated.

---

### Post by nofrendo on 2008-02-23
Yes, you won't lose GRUB.

But in the future if you decide to install any OS, it will most likely overwrite your MBR.

So here's what you do if that happens...

sudo grub
root (hd0,0) <Replace this with whatever partition you want to use GRUB from, for example, the first partition on the first HD would be (hd0,0), the second partition would be (hd0,1), etc. Make sure you have the right partition number, because otherwise you'll have to do this again>
setup (hd0) <This assigns whatever bootloader is on the above partition to the MBR, so that's what will load when your computer boots>
exit

and that's it! Hopefully you won't have to do this though. But it's better to know because it's frustrating as **** when your MBR is full of Winblows and you can't boot into Ubuntu

---

### Post by Berean on 2008-02-24
nofrendo, good man, thanks for the advice!  Am now starting to use the unallocated space.  Cheers, mate.

---

