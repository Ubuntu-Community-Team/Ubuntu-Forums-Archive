---
title: "Fixing an unbootable Ubuntu 9.10 x64 install"
date: 2009-11-04
forum: Apple Hardware Users
---

### Post by Nizumzen on 2009-11-04
I recently installed Ubuntu 9.10 on my 2006 Mac Pro which went fine. However when I restarted the computer it rendered it unbootable which I had to fix by using rEFIt to resync the boot information. Anyway now my computer is back up and running it seems to have broken the Ubuntu install.

In the rEFIt boot menu the Ubuntu install is listed as a legacy operating system and when I select it it just takes me to a screen with GRUB in the top left corner and no way to use the keyboard. Does anyone have any idea how I can fix this problem?

I am running 64bit Ubuntu if that makes a difference.

Thanks.

---

### Post by linuxopjemac on 2009-11-05
I had no problems with the 32-bit version...

---

### Post by NickJones on 2009-11-05
Go 32 Bit version and check the CD from the CD menu.

---

### Post by _mario_ on 2009-11-05
> **Nizumzen said:**
> I recently installed Ubuntu 9.10 on my 2006 Mac Pro which went fine. However when I restarted the computer it rendered it unbootable which I had to fix by using rEFIt to resync the boot information. Anyway now my computer is back up and running it seems to have broken the Ubuntu install...

i assume you installed grub2 (default in karmic) to the boot/root partition. did you try to reinstall grub2 using the live cd?

ciao,
Mario

---

### Post by Nizumzen on 2009-11-05
> **_mario_ said:**
> i assume you installed grub2 (default in karmic) to the boot/root partition. did you try to reinstall grub2 using the live cd?

ciao,
Mario

I'm actually attempting to restore Grub now. The problem is I have three operating systems on this machine. Windows now fails to boot as well which is a bit annoying but not critical.

It seems that Grub has got somewhat confused. Basically I'd like to keep all the operating systems booting through rEFIt 0.13. Windows should boot using its own bootloader and Linux should boot using Grub. Mac OS X should also retain its default behaviour when selected from rEFIt.

The problem is I don't have much experience with Grub so I am trying to work it out whilst running from the live CD which is not exactly optimal.

---

### Post by Nadav34 on 2009-11-14
> **Nizumzen said:**
> I recently installed Ubuntu 9.10 on my 2006 Mac Pro which went fine. However when I restarted the computer it rendered it unbootable which I had to fix by using rEFIt to resync the boot information. Anyway now my computer is back up and running it seems to have broken the Ubuntu install.

In the rEFIt boot menu the Ubuntu install is listed as a legacy operating system and when I select it it just takes me to a screen with GRUB in the top left corner and no way to use the keyboard. Does anyone have any idea how I can fix this problem?

I am running 64bit Ubuntu if that makes a difference.

Thanks.

Hi, are you aware that the 2006/2007 mac pros don't support EFI64 like the 08's and 09's? I believe the same rule applies to linux as well. You would have to mod the installer somehow to get 64-bit to work, just like getting 64-bit windows 7 to work. For a list Apple machines that are already EFI64, goto their website.

I would seriously consider going for a 08 or an 09 as this supports EFI64 + you can then take advantage of all the newer video cards.

---

### Post by Nizumzen on 2009-11-14
> **Nadav34 said:**
> Hi, are you aware that the 2006/2007 mac pros don't support EFI64 like the 08's and 09's? I believe the same rule applies to linux as well. You would have to mod the installer somehow to get 64-bit to work, just like getting 64-bit windows 7 to work. For a list Apple machines that are already EFI64, goto their website.

I would seriously consider going for a 08 or an 09 as this supports EFI64 + you can then take advantage of all the newer video cards.

That will not have an effect. 64 bit Windows runs fine on the machine. Apple just made a bad call when it comes to only supporting 64 bit EFI. Whether a machine uses EFI32 or EFI64 has no bearing on whether it is capable of booting 64 bit operating systems.

---

