---
title: "I've formatted WinXP and I can't boot up Ubuntu"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by FredDre on 2007-06-08
I've formatted the WinXP partition and re-installed it, but now when I reboot the computer I can't see the dual boot menu to select Ubuntu
What should I do?

---

### Post by testube_babies on 2007-06-08
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

The Super Grub Disk has an option that can reconfigure the boot menu automatically, also:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by floke on 2007-06-08
Why on earth did you format the XP partition? 
If you've formatted it then it's gone!
In ubuntu, open a terminal and type 'sudo fdisk -l'
if you see no entries there with NTFS in, then your xp partition is dust my friend.

---

### Post by Najand on 2007-06-08
Try:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by FredDre on 2007-06-08
Because WinXP was working as hell. And I didn't had any important files in there, I've made all my back-ups.
I just want to set up Ubuntu as before

---

### Post by ryanVickers on 2007-06-08
Edit: thanks for clarifying that for everyone, but I got it!:
I think he means that he reinstalled xp, but since it doesn't detect and create a duel-boot option for ubuntu, it's not chowing up - don't worry, ubuntu is still there, but there is no boot option.  Try looking for help on how to configure C:\boot.ini to incluse an ubuntu option, it van't be that difficult.  Once you get it booting ubuntu again though, I would set it to use grub again!

---

### Post by Najand on 2007-06-08
> **ryanVickers said:**
> Edit: thanks for clarifying that for everyone, but I got it!:
I think he means that he reinstalled xp, but since it doesn't detect and create a duel-boot option for ubuntu, it's not chowing up - don't worry, ubuntu is still there, but there is no boot option.  Try looking for help on how to configure C:\boot.ini to incluse an ubuntu option, it van't be that difficult.  Once you get it booting ubuntu again though, I would set it to use grub again!

The link I sent it for recovering ubuntu after installing Windows.

---

