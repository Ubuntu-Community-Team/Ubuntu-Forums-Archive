---
title: "apt-get upgrade"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by polar05 on 2005-09-18
Hi, I'm running hoary hedgehog and I wanted to get the latest versions of installed packages so I did an apt-get upgrade.  I was pretty surprised to find that this killed the customizations I had made to xorg.conf and grub's menu.lst.  Does apt-get back up these configs somewhere?  That sucker is dangerous!

---

### Post by mlomker on 2005-09-18
Hmm.  I'm not surprised by grub because that gets regenerated a fair bit.  If you've modified the setup before then you know it's /boot/grub/menu.lst.  The editors that I use tend to make a backup and that's always been good enough for me.

Your xorg.conf experience is atypical.  Indeed, many people upgrading to breezy can't get a graphical login because the install *will not* overwrite the xorg.conf, even though you can't boot a hoary xorg.conf on breezy without making a few changes.

---

