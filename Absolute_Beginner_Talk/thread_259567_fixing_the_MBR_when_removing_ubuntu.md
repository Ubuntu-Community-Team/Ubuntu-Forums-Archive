---
title: "fixing the MBR when removing ubuntu"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-09-17
Hi everyone. According to this page: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

It says to boot from your Windows XP CD and choose "recovery console" mode, then use the fixmbr command. But when I try to boot from my CD, it just takes me to the regular boot screen where I have to choose between Ubuntu and Windows. Does anyone know why this is, and how I might force a boot from the disc so I can fix the MBR?

Thanks.

---

### Post by Kilz on 2006-09-17
> **JohnJSal said:**
> Hi everyone. According to this page: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

It says to boot from your Windows XP CD and choose "recovery console" mode, then use the fixmbr command. But when I try to boot from my CD, it just takes me to the regular boot screen where I have to choose between Ubuntu and Windows. Does anyone know why this is, and how I might force a boot from the disc so I can fix the MBR?

Thanks.

Get a windows 98 boot floppy, boot from it, then type in ```
fdisk /mbr
```

---

### Post by jordanmthomas on 2006-09-17
Can you boot off of your Ubuntu CD?  If not, you need to follow the same steps to boot off a CD when you installed Ubuntu.

---

### Post by Eric Plumrose on 2006-09-17
That sounds like you are not booting from the CD

You will have to go into your BIOS
It normally says press delete or f2 for setup when you start the computer.

Then find the boot options and change it so the CD is first in the boot order.

---

### Post by JohnJSal on 2006-09-17
Thanks guys. But I tried an alternate method that was also on that website (downloading the MbrFix utility) and that worked in a matter of seconds! :)

---

