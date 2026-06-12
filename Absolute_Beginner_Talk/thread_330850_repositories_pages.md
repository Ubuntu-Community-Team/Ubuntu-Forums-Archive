---
title: "repositories pages?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-03
How do I create the page to paste on repositories? I mean, what is the page that usually needs to be psated on the repositories place on the synaptic? I had had some problems because I am  searching for a page to update the synaptic, but I had only find one for wine. So what is the page? is that where you download the program usually or how does it works? Actually I'm searching specifically for the one for vmware

---

### Post by userundefine on 2007-01-03
I'm not exactly sure what you're asking, but if you mean the file where you can add new repositories, that file is located at /etc/apt/sources.list.  In a terminal, you can simply type **sudo gedit /etc/apt/sources.list** and then add the new repositories.

---

### Post by Jorge32 on 2007-01-03
no, how can I find repositories, I mean the thing that goes there.

---

### Post by userundefine on 2007-01-03
Depends on what kind of programs you're looking for.  Most will be in universe or multiverse, Debian repositories.  There isn't a VMWare repository I know of, and you will likely not be able to get it from anything but an unofficial repository if at all.  Otherwise, you'll have to download the package specifically from VMWare's website, either in RPM or DEB format.

You can check out the large thread in the FAQ forum here about installing VMWare.  There's a good howto there that tells you all you need.

---

