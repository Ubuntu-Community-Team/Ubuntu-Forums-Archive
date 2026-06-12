---
title: "Not clear about a part in the unofficial guide, help please."
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by karma on 2005-12-14
I am reading the part beloq on the unofficial Guide


```

Q: How to change default Operating System boot-up for GRUB menu?

   1. Read General Notes
   2.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

   3. Find this line

...
default         0
...

   4. Replace with the following line

default         X_sequence

   5. Save the edited file (sample)

```

My Question:
I am not sure about one thing. Does "X_sequence" mean a Caps "X" "_" followed by "sequence", or is it that "X" represents a number that have to be replaced with an actual number (eg., 2_Sequence)??


Thank you.

---

### Post by aysiu on 2005-12-14
The numbering probably goes as follows:

0 Ubuntu
1 Ubuntu recovery mode
2 Ubuntu memtest
3 other operating systems
4 Windows

If you wanted Windows to be the default, you'd change it from ```
default 0
``` to ```
default 4
```

---

### Post by karma on 2005-12-14
Thank you for the explanation, I will try that.

ubuntu is getting exciting everyday.

---

