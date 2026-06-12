---
title: "Grub never loads, straight to windows"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by mickd1337 on 2006-12-19
The same thing happened with windows x64 as with windows vista where an installation of ubuntu according to suggested pretenses, ends up with an automatic boot to the respective windows os. This must be something to do with grub, i automatically choose the (hd0) install to mbr, and have tried different. My windows is in hda1, with linux in hda2 and swap hda3. Hopefully someone can suggest something that can help me to get grub working. Thanks.

---

### Post by simonn on 2006-12-19
Check your bios to make sure it tries booting from hda first.

---

### Post by rccharles on 2006-12-19
> **mickd1337 said:**
> The same thing happened with windows x64 as with windows vista where an installation of ubuntu according to suggested pretenses, ends up with an automatic boot to the respective windows os. This must be something to do with grub, i automatically choose the (hd0) install to mbr, and have tried different. My windows is in hda1, with linux in hda2 and swap hda3. Hopefully someone can suggest something that can help me to get grub working. Thanks.

In the default configuration, doesn't grub boot the default OS after 3 seconds.

Press the esc key after booting to get the grub menu.


Check in your grub menu.

To see it:

cat /boot/grub/menu.lst | more

To edit:
sudo nano /boot/grub/menu.lst

I  changed the timeout to 5 seconds.

timeout    5

And, I put a # in front of hiddenmenu.

#hiddenmenu


Pressing, control-x in nano will ask you to save the file.

Robert

---

### Post by macogw on 2006-12-19
If Grub never loads, then you need to edit the Windows ntldr so that it has an option to chainload to Grub

---

### Post by rccharles on 2006-12-19
Did you by chance install Windows after installing Ubuntu?  Windows XP will overwrite the master boot record.  To re-install grub see:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

I have not tried the suggest.

Take care.

Robert

---

