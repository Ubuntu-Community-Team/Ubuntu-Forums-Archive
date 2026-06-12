---
title: "GTK themes problem"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by stesti on 2006-10-29
Hi.
I'm using Ubuntu since September, and I have a problem with GTK2 themes.
I'm using Edgy Eft 6.10, and I've found at art.gnome.org several nice apps theme (like [Outcrop]("http://art.gnome.org/themes/gtk2/1122")), but when I download and install themes via the theme manager it seems that some library are missing, because [they all looks like this]("http://img92.imageshack.us/img92/4390/screenshot1tz5.jpg"), they look like base Gnome theme, and not like, for example, Outcrop.
What can I do?

Thanks,

Stefano

---

### Post by CatKiller on 2006-10-29
I don't know much about it, but have you got the Pixmap theme engine installed?

> Outcrop includes an pixmap engine based theme for 2.x, and a Metacity theme.

GTK+ 2.x theme depends on pixmap engine,

---

### Post by stesti on 2006-10-29
> **CatKiller said:**
> I don't know much about it, but have you got the Pixmap theme engine installed?

Thanks for your answer, but I have that theme engine and I still have this problem... Any other idea? The same think happens with a lot of other themes. I did a clean installation 10 minutes ago but the problem is still here...

---

### Post by CatKiller on 2006-10-29
You could try installing every theme engine you can find - there's a few in the repositories, I think. I really don't understand how it all works, though.

---

### Post by escape on 2007-01-04
You have gtk2-engines-pixbuff installed as well?

Pixmap based themes tend to be a bit buggy- just try Glossy P.

---

### Post by Falcorian on 2007-01-05
I had the same problem with some themes. Installing pixbuff worked for me!

---

