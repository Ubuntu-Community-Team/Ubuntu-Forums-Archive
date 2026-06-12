---
title: "Pause screen output"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Streetwalker32 on 2006-10-21
If I type mysql> \h

I cannot read the first part of the text. It scrolls very quick. How do I pause the screen output or view one page ast a time ?

---

### Post by StormNet on 2006-10-21
The command you are looking for is the less command, but you will want to pipe it. For instance the /boot/grub/menu.lst file is longer than my current terminal, so i would use it like this if i wanted to look at the contents of the file:
> cat /boot/grub/menu.lst | less
This allows me to scroll up and down a page or line at a time using the arrow keys or the PgUp/PgDn keys.

---

