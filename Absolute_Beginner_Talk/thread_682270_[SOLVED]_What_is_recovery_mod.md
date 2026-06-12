---
title: "[SOLVED] What is recovery mod?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by suweihsut on 2008-01-29
I saw[COLOR="Red"] recovery mod [/COLOR]entry in grub menu at boot time, but i don't know what it is. What can i do with it? 
Thanks.

---

### Post by aysiu on 2008-01-29
It logs you in as root (the ultimate administrator account on your system). It allows you to fix certain things that may have gone wrong, as long as you know the right commands to type in.

---

### Post by suweihsut on 2008-01-29
But it don't need me to enter password. If i can modify everything in this mod, someone else can do it too. Is it right?

---

### Post by aysiu on 2008-01-29
> **suweihsut said:**
> But it don't need me to enter password. If i can modify everything in this mod, someone else can do it too. Is it right?
Yes. If you allow someone physical access to your computer, and that person knows what she's doing, you are essentially giving her root access. This would be true with or without recovery mode.

---

### Post by JoshuaRL on 2008-01-29
Yeah, but you would need to know do everything from the command line.  And I think it limits what exactly you can do, you would actually need to log in and use the sudo password to do everything.

---

### Post by suweihsut on 2008-01-29
So if someone can acess my computer physically, i can't do anything save my private data.
Is that right?

---

### Post by JoshuaRL on 2008-01-29
I haven't done it personally, but you could encrypt your drive or your important files/folders.  Another option is to set a BIOS password.  But don't ever forget it, I don't think there's a way to get past it.

---

### Post by iansane on 2008-01-29
If you encrypt the harddrive doesn't it rely on the OS to decrypt at start up? So if you crash there's no way to recove and all your files are still encrypted with no way to decryptr? Sorry not my post. Just butting in to ask :-)

---

### Post by information_entropy on 2008-01-29
By using the GRUB lock and password commands you can secure who can boot in what mode.
I have never tried  this with Ubuntu.


From the grub manual.

13.3.21 lock
— Command: lock
Prevent normal users from executing arbitrary menu entries. You must use the command password if you really want this command to be useful (see password). 
This command is used in a menu, as shown in this example: 
          title This entry is too dangerous to be executed by normal users
          lock
          root (hd0,a)
          kernel /no-security-os
     
[http://www.gnu.org/software/grub/manual/grub.html#lock](http://www.gnu.org/software/grub/manual/grub.html#lock)

---

