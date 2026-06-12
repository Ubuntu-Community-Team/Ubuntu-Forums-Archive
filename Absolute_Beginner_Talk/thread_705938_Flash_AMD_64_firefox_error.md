---
title: "Flash AMD 64 firefox: error?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by fetisha on 2008-02-23
Uh, this is prorably an easy fix, but I'm just an absolute bigginer here, so when I followed the instructions on this page here: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)
I get a message in the third step when trying to move the files into firefox saying, "/usr/local/firefox32/plugins/' is not a directory: No such file or directory"
Don't know what to do.

---

### Post by taurus on 2008-02-23
Have you installed firefox 32bit version or do you have /usr/local/firefox32?

```
ls -la /usr/local/firefox32
```
If you don't have it, create one.

```
sudo mkdir /usr/local/firefox32
sudo mkdir /usr/local/firefox32/plugins
```

---

### Post by fetisha on 2008-02-24
ok, so it told me there was none, then I did what you tole me and it says this:
total 12
drwxr-xr-x  3 root root 4096 2008-02-24 01:30 .
drwxr-xr-x 11 root root 4096 2008-02-24 01:27 ..
drwxr-xr-x  2 root root 4096 2008-02-24 01:30 plugins

and so i tried to finnish the installation in the last step of the guide (sudo mv install_flash_player_9_linux/libflashplayer.so /usr/local/firefox32/plugins/) and it says "mv: cannot stat `install_flash_player_9_linux/libflashplayer.so': No such file or directory"

---

### Post by oedha on 2008-02-24
when i worked on acer4520...it also happen.....i can't install that
i suggest you to open terminal 
and install :==> sudo apt-get install flashplugins-nonfree

---

### Post by fetisha on 2008-02-24
> **oedha said:**
> when i worked on acer4520...it also happen.....i can't install that
i suggest you to open terminal 
and install :==> sudo apt-get install flashplugins-nonfree

I tried and it says:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugins-nonfree

---

### Post by doorknob60 on 2008-02-24
Try this, it integrates it into 64 biit firefox and it works well so far for me :) [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by oedha on 2008-02-24
misstype.....suppose to be sudo apt-get install flashplugin-nonfree
sorry :)

---

### Post by fetisha on 2008-02-24
> **oedha said:**
> misstype.....suppose to be sudo apt-get install flashplugin-nonfree
sorry :)
ok, it did a lot of stuff and ends with:
01:55:09 (755.27 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by fetisha on 2008-02-24
> **doorknob60 said:**
> Try this, it integrates it into 64 biit firefox and it works well so far for me :) [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
I tried that, and, it did something at least, because at least now on flas sites like marilynmanson.com and courtneylove.com it tells me i need to upgrade my version of flash, instead of nothing showing up at all. But now how do I get the latest version?

---

### Post by fetisha on 2008-02-24
Alright, these are the way's I have tried so far to get flash:

This way: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

And this way: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

And by trying to install the plug-in when firefox tells me to.

And by using gnash (which kind of worked on youtube, but the menu at the bottom of the video was all jumbled up, and it didn't work on other flash sites like marilynmanson.com courtneylove.com or davidbowie.com).

 have Xubuntu 7.10 32 bit
Shuttle SN68SG2
AMD Athlon 64 X2 5200
160 Serial ATA
1gig memory

I read somewhere that you can't install flash on a computer using an AMD 64 processor, so I tried everything and still nothing. It's getting really frustrating. Please help!

PS: Someone told me I have a 64 bit computer (I guess it makes sense, AMD 64 and all) but I didn't install Ubuntu for a 64 bit computer, I installed Xubuntu 7.10 and it didn't say what it was for... could this probably be the problem?

Thank you,
Newbi in distress!

---

