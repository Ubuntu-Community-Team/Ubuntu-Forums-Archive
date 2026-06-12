---
title: "Grub Booting Issue"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by leodirk on 2008-01-14
I have had Ubuntu installed for awhile and after I installed Vista on my main HD it killed the grub MBR on it. I can't get linux to boot anymore even if I select the HD it is on in the boot menu. I tried installing Easy BCD and that helped rewrite the MBR to see my Vistaand XP partition and I tried to set it to see the linux one but it wont start up. I figure if I could get grub to install on the HD linux is on I could just use Easy BCD to load that grub, or just use the boot menu and select that HD. My set up is
IDE1 Master: Vista, XP
IDE1 Slave: Storage
IDE2 Master DVD
IDE2 Slave: Linux

Thanks for your help, sorry if this isn't making any sense it is really loud where I am typing ATM so I can't think straight lol

Oh and when I tried to use a UUE 6 Ubuntu Live CD to try the tutorial [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") there it didn't work. It couldn't find the stage1 file and none of the other commands worked either, they all displayed errors.

---

### Post by wolfen69 on 2008-01-14
restore grub [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

edit: sorry, didnt notice you already tried this link.

---

### Post by logos34 on 2008-01-14
> **leodirk said:**
> I tried installing Easy BCD and that helped rewrite the MBR to see my Vistaand XP partition and I tried to set it to see the linux one but it wont start up. I figure if I could get grub to install on the HD linux is on I could just use Easy BCD to load that grub, or just use the boot menu and select that 

Try[ Super Grub Disk]("http://supergrub.forjamari.linex.org/").  

Remember to install Grub to the root partition as well (EasyBCD requires this).

---

