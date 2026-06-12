---
title: "[SOLVED] NTLDR MIssing error after update."
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by dredd999 on 2007-09-26
i accepted the updates last night (25/09/07) and all seem to go alright , it asked to be rebooted which i did and the grub menu came up i could see the order of what os to load up had changed, it had gone back to what it was when i first installed ubuntu. i had put xp pro as first one to be loaded (for wife so that she can use computer). now xp pro is last option and am getting NTLDR MIssing error when i try this ..have tried Tiny Empire's Fixntldr program and at the moment can boot to xp pro using this..just wondering if anyone else has had the same problem.

---

### Post by e_james on 2007-09-26
On one of my machines it's the ubuntu 7.04 boot sequence that gets corrupted by some updates. There seems to be some sort of template stored somewhere which is used to create the grub menu.lst file and sometimes that template is wrong. In my case I can boot ubuntu successfully by editing the grub commands. Did you know you could do this? You do need to know what the correct commands are. If you had it working before, maybe you can remember.

If necessary the grub manual should help. I got most of what I needed from here
[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

By the way you can edit menu.lst to change the default OS to boot. It is probably not a good idea to change the order.

---

### Post by dredd999 on 2007-09-29
managed to find out what was wrong, after a bit of reading and searching all i had to do was edit menu.lst .

# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

to

# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by e_james on 2007-09-29
I suggest you keep a backup copy of menu.lst for reference. It is possible that the next kernel update wiil corrupt it again. Unless you have set a limit to the number of bootable kernels, it will almost certainly change your default OS.

---

### Post by dredd999 on 2007-09-29
already done that made a couple of copies of men.lst..thanks

---

