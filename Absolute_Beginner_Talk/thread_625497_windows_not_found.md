---
title: "windows not found"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by xamasutra on 2007-11-28
hello
soory i just put kubuntu and it s going well but...
i put it at the place of my chinese windows (disc C) and i keep my english windows (disc D)
before i had a choice at beggining between both
now i have no choice at all only kde and it doesn't propose me itself a choice.
how can i go to windows again?
i can no more go to the bios either

---

### Post by xamasutra on 2007-11-28
well i can go to my bios but its not helping me more.
if kubuntu does not find windows what can i do?

---

### Post by rennen01 on 2007-11-28
Please post the the lines under "Other Operating Systems"

```
sudo gedit /boot/grub/menu.lst
```

When you exit the menu.lst file do not save changes.

---

### Post by rennen01 on 2007-11-28
Here is what is says in my menu.lst file at the bottom

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

