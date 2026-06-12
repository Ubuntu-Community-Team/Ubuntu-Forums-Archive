---
title: "mozilla mplayer plugin"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by boglio on 2007-08-28
I've installed mozilla-mplayer plugin, i dont know if it works or not or if i need to do something to watch divx videos. I'm trying to watch videos from [http://stage6.divx.com](http://stage6.divx.com) but i always get an error message saying "For linux support try mplayer" 

All help appreciated - I'm a newbie. And sorry for my spelling since english is not my native language. Thanks:)

---

### Post by mcduck on 2007-08-28
> **boglio said:**
> I've installed mozilla-mplayer plugin, i dont know if it works or not or if i need to do something to watch divx videos. I'm trying to watch videos from [http://stage6.divx.com](http://stage6.divx.com) but i always get an error message saying "For linux support try mplayer" 

All help appreciated - I'm a newbie. And sorry for my spelling since english is not my native language. Thanks:)

First, uninstall totem-plugin. It seems to load instead of mplayer-plugin, and you won't need it any more anyway.

Then open a terminal and run ```
ls /usr/lib/firefox/plugins/
```See if you can find "mplayerplug-in-dvx.so" and "mplayerplug-in-dvx.xpt" in there. If you did, mplayer-plugins should be now able to play divx videos. If you didn't see those files run following commands:
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```
This will create links from where the files are to where mplayer-plugin tries to find them. After that divx should work without any problems.

---

### Post by boglio on 2007-08-28
Thanks that did the trick. :)

---

### Post by Deedlit on 2007-08-28
Hi.  I'm having the same problem with mplayer.  When I use add/remove to look for totem, nothing comes up. But when I put in the code you wrote most of the plug ins are totem and none are the one you said to look for. Help?!???!!?

---

### Post by Perfect Storm on 2007-08-28
You need to use Synaptic Package manager for that task. (under System tab Panel). Or by command line:

```
sudo aptitude remove totem-mozilla
```

---

### Post by Deedlit on 2007-08-28
Thank you, that worked.  I got one thing I was trying to use to work, but not the other.  I really appreciate the help.

---

### Post by deadgobby on 2007-08-28
> **mcduck said:**
> First, uninstall totem-plugin. It seems to load instead of mplayer-plugin, and you won't need it any more anyway.

Then open a terminal and run ```
ls /usr/lib/firefox/plugins/
```See if you can find "mplayerplug-in-dvx.so" and "mplayerplug-in-dvx.xpt" in there. If you did, mplayer-plugins should be now able to play divx videos. If you didn't see those files run following commands:
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```
This will create links from where the files are to where mplayer-plugin tries to find them. After that divx should work without any problems.

I was wounder how to get it to work, ,but really never looked into it. MUCH THANKS

Gobby

---

### Post by philinux on 2007-08-28
Copying the files mentioned ,mplayerplug-in-dvx.so etc, got me watching divx too.

Why weren't the files or links set up in the first place?

---

### Post by FarmerReg on 2007-08-31
Thanks a lot guys, this really helped me out tremendously.

---

