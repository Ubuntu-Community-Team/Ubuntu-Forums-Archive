---
title: "Grub Configuration"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by underdog5004 on 2006-04-24
So, I'm dual booting XP and Breezy Badger, but I can't figure out how to make XP my default os in the grub menu. I've tried playing with menu.lst file...but to no avail. my pc is a
======
1.2Ghz AMD Duron
512Mb RAM
200GB Seagate HDD (for $30, thank you black friday)
Nvidia TNT2 Video Card
ps/2 keyboard/mouse


Thanks in Advance

---

### Post by sn123 on 2006-04-24
[QUOTE=underdog5004]So, I'm dual booting XP and Breezy Badger, but I can't figure out how to make XP my default os in the grub menu. I've tried playing with menu.lst file...but to no avail. my pc is a
======
1.2Ghz AMD Duron
512Mb RAM
200GB Seagate HDD (for $30, thank you black friday)
Nvidia TNT2 Video Card
ps/2 keyboard/mouse


Thanks in Advance[/QUOTE]
post the contents of your menu.lst file.

Hint: Look at **default** setting in menu.lst.


S

---

### Post by olsonar on 2006-04-24
This is easy. just change the 'default' setting. It goes by number, so if windows is the 5th in the list, you would set it to 5. I would also reccomend changeing the '# howmany' entry to something like 2 so it only displays the 2 latest ubuntu kernels,  keeping the number that refers to windows a constant.

---

### Post by Qrk on 2006-04-24
[QUOTE=olsonar]This is easy. just change the 'default' setting. It goes by number, so if windows is the 5th in the list, you would set it to 5. I would also reccomend changeing the '# howmany' entry to something like 2 so it only displays the 2 latest ubuntu kernels,  keeping the number that refers to windows a constant.[/QUOTE]
 A note... if it is fifth on the list, you should need to set it as four. Grub counts from zero.

---

### Post by olsonar on 2006-04-24
[quote=Qrk]A note... if it is fifth on the list, you should need to set it as four. Grub counts from zero.[/quote]

Oops. Forgot about that. You could also move the Windows entry above the "AUTOMAGIC KERNELS LIST" section so that it is always 0. That way u don't have to edit anything else.

---

### Post by underdog5004 on 2006-04-24
Wow. I'm so pleased and surprised with the quick response. I have only been a member of this forum for a couple of hours...
Thank you

---

