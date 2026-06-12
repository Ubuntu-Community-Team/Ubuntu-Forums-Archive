---
title: "Flash 9"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by xunshirine on 2006-12-06
Hello. I am using FF and Opera with flash player 7 and want to switch to 9 version. In [ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox") this is the way 

> wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)
tar xvzf FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 



But I got the absent file or directory message on terminal. Indeed there is not /usr/lib/flashplugin-nonfree/ directory. How can I install flash 9 for opera and FF? And especially do you advice the switch ? Thanks

---

### Post by jordanmthomas on 2006-12-06
instead of
```
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
```
try this:
```
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/firefox/plugins
```

and, yes, I advise you switch.  Flash 9 is head and shoulders above flash 7

---

### Post by xunshirine on 2006-12-06
> **jordanmthomas said:**
> 
```
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/firefox/plugins
```

and, yes, I advise you switch.  Flash 9 is head and shoulders above flash 7
Thanks but is this also valid for Opera?

---

### Post by jordanmthomas on 2006-12-06
Opera looks there for plugins.  That is how I installed it and it worked fine.
If it doesn't pick it up there, do this:
in opera,
Tools --> Preferences --> advanced --> Content --> Plug-in options
On the line plugin path, mine reads as follows:
/usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/usr/lib/firefox/plugins

Then, you can scan for new plugins and it should be picked up


**oh, and on further inspection, my flash player is in /usr/mozilla/plugins

---

### Post by xunshirine on 2006-12-06
Thanks a lot @jordanmthomas. I placed the flash 9 .so file into home directory / .mozilla and .opera folders respectively. Now it works fine. Just ask to know , why ubuntu guide method mentioned above is false still. Why did not they change it ?

---

### Post by jordanmthomas on 2006-12-06
I am not sure why it is wrong.  Perhaps it works for some people.  To be honest, I figured their way would work, I just usually do things my own way, so I have different ways than a lot of people.

---

### Post by gila_monster on 2006-12-06
> **xunshirine said:**
> Thanks but is this also valid for Opera?

It *mostly* works. There are issues with Opera, and Adobe is working with Opera on the problems. You may experience some freezes or other odd behavior with some sites.

Adobe also says that Flash 9 beta is supported on FF 1.5, but doesn't mention 2.0. I have it loaded for both Opera and FF2, and FF2 doesn't crash as often, but as with Opera, it freezes on some sites.

It is, after all, a beta, so I shouldn't complain. I probably will anyway, though. ;)

---

