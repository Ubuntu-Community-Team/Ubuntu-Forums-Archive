---
title: "Lost XP as default in menu.lst after update"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by monton on 2008-04-15
I just did a series of updates and on reboot my menu.lst is new/changed.
This is a dualboot XP/7.10 system that I had set XP as the default OS.
Now XP isn't even on the OS option list at all.
How do I edit the menu.lst file so that XP shows as an option and is the default OS?
Thanks for any help
Monton:confused:

---

### Post by arochester on 2008-04-15
You get XP as default by changing a number. Linux might be 1,2 and 3 and XP 4. When you get a new kernel and don't delete the old, Linux might become 1,2,3,4,5, and 6 and XP becomes 7. If you have previously told it to boot into 4 (by default) that's what it will still do ... an old version of Linux. Either delete the old kernel or change the number again.

---

### Post by Penteado on 2008-04-15
Hi, dunno if this will help. But try getting a startup manager


  ```
sudo apt-get install startupmanager
```

---

### Post by Paqman on 2008-04-15
> **monton said:**
> I just did a series of updates and on reboot my menu.lst is new/changed.
This is a dualboot XP/7.10 system that I had set XP as the default OS.
Now XP isn't even on the OS option list at all.
How do I edit the menu.lst file so that XP shows as an option and is the default OS?
Thanks for any help
Monton:confused:

To edit the menu.lst as root throw this into a terminal:

```

gksudo gedit /boot/grub/menu.list

```

The default number is right near the top. Scroll waaaaay down to the bottom to see the different boot options.

Your Windows entry should look something like:

title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

If it's not there just add it in. If Windows is not the first partition on the disk you will need to change the "root (hd0,0)" entry to reflect that.

---

### Post by indytim on 2008-04-15
Another option if you want to "de-kernalize" (( my term)) your GRUB loader is to build a dedicated GRUB partition.  See the link in my sig for details on how I did it.

IndyTim

---

