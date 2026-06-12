---
title: "[SOLVED] short cut icon"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-20
ok, i know how to make an icon with a launcher, but what i need, is a launcher that will pull up a program that needs to be sudo and give my password to make a package work properly. is there a way to do this?

normally i would have to go into the terminal and do this
k33bz@treehouse:~$ sudo ufoai
Password:
Adding game dir: ./base
Added packfile ./base/0base.pk3 (5 files)
Added packfile ./base/0maps.pk3 (388 files)
Added packfile ./base/0media.pk3 (5 files)
Added packfile ./base/0models.pk3 (874 files)
Added packfile ./base/0pics.pk3 (1730 files)
Added packfile ./base/0snd.pk3 (121 files)
Added packfile ./base/0ufos.pk3 (63 files)
using /home/k33bz/.ufoai/2.1.1/base for writing
Adding game dir: /home/k33bz/.ufoai/2.1.1/base
execing default.cfg
execing config.cfg
execing keys.cfg
Hostname: treehouse
IP: 127.0.1.1
...using language: en_US.UTF-8
Console initialized.

---

### Post by starcraft.man on 2007-05-20
You should be able to go to the launcher menu, then in the drop down select " Application in terminal" and type in the sudo command, in your case:

```
sudo ufoai
```

Then just set it on your desktop, you'll have to put your password yourself.

If you don't want to even do the pass, I assume that requires you to write a script. I haven't gotten to scripting yet... search the forums though, I'm sure there are guides to basic scripting.

---

### Post by k33bz on 2007-05-20
ok thanks, i will go look for some basic scripting. :)

---

