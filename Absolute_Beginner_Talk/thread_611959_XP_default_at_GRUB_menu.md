---
title: "XP default at GRUB menu"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-11-13
Hello,

I searched around on these forums and count not find many solutions to my problem.  The ones i did find were a little vague for me.  Can someone walk me through setting Windows XP as the default OS in the Grub menu?  I am dual booting Windows XP Professional and Ubuntu 7.10.

TIA

---

### Post by fatfranko on 2007-11-13
go to terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

move this:
```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

to above this:
```
### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by ITdrummer on 2007-11-13
thank you.  That is more of what i was looking for.

---

