---
title: "strange removal problem"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2008-04-05
There is a program called kio-umountwrapper that apparently is partially installed. Doesn't show up as broken, won't remove thru terminal or synaptic. I get the followign error in terminal.

It doesn't seem to stop updates, but it is weird.

(Reading database ... 154556 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ChameleonDave on 2008-04-22
I have exactly the same thing.  Can someone please help?

---

### Post by ChameleonDave on 2008-04-25
I posted this in another thread too ([http://ubuntuforums.org/showthread.php?t=762780](http://ubuntuforums.org/showthread.php?t=762780)), and got the answer, but that thread is now locked.

For me, the problem was solved thus:

```
cd /var/lib/dpkg/
sudo mkdir info.backup
sudo mv info/kio-umountwrapper* info.backup/
sudo apt-get purge kio-umountwrapper
```

All traces of the troublesome kio-umountwrapper package are now gone from my system.

If you are feeling daring, the following code will do the same thing:

```

sudo rm /var/lib/dpkg/info/kio-umount*
sudo apt-get purge kio-umountwrapper
```

---

### Post by bartcramer on 2008-04-25
Congrats! Maybe mark the thread as solved?

---

### Post by csabimeta on 2008-04-25
Thanks! It solved my problem too.

---

