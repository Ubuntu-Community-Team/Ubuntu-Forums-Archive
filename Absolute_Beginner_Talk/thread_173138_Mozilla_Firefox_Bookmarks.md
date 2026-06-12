---
title: "Mozilla Firefox Bookmarks"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-09
I've been trying to import my firefox bookmarks all day.

I wrote over the bookmarks.html file that is in /etc/mozilla-firefox/profile (after changing the permissions) with the file from my USB flashdrive, but my bookmarks are still default.

I found two 'SH' files in /usr/bin called firefox & firefox.ubuntu. But they are files, not folders. They do launch firefox when I chose Run instead of Display, though.

So, I'm not sure what I'm doing incorrectly.

When I loaded Portable Firefox on my USB Flashdrive I had to change a file to point firefox to my profile folder (it couldn't see the folder since it wasn't in its default location). I was having pretty much the same problem. But, I can't find anything like that.

---

### Post by ComplexNumber on 2006-05-09
firefox keeps a backup of the bookmarks in the same directory. go into Manage Bookmarks in the bookmarks menu in the main menu. then choose 'Import bookmark'. then 'from file'. then select the file.

---

### Post by aysiu on 2006-05-09
First of all, your bookmarks live in /home/clay/.mozilla

.mozilla is a hidden folder, which you can view by pressing Control-H in Gnome or Alt-V, H in KDE.

But why can't you just launch Firefox and go to Bookmarks > Manage Bookmarks > File > Import?

---

### Post by Clay85 on 2006-05-09
Haha. I didn't know firefox had an import bookmarks feature.

MAN! Talk about making a mountain out of a mole hill. I'm from Windows, so I'm used to complicated procedures for things that should be relatively easy. I guess I learned my lesson. I'm starting to like Ubuntu. :)

Thank you for your help. :)

---

### Post by aysiu on 2006-05-09
[QUOTE=Clay85]I'm from Windows, so I'm used to complicated procedures for things that should be relatively easy.[/QUOTE] In all fairness, this Firefox bookmark import/export feature is available in Linux, Windows, and Mac. It's a Firefox thing that's operating system-independent.

It's always better to find out something is *easier* than you thought it would be than vice versa. Glad it worked out for you.

---

### Post by Clay85 on 2006-05-09
Thanks. Also, I copied and pasted all of my fun firefox add ons into that hidden directory, so thanks for that. Now I don't have to re-download them all.

---

