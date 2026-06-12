---
title: "No Virtual Console, just flashing colors"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by SkipBlue on 2007-08-23
When I do ctrl+alt+F1 instead of going into virtual console, I get random flashing colors. Can anyone help me?

---

### Post by jamvegan on 2007-08-24
That sounds...very strange.  Have you confirmed that there is a tty running there, such as with the following?
```
ps -e | grep getty
```

---

### Post by gcornett on 2007-09-23
Although the original poster has not replied to jamvegan's question, I am having the same problem since upgrading from Dapper to Edgy.  I did run the command and this is what I got:

gcornett@thales:~$ ps -e | grep getty
 4385 tty1     00:00:00 getty
 4386 tty2     00:00:00 getty
 4387 tty3     00:00:00 getty
 4388 tty4     00:00:00 getty
 4389 tty5     00:00:00 getty
 4390 tty6     00:00:00 getty

Thanks for any help you can give.

---

### Post by gcornett on 2007-10-28
Well, I came up with a workaround.

I added 'vga=ask' to the kernel line in the first option in menu.lst for grub. When I rebooted, grub displayed a list of video options.  I chose the first, 80x25.  That got the consoles working.  

Warning to other newbies here: Research grub and menu.lst on the forums before trying to modify it.  And back up the file before you change it!

---

