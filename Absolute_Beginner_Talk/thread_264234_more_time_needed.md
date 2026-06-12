---
title: "more time needed"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Chuck_W on 2006-09-24
When I start my computer there is a very short window of time where I can hit the escape key to get into the text-based mode. It seems less than 5 seconds. Is there a way to change this? I assume it is a setting somewhere but I have no idea as to where to look.
Thanks

---

### Post by nereid on 2006-09-24
Load /boot/grub/menu.lst in an editor and change the number (time in seconds) behind the *timeout* command.

---

### Post by xyz on 2006-09-24
Hi-
In a console, tape
```
sudo gedit /boot/grub/menu.lst

```
and look for:
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10


change timeout to how many seconds you need.
I think that's what you mean?

---

### Post by Chuck_W on 2006-09-24
Thanks folks. Worked like a charm. For some reason it was only 3 seconds. I reset it to 10 and will see how that works.

---

