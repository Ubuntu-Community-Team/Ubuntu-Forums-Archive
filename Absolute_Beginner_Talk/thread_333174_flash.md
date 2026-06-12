---
title: "flash?????"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-01-07
ok, i have been having this problem for weeks, i have the extracted files for upgrading my flashplayer so that i can watch stuff on myspace and other flash based things, and i keep following the instructions, and yet it still wont work, also youtube videos have no sound whatsoever, and yet rhythmbox can work all day......so i know its not my sound card-

---

### Post by aysiu on 2007-01-07
Follow these instructions instead:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Sniper99 on 2007-01-07
ok, the first two commands worked, but after that it all went downhill....this is wut my terminal reads 


spencer@spencer-desktop:~$ sudo apt-get remove flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
spencer@spencer-desktop:~$ rm ~/.mozilla/plugins/*flash*
spencer@spencer-desktop:~$ wget -c [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.g](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.g)
--00:03:30--  [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.g](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.g)
           => `FP9_plugin_beta_112006.tar.g'
Resolving download.macromedia.com... 72.246.171.191
Connecting to download.macromedia.com|72.246.171.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:03:31 ERROR 404: Not Found.

spencer@spencer-desktop:~$ tar -xvzf FP9_plugin_beta_112006.tar.gz
tar: FP9_plugin_beta_112006.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous err


sorry its a pain to read

---

### Post by aysiu on 2007-01-07
It looks as if you're missing a *z* on that third command there. 

It should be ```
wget -c http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.g**z**
``` instead of ```
wget -c http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.g
```

---

### Post by Sniper99 on 2007-01-07
wow i feel like i just lost 28 ig points, thank you so much

---

### Post by aysiu on 2007-01-07
> **Sniper99 said:**
> wow i feel like i just lost 28 ig points, thank you so much
It's okay. It's a lot to highlight before you copy and paste. No worries. We all make mistakes.

---

### Post by Sniper99 on 2007-01-07
ok, i got flash, and that was actually really easy, now how about java, it sounds similar i was wondering if you know any instruction sites that can show me that

---

### Post by aysiu on 2007-01-07
> **Sniper99 said:**
> ok, i got flash, and that was actually really easy, now how about java, it sounds similar i was wondering if you know any instruction sites that can show me that
To be honest, Java kind of confuses me (so many different versions), and I don't really use it.

This site should help you out, though:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by ragadanga63 on 2007-01-07
Installing Java made my head spin too, being an Ubuntu semi-newbie.  That was until i installed automatix2.  which as its name suggests automates the installation.  You can get automatix from:

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Good luck.

---

