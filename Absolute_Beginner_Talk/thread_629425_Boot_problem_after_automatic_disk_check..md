---
title: "Boot problem after automatic disk check."
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by A1dan on 2007-12-02
Today my family's box Did an automatic disk check, after it had finished and subsequently booted into Gutsy the systems ntfs partition was unavailable and upon reboot it will not read the boot information to boot into the grub OS selection screen. I'm sorry I cant be much more specific (I have just come home and been told that its broken.) I'm just using the standard Gutsy x86 edition and default boot loader from the live cd.
Any further info needed please ask, any suggestions as to whats wrong here?
Thank you.

---

### Post by PmDematagoda on 2007-12-02
I suggest that you use [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") to try and reinstall GRUB to the MBR.

---

### Post by A1dan on 2007-12-02
Thanks for your suggestion,
the SuperGrub disk has enabled me to boot Ubuntu. It seems that my second disk containing an ntfs partition and xp installation is not reading properly though partition manager gives incorrect information regarding it, and grub/Supergrub cant boot it. this was fine before the automatic disk check. So im guessing that it changed it some how, any ideas?
Thanks again.

---

### Post by ajgreeny on 2007-12-02
I suggest you restore the windows MBR if it is WinXP with the recovery module on the install CD (no idea about vista!) and then reinstall grub with the live ubuntu CD.  Plenty of detail in the forums on how to do this.

---

### Post by A1dan on 2007-12-02
Maybe I'm not using it properly but the "fixmbr" command in windows recovery console has done nothing to help the ntfs partition which is displaying as unpartitioned space now. Anybody know what the disk check could have done to cause this and any other way of reversing that? Because I would really like to be able to salvage the data on that partition.

---

