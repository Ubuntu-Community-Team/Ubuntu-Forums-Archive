---
title: "How to get full permission"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by MiThRaZoR on 2006-10-24
How do I get full permission. Because I want to add a directory to my filesystem and it won't let me do anything on there. I have folders that have nothing in them which I made. I want to delete those.

---

### Post by dillbertdabomb on 2006-10-24
gksudo nautilus

---

### Post by PriceChild on 2006-10-24
You may want to read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for details on sudo.

In a nutshell... precede commands with "sudo" to give admin rights to terminal programs, "gksudo"/"kdesu" for graphical apps.

Use "sudo su -" to gain a root terminal.

Be VERY CAREFUL with "gksudo nautilus", close it when you're finished!

---

### Post by Bachstelze on 2006-10-24
I highly recomment **not** to use gksudo nautilus at all ! Even such a stupid thing as a wrong click-and-drop can have disastrous effects ! Running *sudo rmdir /path/to/dir* is not much hassle I think.

---

### Post by MiThRaZoR on 2006-10-24
Thanks but now I want to write to /etc/ on there.

Better yet, can you tell me how to install FireFox 2.0? It has the tar.gz extension. I have it uncompressed. But I'm trying make it so when I click on the FireFox icon, it goes to FireFox 2.0 and not 1.5.

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/)
^^ If anyone wants to real FireFox 2.0

---

