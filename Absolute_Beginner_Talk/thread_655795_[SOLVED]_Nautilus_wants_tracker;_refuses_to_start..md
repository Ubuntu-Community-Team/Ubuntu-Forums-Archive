---
title: "[SOLVED] Nautilus wants tracker; refuses to start."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Vadi on 2008-01-01
> vadi@vadi-laptop:~$ nautilus
nautilus: error while loading shared libraries: libtrackerclient.so.0: cannot open shared object file: No such file or directory
vadi@vadi-laptop:~$ 


I already have libtrackerclient0 package installed. What can I do?

(I -hate- the tracker thing because it only abuses my HD, but I need nautilus more, so I can live with it. Until my harddrive dies from all of the abuse that is).

---

### Post by blueridgedog on 2008-01-02
Checking the obvious first:

Do you have the file?

sudo find / -name libtrackerclient*

It should be in /usr/lib/

---

### Post by philinux on 2008-01-02
An idea maybe to use synaptic and reinstall tracker then in prefs indexing just turn it off by unchecking the two tickboxes.

---

### Post by Vadi on 2008-01-02
I reinstalled the libtrackerclient0 package and it starts now, whew.

---

### Post by crjackson on 2008-01-02
> **philinux said:**
> An idea maybe to use synaptic and reinstall tracker then in prefs indexing just turn it off by unchecking the two tickboxes.

Turning off indexing is one of the 1st things I do on a new install.  With this turned off, does tracker cause any performance reduction?

---

### Post by Vadi on 2008-01-02
I think it's OK with it off.

That program is horribly broken. It said it would take "a few minutes" to merge indexes - I left my laptop on for two nights in a row, and it was still merging. I stopped it because I didn't want my brand-new 7200rpm HD going down so quickly.

---

### Post by philinux on 2008-01-02
Most people think it's a performance improvement with it turned off. :)

---

