---
title: "What is the &quot;staff&quot; group?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Frogbarf on 2008-02-10
Some of the directories in /usr/local/share have the group "staff" but there is no such group and I can't create one. Attempts to create one and add users to it don't work: the group just quietly evaporates after exit the relevant dialogues.

What is going on?

---

### Post by smartboyathome on 2008-02-12
I think that group just makes it so that other stuff can modify the stuff, but isn't really a user group. Dunno, though.

---

### Post by Patsoe on 2008-04-24
The group disappears after you create it, because you can't really create it: it already exists. For some reason, the Gnome dialog does not show all groups that exist on the system (I have a Debian Etch machine where I can at least tick a box "show all users/groups", but on Ubuntu Hardy it simply doesn't show all of them). If you want to see all groups, look in /etc/group (and "man group" explains how to interpret that file).

The idea behind the staff group is explained here: [http://www.debian.org/doc/manuals/securing-debian-howto/ch12.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ch12.en.html) (long page, so just search for staff :))
I actually ran into your post because I was looking at this too: [http://ubuntuforums.org/showthread.php?t=763637](http://ubuntuforums.org/showthread.php?t=763637)

---

