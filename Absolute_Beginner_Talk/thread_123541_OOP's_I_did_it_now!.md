---
title: "OOP's I did it now!"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2006-01-30
Ok I did something that took my admin powers away. Now when I try to do admin stuff I get something back saying something about child 1.

How do I get back in to correct this? 
Can it be corrected or do I need to do a reinstall?

---

### Post by kont.raen on 2006-01-30
First, you need to boot into the recovery mode (restart the machine, then choose the recovery mode in the grub boot-menu).

When the machine has booted you are presented with a root console, e.g. 

```
mymachine:~# 
```

there you have to type 

```
mymachine:~# adduser bill admin
```

be aware that you have to substitute bill with the username you actually have on your machine.

After you did that, reboot the machine with

```
mymachine:~# init 6
```

That should do the trick

---

### Post by Micro Rotors on 2006-02-02
Thanks kont.raen,

I cant belive I did that.

Worked like a charm.

Thanks
Again

---

