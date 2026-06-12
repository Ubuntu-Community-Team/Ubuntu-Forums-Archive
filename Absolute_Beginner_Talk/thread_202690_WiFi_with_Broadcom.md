---
title: "WiFi with Broadcom"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by davidcrunkmd on 2006-06-23
Why is it so difficult get my internal Broadcom WiFi card to be recognized by ANY distro ?](*,)

---

### Post by Apple 101 on 2006-06-23
Use ndiswrapper.  A search should help you.

---

### Post by Winblowz on 2006-06-23
It's probably because of the chipset the Broadcom card uses.

---

### Post by MarkSheely on 2006-06-23
Which Broadcom card do you have?

--Mark
[email]marksheely@gmail.com[/email]

---

### Post by vigleik on 2006-06-23
Ndiswrapper is probably the way to go. You'll need the windows driver for that. You might also have to remove a module from the kernel, temporarily with something like "sudo rmmod bcm43xx", permanently by blacklisting it. Do a search for bcm43xx and you'll probably find some howto's.

Vigleik

---

### Post by ubunturules on 2006-06-23
[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

---

