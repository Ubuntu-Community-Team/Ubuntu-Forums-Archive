---
title: "Updating GRUB"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-12-12
Here is what I did...

I installed Windows Vista, then I installed Ubuntu Gutsy. I later on wanted to go back to Windows XP since I was having a bit of trouble getting things to work in Vista and I installed Windows XP on over Vista. I then used my Gutsy live cd, to put GRUB back on since the XP installer removed it. However, the GRUB boot menu still says Windows Vista/Longhorn (Loader) and not Windows XP  (however it still loads windows xp).  How can I update grub so that it can it can detected windows xp and update the grub boot menu?

---

### Post by meborc on 2007-12-12
you can change the title that is in grub menu by editing the /boot/grub/menu.lst file

be sure to make a bacup first```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```search for the VISTA and change the title to whatever ("wind-blows" is my favourite) this section should be in the end of the file

---

