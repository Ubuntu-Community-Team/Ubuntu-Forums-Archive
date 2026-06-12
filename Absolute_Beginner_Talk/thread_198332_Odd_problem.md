---
title: "Odd problem"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Fireborn on 2006-06-17
Grub shows the same exact things twice when I start my machine up. I don't know what's going on with it and I'd like to remove one set, though I don't really know how. "Ubuntu kernel 2.6.15-25-386" then "Ubuntu kernel 2.6.15-25-386(recovery mode)" These things repeat once.

---

### Post by aysiu on 2006-06-17
Recovery mode is a different thing from the regular boot mode. Recovery mode drops you to a terminal with root access.

---

### Post by x64Jimbo on 2006-06-17
[QUOTE=Fireborn]Grub shows the same exact things twice when I start my machine up. I don't know what's going on with it and I'd like to remove one set, though I don't really know how. "Ubuntu kernel 2.6.15-25-386" then "Ubuntu kernel 2.6.15-25-386(recovery mode)" These things repeat once.[/QUOTE]
Same thing happened to me recently. I'm not sure why - probably has something to do with a program that was updated that called the grub-update program... Doesn't really matter what caused it cause what you need is the solution, right? ;)
If you open your /boot/grub/menu.lst file in your favorite editor (make sure you've got root privs first) you can remove excess entries by either deleting them or commenting them out.

---

### Post by Fireborn on 2006-06-17
Thanks fer the help! I was thinkin for a second that I might have an extra kernel... If that was the problem, I'd still not know what's going on. heh.

---

### Post by defned on 2006-06-18
Thanks for the information on this, I was having this problem also!

---

