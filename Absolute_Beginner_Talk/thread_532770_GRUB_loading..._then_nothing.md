---
title: "GRUB loading... then nothing"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by domibud on 2007-08-23
I just get back my broken harddrive from the vendor. All the data had been restored. Now, my GRUB is not working at all (just showing GRUB loading...). I don't know what are the problems. That harddrive has 5 partitions, hda1 (NTFS - Windows XP), hda 5 (NTFS), hda6 (ext3 - Ubuntu 6.06), hda7 (NTFS), hda8 (swap). I tried to reinstall GRUB, but I failed.

Can anyone give me a step by step on how to reinstall GRUB?

Or a link that has the explanation about reinstalling GRUB?

---

### Post by steve.horsley on 2007-08-23
If you have the Ubuntu installer disk still, then I would boot that and choose the option to restore a broken system. Tell it to use hda6 as the root partition, and then run this command:
sudo grub-install /dev/hda

Or you could use the GRUB superdisk - see these instructions:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by domibud on 2007-08-28
Thanks for your help. Now, I can use my windows and Ubuntu...

---

