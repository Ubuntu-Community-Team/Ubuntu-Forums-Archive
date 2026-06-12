---
title: "Cannot get Boot camp to Load Ubuntu"
date: 2009-10-10
forum: Apple Hardware Users
---

### Post by Ravernomina on 2009-10-10
Hello as the title says Bootcamp will not Load Ubuntu. I know their is rEFIt but i HATE IT. I keep getting "missing operating system" error and i do not have a clue how to fix. Could someone please give me a solution please. Thank you (:

---

### Post by Ravernomina on 2009-10-11
Bump

---

### Post by cool2000m on 2009-10-12
i'm pretty sure the default bootloader does not support linux booting, unfortunately. it's probably a format issue. looks like the only way to fix this is to use rEFIt. sorry. :(

---

### Post by cool2000m on 2009-10-12
one good thing when it comes to refit is the 'sync' utility, which syncs the hdr tables (linux/windows) with the EFI (mac). if you do try to use that, you'd need to install grub to the ubuntu partition first, and then before ANYTHING sync the tables (since they have been edited by the installer) and you should be fine.

also, you could try installing ubuntu on a FAT partition, although I do *NOT* reccomend it.

---

### Post by fbugnon on 2009-10-12
I've been using rEfit for a while now and I acutally like it. *But before I had just installed Ubuntu sideways with MacOSX (boot campo method), and use to use the "alt" button to get the choice in between the OSs, it worked fine, never had a problem.

I'm not sure I understood your point - do you want Linux-only, is that what causes the EFI problem?  (sorry for my slowness)

---

### Post by Ravernomina on 2009-10-12
I got It to work just needed to install GRUB On my Linux Partition HDA (0,3)

---

