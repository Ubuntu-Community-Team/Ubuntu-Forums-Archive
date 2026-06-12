---
title: "Uninstalling Ubuntu"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Albinus on 2007-11-13
Hi,

I recently installed Ubuntu and I want to uninstall it now. I have a windows reinstall disc which has been used once. How do i uninstall Ubuntu and restore my hard drive to its full size?

---

### Post by por100pre1 on 2007-11-13
Do [this]("http://ubuntuforums.org/showpost.php?p=1434123&postcount=2").

---

### Post by reckless2k2 on 2007-11-13
just pop the XP disk in and then follow the setup. you'll have to delete all the partitions and reformat everything made by ubuntu. before you move on you should have one partition. then XP will install. 

understand?

---

### Post by Albinus on 2007-11-13
I am using Windows Vista at the moment. WIll this work the same?

Also I have files and programs on my vista side will they be wiped?

---

### Post by sailor2001 on 2007-11-13
follow directions from por100

---

### Post by Duck2006 on 2007-11-13
> **sailor2001 said:**
> follow directions from por100

+1

---

### Post by zeller on 2007-11-15
I too have Windows Vista, and following por100's instructions via the link he posted did not work for my system.

Are there any other ways to uninstall safely? I already deleted the whole Ubuntu partition once and hosed the whole system. Nothing would boot.

So I inserted the Ubuntu Live CD again and reinstalled to get my GRUB bootloader to work so I'm back to square one.

Is there a way to fix the mbr once I start Vista?

I have an HP zd8000 and Gutsy doesn't play well with it. :( I have to go back to Feisty.

---

### Post by Tux.Ice on 2007-11-15
lolio i love gutsy gibbon and windows xp and vista both are **** and ya dont get windoz

---

### Post by por100pre1 on 2007-11-15
Please read [this]("http://support.microsoft.com/kb/927392").

---

### Post by zeller on 2007-11-15
> **por100pre1 said:**
> Please read [this]("http://support.microsoft.com/kb/927392").

Thank you for that por100. It did not occur to me to check the kb from ms. It's a "duh" moment. I'll try it out as soon as I have the time.

---

### Post by zeller on 2007-11-16
Should I delete the Ubuntu partitions and then follow the ms kb?

---

### Post by whitenerdy92 on 2007-12-03
another method to uninstall that should work (in theory):
1. Install a 3rd-Party Boot Loader, like an Acronis Trial.
2. Uninstall the boot loader, this will set the boot loader to the original Windows state.
3. In Vista, or GParted, delete the Ubuntu partition, and either add the empty space to C: or format as a new partition.


By the way, that method does not work if you bought a computer right before Vista was released, because then you got an upgrade disk later, and no recovery disks.

---

