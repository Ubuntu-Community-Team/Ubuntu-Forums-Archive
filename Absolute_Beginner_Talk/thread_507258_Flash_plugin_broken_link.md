---
title: "Flash plugin broken link?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-07-22
I followed the instructions as posted in the above sticky for multimedia supoprt...

But my flash pluigns are broken - i have even attempted to remove and reinstall but they reamain broken? anybody know how to fix? or why it does this?

---

### Post by hangthedj on 2007-07-22
go to a konsole, and to the directory and do 'ls -l' for a long directory listing, 

```
root@elliott:/usr/lib/firefox/plugins# ls -lh
total 12K
lrwxrwxrwx 1 root root   39 2007-07-06 13:10 kaffeineplugin.so -> ../../mozilla/plugins/kaffeineplugin.so
lrwxrwxrwx 1 root root   34 2007-07-10 13:29 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root   54 2007-07-06 10:06 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx 1 root root   39 2007-07-06 10:06 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root   41 2007-07-10 14:42 libmozilla_bonobo.so -> ../../mozilla-bonobo/libmozilla_bonobo.so
-rw-r--r-- 1 root root 8.8K 2007-07-18 05:50 libunixprintplugin.so
lrwxrwxrwx 1 root root   37 2007-07-06 15:15 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root   42 2007-07-06 10:50 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root   43 2007-07-06 10:50 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root   42 2007-07-06 10:50 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root   43 2007-07-06 10:50 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root   39 2007-07-06 10:50 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root   43 2007-07-06 10:50 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root   44 2007-07-06 10:50 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root   40 2007-07-06 10:50 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
```


and it should tell you where its trying to link to it.  then find out where the real file is and either copy it to the directory or re link the file to  the correct one using 
```
ln -s /path/to/libflashplayer.so ./libflashplayer.so
```  
you can find the real file by doing 
```
locate libflash*.so' or just locate libflash*
```

---

### Post by cjnkns on 2007-07-22
Hey thanks for the reply...
ok, I am really lost here atm -  I tried to uninstall / reinstall flash and ubuntu restricted.. worked fine so it says.

But - when I go to the /usr/lib/flashplugin-nonfree there is nothing in the directory i was expecting to find the libflash*.so file but.. it's not there ..

Then when I do the locate libflash*.so it does not return and results? what am i missing here?

---

### Post by cjnkns on 2007-07-22
Ok, so I did an updatedb and now I can at least locate the libflash*

But, the links point to an empty directory? 

/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


Both of the above point to /usr/lib/flashplugin-nonfree
which is empty not sure why ...

---

### Post by hangthedj on 2007-07-22
i would recommend going to the flash website and downloading the bin installer.

add executable properties to it, and then run it in a terminal.  and tell it what directory you want it installed.

firefox searches a couple of directories for the plugins

firefox-dir/plugins and ~/.mozilla/plugins

for things like flash i usually don't use apt, cause you know you always have the most up to date version. adobe upgrades little things on all their programs constantly.

---

### Post by cjnkns on 2007-07-25
Ok, I'll give that a shot thanks for the help.

---

### Post by cjnkns on 2007-07-25
>add executable properties to it, and then run it in a terminal. and tell it what directory you want it installed.

How do I specify which directory I want it installed in? .. if I execute ./flash doesn't install where ever the script says too?

---

