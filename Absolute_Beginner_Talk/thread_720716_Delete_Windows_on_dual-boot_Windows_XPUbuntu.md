---
title: "Delete Windows on dual-boot Windows XP/Ubuntu?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by rich41952 on 2008-03-10
I have Win XP installed on my "C" drive, and installed Ubuntu 7.10 on my "D" drive and dual-boot.  I have Ubuntu set up perfectly, but would like to completely remove Windows and install ANOTHER Ubuntu 7.10 on "C" where Windows lived without losing access to my Ubuntu on "D" Any ideas?

---

### Post by maybeway36 on 2008-03-10
Just overwrite the Windows partition with something else, and remove its entries in /etc/fstab and /boot/grub/menu,lst.

---

### Post by alphaniner on 2008-03-10
If you just run the install CD again and use manual install to install to the first partition, I *think* everything should work out ok.  At most you may need to edit the new menu.lst file that the new install will create.  But if I were you, I'd wait for a second opinion on this.

---

### Post by aysiu on 2008-03-10
> **alphaniner said:**
> If you just run the install CD again and use manual install to install to the first partition, I *think* everything should work out ok.  At most you may need to edit the new menu.lst file that the new install will create.  But if I were you, I'd wait for a second opinion on this.
alphaniner's on the right track.

Install another Ubuntu 7.10 over the C:\ drive, and it will erase Windows, reinstall Grub and automatically add the first Ubuntu 7.10 to the new boot menu.

---

### Post by Duck2006 on 2008-03-10
> **rich41952 said:**
> I have Win XP installed on my "C" drive, and installed Ubuntu 7.10 on my "D" drive and dual-boot.  I have Ubuntu set up perfectly, but would like to completely remove Windows and install ANOTHER Ubuntu 7.10 on "C" where Windows lived without losing access to my Ubuntu on "D" Any ideas?

Why not do it when  8.04 comes out, it's getting so close now.

---

### Post by alphaniner on 2008-03-10
If he installs another copy of Ubuntu, won't it overwrite the MBR settings to have grub look for the menu.lst in the new install?  I know there is an option to not install the boot loader, but I don't know if that will write to the MBR as though the new copy will be the only one installed, or if it just leaves the MBR as it is,

Forgot about fstab, though, that will definitely have to be edited if you had the windows partition mounted.

---

### Post by aysiu on 2008-03-10
> **alphaniner said:**
> If he installs another copy of Ubuntu, won't it overwrite the MBR settings to have grub look for the menu.lst in the new install?  I know there is an option to not install the boot loader, but I don't know if that will write to the MBR as though the new copy will be the only one installed, or if it just leaves the MBR as it is,

Forgot about fstab, though, that will definitely have to be edited if you had the windows partition mounted. The /etc/fstab on the original (D:\) Ubuntu will have to be edited, as it will refer to a non-existent filesystem, but the rest should take care of itself.

Yes, you could not have Grub overwrite the current Grub on MBR, but that would mean you'd have to manually add the new Ubuntu to the old Ubuntu's menu.lst file. If you do overwrite Grub, the new Ubuntu should *automatically* add the old Ubuntu to the its menu.lst file.

---

### Post by Duck2006 on 2008-03-10
> If he installs another copy of Ubuntu, won't it overwrite the MBR settings to have grub look for the menu.lst in the new install?

Yes it will. It will also pick up the old install to.

---

### Post by alphaniner on 2008-03-10
I thought so, I just wasn't sure how well the 'AUTOMAGIC KERNELS LIST' worked, as I've never done a Lin/Lin system before.

---

### Post by rich41952 on 2008-03-12
WOW!  So much good advice! Another reason why I won't miss Windows.......    When I first installed Ubuntu it looked for other operating systems and found XP, so I assume that in wiping "C" and replacing XP with Ubuntu it will probably find the other Ubuntu on "D".  The absolute WORST that could happen is I just end up with a clean install of ubuntu on "C" and no Windows and no access to the "D" drive version.

---

### Post by forrestcupp on 2008-03-12
> **rich41952 said:**
> The absolute WORST that could happen is I just end up with a clean install of ubuntu on "C" and no Windows and no access to the "D" drive version.

It will work without any trouble.  But even if for some reason it didn't automatically detect your previous version, the new version should still mount that drive so you could access the files.

You won't have any trouble though.  The new installation will sort everything out for you.

---

### Post by justleen on 2008-03-12
the absolute worse is that your HD fails, your monitor burns out, your keys get stuck, your mouse dies and your Internet subscribtion is cancelled...

But hey, that can happen any time  ;)

---

