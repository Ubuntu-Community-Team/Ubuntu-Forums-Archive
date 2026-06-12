---
title: "flashplayer/firefox"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by noob_1 on 2008-01-21
when i install flashplayer on/in firefox, nothing happens. when i try terminal by typing sudo command, i get this

eugene@eugene-desktop:~$ 
eugene@eugene-desktop:~$ sudo -get install flashplayerplugin-nonfree 
sudo: please use single character options 
sudo: illegal option `-get' 
usage: sudo -K | -L | -V | -h | -k | -l | -v 
usage: sudo [-HPSb] [-p prompt] [-u username|#uid] 
            { -e file [...] | -i | -s | <command> } 
eugene@eugene-desktop:~$ -k 
bash: -k: command not found 
eugene@eugene-desktop:~$ -l 
bash: -l: command not found 
eugene@eugene-desktop:~$ sudo -get install flashplugin-nonfree 
sudo: please use single character options 
sudo: illegal option `-get' 
usage: sudo -K | -L | -V | -h | -k | -l | -v 
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]

---

### Post by Kilz on 2008-01-21
> **noob_1 said:**
> when i install flashplayer on/in firefox, nothing happens. when i try terminal by typing sudo command, i get this

eugene@eugene-desktop:~$ 
eugene@eugene-desktop:~$ sudo -get install flashplayerplugin-nonfree 
sudo: please use single character options 
sudo: illegal option `-get' 
usage: sudo -K | -L | -V | -h | -k | -l | -v 
usage: sudo [-HPSb] [-p prompt] [-u username|#uid] 
            { -e file [...] | -i | -s | <command> } 
eugene@eugene-desktop:~$ -k 
bash: -k: command not found 
eugene@eugene-desktop:~$ -l 
bash: -l: command not found 
eugene@eugene-desktop:~$ sudo -get install flashplugin-nonfree 
sudo: please use single character options 
sudo: illegal option `-get' 
usage: sudo -K | -L | -V | -h | -k | -l | -v 
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]

try ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by noob_1 on 2008-01-21
tried it and does not appear to work, at least not all the way.(seems  i can't access mycokerewrads.com, which requires flash).

---

### Post by FuturePilot on 2008-01-21
The flashplugin-nonfree is broken currently.
Try this thread
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

---

### Post by stchman on 2008-01-21
Do you have an internet connection?

If not then you need one.  Also make sure to have the multiverse repository enabled.

---

### Post by philinux on 2008-01-21
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)

Download this deb package to your desktop then double click it to install it.

---

### Post by brn on 2008-01-21
Synaptic installs _flashplayer.xp_t and_ libflashplayer.so_ in */usr/lib/flashplugin-nonfree/* with links in */usr/lib/mozilla/plugins/*.  You may need to make copies of (or links to) these in *~/.mozilla/plugins/* for firefox to find them.

---

### Post by MarkX on 2008-01-21
Had the same problem, see this thread with two easy ways to solve it:
[http://ubuntuforums.org/showthread.php?t=670582](http://ubuntuforums.org/showthread.php?t=670582)

---

