---
title: "How can I delete files using the terminal?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-06-04
Hi,

I've been trying to install aiglx/compiz but I failed and now I have no panels/window borders. I need to delete this compiz file in /etc/xdg/autostart that I put there, but I can't seem to do it from nautilus. However, I managed to access the terminal through /usr/share/applications and now I can reach the file . But, alas, I am a newbie and still don't know my way around the command line. :(  How can I delete that file using the root terminal I found in usr/share/applications?

Thanks!

---

### Post by croak77 on 2006-06-04
rm for user and sudo rm for root.

---

### Post by aysiu on 2006-06-04
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by CompShrink on 2006-06-04
if you got a terminal, type in:

gksudo nautilus

and you'll get the comfy file manager back, with permission to delete that file. When you have time, learning some basic command line operations isn't a bad idea.

---

