---
title: "InitNG"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-01-27
Hello,


I followed the instructions from here:

[http://ubuntuforums.org/showthread.php?t=80423](http://ubuntuforums.org/showthread.php?t=80423)

to install this and it works beautifully but the only problem is that I would like it to boot from it immediately rather that me having to go to the GRUB menu and select it as this makes the endevour a little pointless as the time spent doing this negates some of the effect of InitNG.

Thank you very much

---

### Post by ubuntuuser on 2006-01-27
I cross-read that Howto you mentioned, and I guess that you changed you menu.lst accordingly. To select that InitNG entry as default look for the line ```
default        0
``` and change it to the correct number. Just count the uncommented lines starting with the word title, and remember that grub starts counting with 0, so the fourth entry in your menu.lst would lead to ```
default        3
```

---

### Post by xXx 0wn3d xXx on 2006-01-27
I can't get it to install...how did you ? I get arcive not found after I download it and try to install.

---

### Post by Dr Von Bon Bon on 2006-01-27
In mine i have something that says "savedefault".


When i tried booting it it just didn't work.


Any ideas?

---

### Post by xXx 0wn3d xXx on 2006-01-27
ok, I got it to work thanks :)

---

