---
title: "[SOLVED] What was that program called?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by snakeeyes on 2008-01-08
Hi, I for got the name of the program that would let u choose ur splash screen while booting up and it could also configure the resolution of the splash screen. I want to use it to remove my splash screen so I can see the processes occurring while booting. Its more Unix like that way. ;)

Thanks :)

---

### Post by philinux on 2008-01-08
startupmanager

---

### Post by Dr Small on 2008-01-08
I think you need to remove "quiet splash" from your grub entry at /boot/grub/menu.lst

---

### Post by snakeeyes on 2008-01-08
> **Dr Small said:**
> I think you need to remove "quiet splash" from your grub entry at /boot/grub/menu.lst
THanks for ur reply, when I went to my Grub options I noticed it doesn't say "quiet splash", it says "splash" only instead.

---

### Post by ByteJuggler on 2008-01-08
OK, take out the "splash" then.

---

### Post by snakeeyes on 2008-01-08
That doesn't work for some reason, I tried that.

---

### Post by philinux on 2008-01-08
why not use startupmanager it's so easy.

---

### Post by snakeeyes on 2008-01-08
I am using Kubuntu.

---

