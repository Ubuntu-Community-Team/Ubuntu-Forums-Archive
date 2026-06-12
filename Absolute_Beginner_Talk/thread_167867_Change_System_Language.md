---
title: "Change System Language"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Boemer on 2006-04-29
Hi everyone,

I wanted to know if it easily possible to change the system language. I'm not use GNOME or any other GUI, it is a root-server, but the internet-provider, put a german Ubuntu 5.04 on it. And half of the text is in german the other half in english. We would love to just remove the german and add the complete english help and programs.

Is this easily possible, should i change some variables? Or can I apt-get some libraries... ?

---

### Post by GilGalad on 2006-04-29
Install the language-pack-en, language-pack-en-base, manpages and uninstall their respective german (-de) packages. Also as root:

 sudo dpkg-reconfigure locales

Check that /etc/environment has the right values, ie.

LANGUAGE="en_GB:en_US:en_GB:en"

LANG=en_GB.UTF-8
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"

---

### Post by user1397 on 2006-04-29
You can just go to System-->Administration-->Language Selector

---

### Post by Boemer on 2006-04-29
Thanks that did it, I just had to deinstall de manpages-de

and set the environment to en_US instead of de_DE

strange the language-pack-de wasn't installed, is it maybe only for some gui?


[QUOTE=GilGalad]Install the language-pack-en, language-pack-en-base, manpages and uninstall their respective german (-de) packages. Also as root:

 sudo dpkg-reconfigure locales

Check that /etc/environment has the right values, ie.

LANGUAGE="en_GB:en_US:en_GB:en"
LANG=en_GB.UTF-8
[/QUOTE]

---

