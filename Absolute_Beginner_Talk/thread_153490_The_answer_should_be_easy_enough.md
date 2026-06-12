---
title: "The answer should be easy enough"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Abu Imak on 2006-04-01
Hi guys, I'm having problems logging in. For some reason, ubuntu is taking an ETERNITY logging me into gnome. So i figured i'll just create a new user. How do i do that? I would like an answer that explains how to do it both in the terminal and in the GUI. I'm really new to linux so I don't know much.

Also, in case that solution doesn't work. How would I reinstall gnome? I tried doing an apt-get, but it tells me I need a bunch of dependencies or something and I'm not sure how to do that as well. I was able to download fluxbox and openbox but they aren't very nice looking in my opinion.

---

### Post by SkimWear on 2006-04-01
dont know about the terminal.

but heres the GUI version:

System >> Administrator >> Users and Groups

click Add User

then just fill in the blanks.

and add the user :)

Oh by the way, this is for Ubuntu Breezy 5.10

edit: that dependencies problem might be the repositories. i know they arent enabled from default. try doing
System >> Administrator >> Synaptics

go to Settings >> Repositories.

enabled Ubuntu 5.10 "Breezy Badger" (binary) the universal repositories.

then take a look at your Synaptics, it shouldve added more to it.

---

### Post by Abu Imak on 2006-04-01
i'll try that thank you

---

### Post by Mustard on 2006-04-01
[QUOTE=Abu Imak]i'll try that thank you[/QUOTE]

Remember to give yourself sudo privileges, before you go deleting your old account. :)

---

### Post by professor_chaos on 2006-04-01
"sudo adduser name_of_newuser_here"

---

