---
title: "Ubuntu Server"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by porkcows on 2007-04-17
I am new to Linux and I just installed ubuntu server 6.10.  I asked a friend how to install a GUI for it and he said  "type sudo aptitude ubuntu-desktop"  so I did and it installed a buch of stuff.  so now I restarted the computer and it brought me back to the command line.  my question is how do I open the GUI once it is installed?. also how can I make it do that automatically like Ubuntu desktop?

Thanks 
-Porkcows

---

### Post by dfreer on 2007-04-17
startx will start the GUI from the commandline.

Ummm try this [http://ubuntuforums.org/showpost.php?p=2322198&postcount=2](http://ubuntuforums.org/showpost.php?p=2322198&postcount=2)
Make sure to CHECK gdm, not uncheck it as the post states. These instructions were given to disable x server, not enable x.

---

### Post by dfreer on 2007-04-17
also ```
sudo /etc/init.d/gdm start
``` or ```
sudo /etc/init.d/gdm restart
```

depending on whether gdm is already running or not...

---

