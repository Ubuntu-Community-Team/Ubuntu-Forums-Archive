---
title: "Do you know?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Newbie2929292 on 2006-10-27
I want to uninstall Grub.  I have found out how to do this using the Recovery CD in XP.   With Grub gone if I install another boot loader (Such as System Commander or Partion Magic's Boot Magic) will it list Ubuntu?

---

### Post by CatKiller on 2006-10-27
> **Newbie2929292 said:**
> If we uninstall GRUB will a boot (Partition Magics Boot Magic,System Commander etc.,) or will it just mess up and not boot at all and nothing will take its place....or if we install one after we unistall Grub?

[How to uninstall GRUB from my hard disk drive?]("http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12")> There is no concept *uninstall* in boot loaders, because if you *uninstall* a boot loader, an unbootable machine would simply remain. So all you need to do is overwrite another boot loader you like to your disk, that is, install the boot loader without uninstalling GRUB.

For example, if you want to install the boot loader for Windows, just run **FDISK /MBR** on Windows. If you want to install LILO (I can't imagine why you want to do such a thing, though), run **/sbin/lilo** on GNU/Linux. 

---

### Post by Newbie2929292 on 2006-10-27
> **CatKiller said:**
> [How to uninstall GRUB from my hard disk drive?]("http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12")

We already found out how to unistall it
But thank you for telling us again
I didnt know another boot loaded would overwrite grub

PS we dont want to install LILO (we hate it we already mess up with it....we stayed up all night)

---

