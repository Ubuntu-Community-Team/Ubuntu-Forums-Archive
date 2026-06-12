---
title: "Help to remove Enemy Territory"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-12-04
Hi

I installed the game Enemy Territory, and followed this howto: [http://katanoon.nl/Ubu-e/install.php](http://katanoon.nl/Ubu-e/install.php) 

But I didnt get any sound, so then I want to remove it. Can you tell me the terminal command to remove it?
I have tried sudo apt-get remove et but it is still there.

Thanks

---

### Post by CatKiller on 2006-12-04
As I understand it, not having used Enemy Territory, you need to delete 

~/.etwolf
/usr/local/games/enemy-territory
/usr/local/bin/et
/usr/local/bin/etded
and possibly .desktop entries in /usr/share/gnome/apps/Games/

Most games come with an uninstallation script, but I guess id forgot on this one.

---

