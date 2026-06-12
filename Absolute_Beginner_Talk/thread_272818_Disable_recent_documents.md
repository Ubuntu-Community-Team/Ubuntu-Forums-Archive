---
title: "Disable recent documents"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by thoeng on 2006-10-07
Hello there i was just wandering is there a way to turn off the recent documents under places as i don't need them and i find it exposing my files to other user

---

### Post by mitch.c on 2006-10-07
> **thoeng said:**
> Hello there i was just wandering is there a way to turn off the recent documents under places as i don't need them and i find it exposing my files to other user

From the Ubuntu Desktop Guide:
> To hide Recent Documents from the Places menu, open a terminal and run the command:

```
chmod 400 ~/.recently-used
```

To enable it again, run the command:

```
chmod 600 ~/.recently-used
```

---

### Post by jaboua on 2006-10-07
As permission 4 still grants reading access, I would have done "chmod 000" instead - I remember using that once before, you will get errors if you start an app from terminal, but everything works. An alternative would be to run "echo > ~/.recently-used" before making it read only - that will empty the file.

---

### Post by mitch.c on 2006-10-07
> **jaboua said:**
> As permission 4 still grants reading access, I would have done "chmod 000" instead - I remember using that once before, you will get errors if you start an app from terminal, but everything works. An alternative would be to run "echo > ~/.recently-used" before making it read only - that will empty the file.
I think the idea behind the 400, is that if there is no write access, no new entries will be written. You'll want to clear the current entries first obviously.

---

### Post by wh0rd on 2006-12-13
It doesn't seem to work!

---

### Post by Rab22 on 2006-12-24
I've had problems with this method as well now. Worked great in GNOME 2.10 and 2.12 days, but lately (2.14, 2.16) it doesn't seem to work. 

I've been trying to resolve this issue for a few days now.

I've noticed that there is now two files associated with recently used documents: 
.recently-used
.recently-used.xbel

When I open a document an entry is created in both files. When the "clear documents" item is selected, only those documents inside the '.recently-used.xbel' are removed. I have attempted at setting both files with permissions of 400 and 000 and neither of which worked. 

I'm starting to wonder if this could be a bug. The first .recently-used document, to me, seems as though it should be cleared upon selecting the option. Unless of course, this document is used by applications,  but this should be defined somewhere (probably is and I just haven't found it yet).

A file that keeps appending records upon each new file opened would get significantly large in a short time. I have several entires already and I've cleared the document a couple times.


Does anyone else have any thoughts on how this works or any idea on how to turn off this feature?

---

### Post by otaviofcs on 2006-12-30
Hy Rab22,

It seems to me that gnome are moving the recently used to that new file recently-used.xbel. The old one i think they kept for compatibility matters.

What you can do, if it's bothering you is put the ine above in your ~/.bashrc file:

echo "" > ~/.recently_used

It will clean your .recently_used file each time you log in.

---

