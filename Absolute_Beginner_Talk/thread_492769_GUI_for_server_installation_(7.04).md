---
title: "GUI for server installation (7.04)"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by 5circles on 2007-07-05
I suspect this is a dumb question, but the installation documentation doesn't make it very clear.

I installed the server version of Feisty Fawn.  It doesn't appear that there is any GUI installed or configured.  When I try to run startx, the message is that it is not installed.

If I want to use a graphical interface for administration, do I need the desktop version instead?  Do I lose any server features or performance?

Thanks

---

### Post by moredhel on 2007-07-05
install ubuntu-desktop

in terminal type:

```
sudo aptitude install ubuntu-desktop
```

Most people would probably say it's a waste to have a gui on a server, but I dunno, I'm not a server person.

---

### Post by coolen on 2007-07-05
Yeah, no GUI for the server. You can install ssh easily enough (thus eliminating the need for a monitor). SSH also supports X forwarding over a network, so if you install graphical text editors and such, you can do some stuff graphically from your desktop.
Alternatively, install ubuntu-desktop for a full desktop experience with server capabilities. Shouldn't be a massive performance hit. If it's old hardware, try xubuntu-desktop instead.

---

### Post by 5circles on 2007-07-05
Thanks.  Somehow I managed to post twice, but in any case I'm trying the desktop.

---

