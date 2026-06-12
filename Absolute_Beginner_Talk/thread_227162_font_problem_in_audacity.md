---
title: "font problem in audacity"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by mathieuS on 2006-08-01
Hi, i installed audacity using apt-get, under Ubuntu 6.06.

my problem is that the font does not look right. in some places the text is a bit too big for the container. also, in the "about" window, the text only shows squares.

anybody knows which font i could be missing ?

i recently ran easyUbuntu to add extra fonts, but still same problem with audacity.

many thanks

mathieu

---

### Post by Perfect Storm on 2006-08-01
Can you post a screenshot of it?
It may be because that Audacity is using the GTK1 engine while the rest of gnome is using gtk2 engine.

---

### Post by mathieuS on 2006-08-01
ok, the screenshot should be attached to this post.

cheers

mathieu

---

### Post by mathieuS on 2006-08-01
anybody got an idea ?

---

### Post by mathieuS on 2006-08-01
so i got an answer from the audacity forum. apparently it is a known issue.

[http://audacityteam.org/forum/thread/2343](http://audacityteam.org/forum/thread/2343)

---

### Post by dentament on 2008-02-03
I had the same problem, affecting every gtk1 application, solved by editing /etc/gtk/gtkrc.utf-8 so that it states

```
style "default-text" {
        fontset = "-*-helvetica-medium-r-*-*-*-120-*-*-*-*-iso10646-1"
}
class "GtkWidget" style "default-text".
```

That is, you have to edit your "/etc/gtk/gtkrc.[your locale charset, utf-8 by default]" and specify a font you like as "fontset" (you can choose the font by running xfontsel).

Bye

---

