---
title: "Evince disfunctional after update?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by itayshom on 2008-01-19
Hello all,

All of a sudden I cannot view PDFs and DJVUs with Evince on Gutsy. I still see the preview in Nautilus, but when Evince starts, it only shows the large 'Loading' text but never goes to show the contents.

Everything worked fine till now. Now all my documents are undisplayable. That's very annoying.

The only thing I can think of is some update from the last few days. Currently no more updates are available for my system.

Can anyone help me with this?

Itay.

---

### Post by jeffus_il on 2008-01-19
Evince is dependent on the [libpoppler-glib2]("http://packages.debian.org/sid/libpoppler-glib2") library to display pdf's and the [libdjvulibre15]("http://packages.debian.org/sid/libdjvulibre15") to display DjVu, Are these packages installed on your system?

&#1489;&#1492;&#1510;&#1500;&#1495;&#1492;

---

### Post by itayshom on 2008-01-19
Yes, they are both installed. The problem only started a few days ago; everything was fine until then.

Thank you.

Itay.

---

### Post by jeffus_il on 2008-01-19
Use synaptic to see the history of installs for the past few days, there may be a hint there.

---

### Post by itayshom on 2008-01-19
I did. In the past month I only installed Wammu. Besides that I just follow the update manager. There were quite a few updates last month (evolution, cups, avahi, gimp, etc..) and of course xorg-core. libxfont was updated, could this be it? Why am I the only one to report this problem if it's just an update issue?

I might be worth mentions that I haven't rebooted recently.

Thanks again.

Itay.

---

### Post by jeffus_il on 2008-01-19
Rebooting would be a good idea, doesn't cost much :wink:

---

