---
title: "Openbox - where is menu.xml? (config file)"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by paul6 on 2006-10-19
I can't find the config file for Openbox. According to the wiki [here]("https://help.ubuntu.com/community/Openbox") it should be under ~/.config/openbox/ . But when try to browse to that directory:

paul@ubuntu:~$ cd ~/.config/openbox
bash: cd: /home/paul/.config/openbox: No such file or directory

"locate menu.xml" does not find it either.

---

### Post by jordanmthomas on 2006-10-19
Have you installed obconf?
Install that and run it
```
sudo aptitude install obconf
onconf
```

It should make the config for you.

---

### Post by kerry_s on 2006-10-19
You also want to make sure "menu" is installed and do > update-menus or sudo update-menus i can't remember if it points to the right place in you /.config/openbox/debian.xml

---

### Post by moore.bryan on 2006-10-19
*running obconf should put it in the right place... otherwise, you could just cp the file from the openbox dir (where-ever that is... i always forget.)*

---

