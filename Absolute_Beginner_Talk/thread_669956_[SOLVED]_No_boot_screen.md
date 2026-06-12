---
title: "[SOLVED] No boot screen"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by wildgene789 on 2008-01-16
Hey guys i just installed ubuntu for 3rd time now hoping i can fix this problem but it seems that it still doesnt work. when i boot my computer i dont get the loading screen with the loading bar it just goes black untill its done loading same thing when shutting down. what should i do?

---

### Post by ARhere on 2008-01-16
My wifes PC does this.  It is simply a problem resolving the native resolution, usually a problem with embedded graphics.  My advice, don't worry about it.

If you want to see something to make sure all is good, then
```
sudo gedit /boot/grub/menu.lst
``` and remove the 'silent' and 'splash' keywords from the bottom boot selection item.

[COLOR=Blue]title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70 [/color][color=red]ro quiet splash[/color]
[color=blue]initrd		/boot/initrd.img-2.6.22-14-generic[/color]
[color=red]quiet[/COLOR]

Hope this helps!  If you want to learn more, there are a LOT of posts that talk about this.  Search for 'faster boot' or 'Ubuntu boots slowly'
-AR

---

### Post by wildgene789 on 2008-01-16
thanks for a fast reply ill do that right away

---

### Post by nikoPSK on 2008-01-16
once you've done so, and fixed the issue, please mark this thread as "SOLVED".

nikoPSK

---

### Post by wildgene789 on 2008-01-17
how do i make it as solved

---

### Post by thelatinist on 2008-01-17
There's a "thread tools" menu at the top of the thread.

---

### Post by nikoPSK on 2008-01-18
> **thelatinist said:**
> There's a "thread tools" menu at the top of the thread.

like this:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

---

