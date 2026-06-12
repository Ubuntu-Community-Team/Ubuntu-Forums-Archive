---
title: "Help with printing in 7.10"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by mpfeif101 on 2007-10-27
Hi guys, simple question hopefully with a simple answer.

I used to have Feisty, 7.04, and installing my printer was a breeze.  I just went to Add Printer -> Network Printer -> Unix Printer -> then typed in the ip address and queue.

I see no similar option in 7.10?  I go to New Printer but there's no option for that.  I tried LDP but it has hostname and printer name, not ip address and queue.

Thanks so much for any help :)

---

### Post by caffienefree on 2007-10-27
I seem to be getting host and queue... Does your prompt look like this?

---

### Post by mpfeif101 on 2007-10-27
That's the screen I got in 7.04, but in 7.10 I get this:

---

### Post by caffienefree on 2007-10-27
See if the command gnome-cups-manager does anything on your system... if so, and it works, add it to your menu by right clicking on system> edit menus, and add the command as an item in administration. If not, sudo apt-get install gnome-cups-manager.

Oddly enough, I have both on my system...

---

### Post by mpfeif101 on 2007-10-27
Thanks!  Worked liked a charm :)

Wonder why they took that out for 7.10...

---

