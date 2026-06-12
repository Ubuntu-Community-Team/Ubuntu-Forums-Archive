---
title: "/etc/fonts/local.conf Question"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Ishkhara on 2007-04-15
I was installing the ms true type fonts today and came across an error. The apt-get thing worked, and I was trying to enable the fonts.

I was following instructions (lost them, so no reference), and hit a point where I was to edit something in the /etc/fonts/local.conf file. Well, there was no such file in that location, but there was a fonts.conf. I looked at that file and it said to make changes to the local.conf. Well, not having that file, I did a "let's try this" and created a copy of fonts and renamed it local, just for a stating point.

Well, that was a bad idea.

The system instantly went wacky. No windows would open. I rebooted, and it got worse. Took forever to boot and login, and once the desktop was up, all I had was my wallpaper. No icons or task bars or anything. I booted into recovery mode and deleted the file, and that cleared everything up.

Question is, what the heck happened? I'm assuming that local.conf has a different format than fonts.conf, and that the system picks up changes to the local.cong file. Can anyone shed some light on why the reaction was so bad?

---

### Post by lamalex on 2007-04-15
could you try finding that guide? if I saw what you were following I might be able to help.

---

### Post by Ishkhara on 2007-04-16
Found it

[http://www.ubuntux.org/how-to-install-the-free-microsoft-truetype-fonts](http://www.ubuntux.org/how-to-install-the-free-microsoft-truetype-fonts)

they key instructions

[I]sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
sudo cp /etc/fonts/local.conf /etc/fonts/local.conf_backup
sudo gedit /etc/fonts/local.conf

Search for "Uncomment below to enable the freetype autohinter module".
Remove the comments as described and you're finished.[/I]

I'm just not sure where local.conf comes from. The instructions are from 2005, and... I'm using straight Ubuntu where these are for Ubuntux (which I just noticed). so it may be a version thing.

---

### Post by yabbadabbadont on 2007-04-16
If you are using Edgy or later run:
```
sudo dpkg-reconfigure fontconfig-config
```
and answer the questions.

---

