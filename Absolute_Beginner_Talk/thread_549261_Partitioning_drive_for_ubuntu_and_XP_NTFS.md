---
title: "Partitioning drive for ubuntu and XP NTFS"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Chuck58 on 2007-09-12
I've got XP on this beast right now and run Ubuntu 7.04 as a live CD. Since my wife also uses this computer and has all her software on it also, rather than completely format and install Ubuntu, which was my original plan, I've been ordered to keep XP and add Ubuntu.

The problem, or so I've read here and there, is that my drive is NTFS and that might be a problem since Ubuntu needs FAT32.  Does anybody know whether I can add Ubuntu to a partition with NTFS, or does Ubuntu 7.04 convert NTFS to FAT32 automatically, or should I continue with the live CD to appease the wife?

---

### Post by chrome307 on 2007-09-12
Get yourself a cheap HDD and use that for installation - not worth upsetting marital equilibrium if something goes wrong for any reason - remember you'll be the person who's  in the wrong :lolflag:

---

### Post by Chuck58 on 2007-09-12
I have a second hard drive on this thing, but have never tried installing an OS to it. I've only used it to store files that are also saved on CD. I'm not sure I'd know how to put an OS on it, or how to use it if I did. 

I asked the guy I got the computer from and all he said was, "I wouldn't," and wouldn't elaborate. He builds computers, but isn't that knowledgeable about software, other than installing XP.

---

### Post by PmDematagoda on 2007-09-12
First thing is Ubuntu uses ext3, not FAT32.

And could you post the space you have in your hard drive/s?

---

### Post by mindtrick on 2007-09-12
Ubuntu's installer can shrink your existing partitions

---

### Post by PmDematagoda on 2007-09-12
> mindtrick:-

Ubuntu's installer can shrink your existing partitions 

Yes, but before that we need to know if there is enough free space for him to install Ubuntu with XP.

---

### Post by Chuck58 on 2007-09-12
> **PmDematagoda said:**
> First thing is Ubuntu uses ext3, not FAT32.

And could you post the space you have in your hard drive/s?

My C: drive is 37G with 29G available. D drive is 128G with 126G available. Don't ask me. That's how the guy who built this thing did it. I'd have put the larger drive as C.

---

### Post by CaptainInsaneO on 2007-09-12
Ubuntu uses a multitude of filesystems, NOT just ext3 (however, NTFS is not one of them). I recommend ext3 for Ubuntu but that's because I'm bias. lol

Chuck, when you go to install Ubuntu it will have a section for partitioning. When you get there in the install, choose "Manual" and partition your second hard drive. You can find various guides on how to do that all over these forums. I keep Ubuntu on a seperate physical drive from Windows just because I've heard a lot of problems come out of keeping them on the same drive with different partitions, so I highly recommend you do the same just because it's worked great for me so far.

Hope this helps, good luck with the wife. :lolflag:

---

### Post by PmDematagoda on 2007-09-12
Personally I recommend installing on the 127 GB hard drive as it has more than enough space, considering that Win XP is installed in the smaller one. But is your wife going to be happy with that setup?

---

### Post by Chuck58 on 2007-09-12
No problem with the wife, except she has her Paint Shop Pro, PhotoImpact, and other stuff that she uses for graphics work on this box, loves them both and doesn't want to switch.  LOL

OKay, if i install on the second drive, dumb question here, how do I boot into Ubuntu? Or, will the option appear when the computer boots?

---

### Post by PmDematagoda on 2007-09-12
Ubuntu's own boot loader, grub will be installed to the MBR allowing you to boot to either XP or Ubuntu at startup.:)

---

### Post by bwhitaker on 2007-09-12
You may also want to modify your grub config to boot into XP by default, since she may not know what to do if she ended up at the gdm login screen.

This post seems to cover what you would need to do:

[http://ubuntuforums.org/archive/index.php/t-393809.html](http://ubuntuforums.org/archive/index.php/t-393809.html)

---

