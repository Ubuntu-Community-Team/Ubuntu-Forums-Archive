---
title: "Where is Grub stored?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by jtuttle on 2007-07-23
Where is the grub system stored?  I have formatted both my C: and D: drive and it still prevents boot.  How do I get rid of it?

Thanks,

Jerry Tuttle

---

### Post by Orochi on 2007-07-23
GRUB is installed to the Master Boot Record (MBR) of the drive. The easiest way to get rid of it is probably to reinstall XP or Vista, as they overwrite the MBR with their own bootloader. Alternatively you should be able to uninstall it through Ubuntu, although I've never done it so I'm not sure how.

---

### Post by Tsen on 2007-07-23
In the MBR, typically.  Are you trying to remove Linux?  Because otherwise, you don't want to get rid of it.

---

### Post by jtuttle on 2007-07-23
yes,  my goal is to totally remove Ubuntu.  In two days Grub has caused me nothing but trouble.  I like everything else.

Jerry Tuttle

---

### Post by Orochi on 2007-07-23
Well if you like everything else, it's probably a better idea to try to get GRUB fixed rather then get rid of Ubuntu. But like I said, if you're removing Ubuntu you're probably replacing it with XP or Vista. Installing either one of those normally should overwrite GRUB with the Windows bootloader.

---

