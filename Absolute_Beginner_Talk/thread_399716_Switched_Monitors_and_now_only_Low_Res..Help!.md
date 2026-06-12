---
title: "Switched Monitors and now only Low Res..Help!"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-04-02
I just switched to a different monitor and now I can only get a 640x480 resolution.  How can I change this?  It does not give me an option in the preferences. I know for a fact that it is capable of higher res. :confused: 

Thanks,
Mike

---

### Post by Jose Catre-Vandis on 2007-04-02
You will need to reconfigure your xorg.conf file. You can do it by hand if you know your monitor specs and you know what you are doing (!) or use this command in a terminal to use a wizard:

```
sudo dpkg-reconfigure xserver-xorg
```

It asks lots of questions, most of which you can answer the default to, but try it with the automatic identification of your monitor.

Back up your existing xorg.conf first, then you can always go back to it, if needs be:
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by twolf427 on 2007-04-02
I am having the same problem, I just installed Ubuntu, and after using Jose's advice, I still can only use 800x600 when my monitor is capable of 1024x768. Any ideas? Thanks.

---

### Post by Dual Cortex on 2007-04-02
**mramsey** and **twolf427**, can you please post the output of
> cat /etc/X11/xorg.conf

---

### Post by mramsey on 2007-04-03
sorry would have replied sooner but I forgot to subscribe to my thread.  I did try to reconfigure the xserver but had no luck.  Fortunately since this was a brand new install I just installed Ubuntu again.   I don't know what the issue was it was the same monitor one was black and one was white:lolflag:  all is working fine now.

---

