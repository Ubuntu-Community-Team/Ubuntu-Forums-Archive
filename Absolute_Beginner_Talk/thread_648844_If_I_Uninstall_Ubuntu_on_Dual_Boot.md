---
title: "If I Uninstall Ubuntu on Dual Boot"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Lanc1988 on 2007-12-24
I have vista installed on the primary hard drive in my computer and ubuntu 7.10 installed on the secondary hard drive (both hard drives are 120GB if that matters). Anyway, I was just thinking that if I ever decide to uninstall ubuntu by booting into vista and reformating the hard drive that ubuntu is on, wouldn't that make it unable to let me boot into vista because the grub boot menu file is under ubuntu or would it just go back to loading vista automatically how it used to before I installed ubuntu?

Also, after installing ubuntu on that 2nd hard drive, when I boot into vista I can no longer see that hard drive under My Computer, so currently I couldn't reformat the hard drive even if I wanted to.. how would I go about being able to see that hard drive that ubuntu is on in vista again?

Thanks.

---

### Post by Paqman on 2007-12-24
Ubuntu's GRUB bootloader works by using the windows bootloader. First GRUB fires up, then if you select Windows it starts NTLDR, the bootloader for Win (at least, that's the way it works for XP) So if you got rid of GRUB, you should still be able to boot Windows.

As for your Ubuntu partition not showing up, that's probably because Windows can't read the Ext3 filesystem. You could use the [Gparted LiveCD](http://gparted-livecd.tuxfamily.org/) to reformat the partition to NTFS, then it would show up.

---

### Post by ray bot on 2007-12-24
> Ubuntu's GRUB bootloader works by using the windows bootloader. First GRUB fires up, then if you select Windows it starts NTLDR, the bootloader for Win (at least, that's the way it works for XP) So if you got rid of GRUB, you should still be able to boot Windows.
The trouble with this is that most of GRUB is actually on the partition that contains /boot (probably your main Ubuntu partition).  The part of grub that is in the MBR (called GRUB stage 1) doesn't do much.  The real work is done by GRUB stage 2, which would get erased if you formated your Ubuntu partition.
What you should do instead is restore the Vista boot loader.  I don't have Windows, so I'm not entirely sure how to do that, but this might help: [http://www.pronetworks.org/forum/about76643-0.html&sid=ea8b10cceda9f68edc22bffab16ab3e8](http://www.pronetworks.org/forum/about76643-0.html&sid=ea8b10cceda9f68edc22bffab16ab3e8)

---

