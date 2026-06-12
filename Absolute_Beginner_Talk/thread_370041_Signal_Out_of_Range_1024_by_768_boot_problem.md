---
title: "Signal Out of Range 1024 by 768 boot problem"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by sssidddd on 2007-02-25
[IMG]http://img404.imageshack.us/img404/1315/p2250011ax5.jpg[/IMG]

Thats the problem I have when I bootup. After some time, I see the Ubuntu log in form and I log in.

Any ideas on how to change that? Is it just a problem with my monitor?

I cant see anything while it's booting up except the Packard Bell vendor's screen.

Please help.

Thanks,

Sid M

---

### Post by n8bounds on 2007-02-25
try adding ```
 vga=791 
``` to your kernel parameters (in grub) before booting linux

---

