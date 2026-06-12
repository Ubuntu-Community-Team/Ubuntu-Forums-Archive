---
title: "lilo question for santa rosa (macbook pro 17 d2c) with feisty"
date: 2007-10-01
forum: Apple Intel Users
---

### Post by willnight on 2007-10-01
i have tripleboot set up . i had it done quite successfully on my last lapton (macbook pro 17 duo core -- not d2c). this time, i'm hitting a stone wall due to new hardware on the d2c (?).

i like grub (which i have installed now, and working), as a duoboot, but prefer lilo for tripleboot. i like the direct path into ubuntu that lilo allows, without a menu that grub has.

anyway, is it possible to install lilo on my new laptop? the problem i'm running into has something to do with linux-kernel-headers, which don't exist anymore.

if someone could offer a successful solution or point me to one, i'd appreciate it!

---

### Post by pxwpxw on 2007-10-01
You can set grub in the menu.lst for a zero delay and hidden menu, if that helps.

If there is a problem with linux headers it wont have anything to do with bootloaders.

---

### Post by willnight on 2007-10-01
got it!

do steps 21 - 24 from this how-to:

[http://ubuntuforums.org/showthread.php?t=187465&highlight=macbook+pro+install+lilo]("http://ubuntuforums.org/showthread.php?t=187465&highlight=macbook+pro+install+lilo")

(note: make sure you match the version in step 21)

then use windows boot disk to "uninstall" grub with fixmbr (select 'repair' when prompted to install windows. important: make sure you set an administrator password in windows first because it will ask for it in 'repair'.)

if you did the lilo install from the link above correctly, refit will allow you to boot into the respective environment --- which mean going in windows without having to go through grub.

(another note: the first time, refit will kinda hang when you choose linux. simply reboot and choose linux again. lilo will kick in the second reboot.)

best!

---

### Post by pxwpxw on 2007-10-01
Glad you got the answer.:)
However is is worth noting that  we can use grub for booting  linux but boot windows direct, not via grub menu, if refit is installed.  :cool:

---

### Post by willnight on 2007-10-02
pxwpxw, thx for your post. i am actually confused as to what you said though in your last post about grub.

what i know is after having installed windows, i can access it via refit and go in directly (mbr). then after installing grub, grub overwrote the mbr and assumed the booting job of mbr. so what i had gotten was from refit, i was only able to access window only through grub, even if i click on the windows icon from the refit menu.

i'm not sure if there would be a work-around for my (no longer an) issue, but i wasn't able to find one.

thx anyway for your feedback!

---

### Post by cyberdork33 on 2007-10-02
> **willnight said:**
> pxwpxw, thx for your post. i am actually confused as to what you said though in your last post about grub.

what i know is after having installed windows, i can access it via refit and go in directly (mbr). then after installing grub, grub overwrote the mbr and assumed the booting job of mbr. so what i had gotten was from refit, i was only able to access window only through grub, even if i click on the windows icon from the refit menu.

i'm not sure if there would be a work-around for my (no longer an) issue, but i wasn't able to find one.

thx anyway for your feedback!
Install bootloader (Grub) to the ubutnu partition rather than to the MBR, and install the Windows Bootloader to the MBR. then you can boot directly to either from refit.

---

