---
title: "install flashplayer"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-08-17
so.....
[I]
i have the [/I]**install_flash_player_9_linux.player.tar.gz** living on my desktop (7.04)

how would i install this w/o accessing the internet

-PS
why can i not:
[LIST=1]
[*]cd /desktop
[*]create a directory (all permisions enabled in the GUI)
[*]be root in the GUI
[/LIST]

btw     ima nub

---

### Post by robgill on 2007-08-17
> **phoenix24x said:**
> so.....
[I]
i have the [/I]**install_flash_player_9_linux.player.tar.gz** living on my desktop (7.04)

how would i install this w/o accessing the internet

-PS
why can i not:
[LIST=1]
[*]cd /desktop
[*]create a directory (all permisions enabled in the GUI)
[*]be root in the GUI
[/LIST]

btw     ima nub

1) Try cd Desktop  (it's case sensitive)
2) ??? you need to be root to create directories outside of your home folder
3) gksu nautilus (in terminal)

---

### Post by Outrunner on 2007-08-17
since it's on your Desktop:(yes, that is a CAPITAL D)

```
cd ~/Desktop
```

Extract the file

```
tar xzvf *.tar.gz
```
```

cd <newly_created_dir>
```

I think this is the correct name, if not, it's not too hard to find...

```
./flashplayer_installer.sh


```

---

### Post by Arthur Archnix on 2007-08-17
You running Feisty? It couldn't be easier. Ignore your desktop, go to a website that uses flash, and when firefox prompts you choose to install it automatically. Nice!

---

### Post by Banjooie on 2007-08-17
Firefox's 'automatically install flash' never works, though. Then again, downloading it from the site itself is usually hit or miss. Every time I've tried, it's like 9/10 it'll download really slowly and then stop midway through. (This never happens with the Windows version. How odd.)

---

### Post by aysiu on 2007-08-17
This website will help you:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by phoenix24x on 2007-09-17
first off....THANK YOU!!!!

i am not yet successful but i follow what your saying and im getting more comfortable with linux/ubuntu. i followed your directions and when i:

**./flashplayer-installer**

i get a:

**Your architecture, \'86_64\', is not supported by the Adobe Flash Player Installer.**

which leads me to believe i nned a 32bit flash.

thanks again

BMg

---

### Post by afonic on 2007-09-17
Use the instructions here to download Flash for AMD64:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by jds06 on 2007-09-20
Okay. Everytime I install the flashplayer, I'll go to any number of websites and as soon as I click on a button, the browser closes. I am working off the 5.10, but am trying to change that now.

How do I keep my browser from closing?

---

