---
title: "Ubuntu rEFIt Penguin Disappeared"
date: 2009-12-05
forum: Apple Hardware Users
---

### Post by undoIT on 2009-12-05
I've got Ubuntu 9.10 Karmic installed on my Macbook 5,1 and I'm using rEFIt 0.13 to manage boot. It seems that rEFIt doesn't recognize Ubuntu 9.10 as a Linux OS because instead of the penguin icon, I get the legacy OS icon. The penguin icon was working with Ubuntu 8.10 - 9.04. Does anyone know how to fix this?

It's not a big deal, I just like the penguin better than four grey squares :)

---

### Post by tom4everitt on 2009-12-05
I think its because 9.10 is using grub2 rather than grub. So I guess you could simply down grade to grub in ubuntu, and it should work. I really wouldn't consider it worth the effort though :P

---

### Post by thinktyler on 2009-12-05
Ya I wish I could have the penguin back.

---

### Post by undoIT on 2009-12-05
> **tom4everitt said:**
> I think its because 9.10 is using grub2 rather than grub. So I guess you could simply down grade to grub in ubuntu, and it should work. I really wouldn't consider it worth the effort though :P

Yeah, not worth it. I may dig around in the rEFIt install and see if I can replace the legacy OS image file with the Linux image file.

---

### Post by undoIT on 2009-12-05
Okay, that was easy.

in OS X navigate to /efi/refit/icons

copy os_linux.icns and paste to desktop

move os_legacy.icns to trash

rename file on desktop to os_legacy.icns and move back to /efi/refit/icons

Long live the penguin!

---

### Post by CJN on 2009-12-06
Or you could just sync the partitions ala: [http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229) that worked for me, and then you can use the mac "option bootloader" without refit, or at least it's working fine for me. (note that updates to grub2 will require that you repeat these steps but it's more of a solution rather than a hack)

---

### Post by tom4everitt on 2009-12-06
@undoIT

Aah, of course! Didn't think about it :)

---

### Post by kev0153 on 2010-02-05
awesome post, I just got tiple boot working with my macbook pro and noticed that tux wasn't showing up.  I couldn't figure out why.

---

### Post by Craigular.B on 2010-06-02
As of March 7, 2010 rEFIt has been updated to properly detect grub2. I just installed it on my Macbook Pro (after having done the icon swap), and it replaced the icons to the correct name, and then when rEFIt came up I had the penguin graphic and "Boot Linux from Partition 4" instead of "boot legacy OS..."

So, all is good and fixed! :)

---

