---
title: "2nd hard drive install"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Max_Kbrown on 2007-04-12
I want to install ubuntu on 2nd hdd(not a new HDD , some data still store in it), 1st hdd has Win XP, my question is: Do I need to format / partition 2nd HDD before ubuntu install? or ubuntu set up will take care of that?...

---

### Post by Stickymaddness on 2007-04-12
Ubuntu install will take care of that! You'll be pleasantly surprised how easy it is to install Ubuntu. Just be sure to install to your 2nd hard drive and not the first!!!

Good luck & enjoy!

---

### Post by Max_Kbrown on 2007-04-12
thanks for responding...

---

### Post by igknighted on 2007-04-12
> **Max_Kbrown said:**
> thanks for responding...

Make sure that you change the bootloader(grub) in the last step to install to (hd1) instead of (hd0) which is default.  You will then have to go into the bios and change the boot order of the HD's to have ubuntu's disk get booted, but doing it this way preserves the windows bootloader which (if overwritten) could cause issues later.

I am assuming you are using Edgy.  If you are using Dapper, this option is not there on the liveCD installer, you need to get the Alternate install CD.

---

### Post by Max_Kbrown on 2007-04-12
> **igknighted said:**
> ...  You will then have to go into the bios and change the boot order of the HD's to have ubuntu's disk get booted, but doing it this way preserves the windows bootloader which (if overwritten) could cause issues later.

I am assuming you are using Edgy.  If you are using Dapper, this option is not there on the liveCD installer, you need to get the Alternate install CD.


Sorry for not giving out more details. I want to install 6.10 and I will like to dual boot. If I followed what you recommended I will have to go into the bios and change from which drive to boot in order to change OS. Is that correct?

---

### Post by igknighted on 2007-04-12
> **Max_Kbrown said:**
> Sorry for not giving out more details. I want to install 6.10 and I will like to dual boot. If I followed what you recommended I will have to go into the bios and change from which drive to boot in order to change OS. Is that correct?

No, grub will be on the second HD and will be able to boot either Ubuntu or windows, the selection in the bios is just the first time.  However, should something happen and Ubuntu stop working or you decide not to use it, your windows boot sector will be untouched.  The default way is for Ubuntu to install over top of the windows bootloader, so if you ditch Ubuntu it will require you to use a windows disk to fix the windows MBR.  Either way works, but the many don't have a true windows install disk, just a recovery disk, which cannot fix the MBR.

---

### Post by Max_Kbrown on 2007-04-12
Got it !!... Thank you very much   :)

---

