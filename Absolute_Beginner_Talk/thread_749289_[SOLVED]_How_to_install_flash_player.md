---
title: "[SOLVED] How to install flash player"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by X_CheshireCat_x on 2008-04-08
how do i install flash so i can watch youtube videos?

---

### Post by philinux on 2008-04-08
In case you get stuck with other multimedia stuff this explains it all.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by thegreenblob on 2008-04-08
You should be able to go to a site with flash, and firefox will ask you if you want to install it.

If it don't try this in the terminal:
> sudo apt-get install flashplugin-nonfree

---

### Post by gandaran on 2008-04-08
> **X_CheshireCat_x said:**
> how do i install flash so i can watch youtube videos?

go to youtube, when you get the plugin missing message just click install, but choose the flashplugin-nonfree or just go to synaptic package manager and install that flashplugin-nonfree.

---

### Post by X_CheshireCat_x on 2008-04-08
i have just installed ubuntu. how do i install flash so i can watch youtube videos?

---

### Post by spiderbatdad on 2008-04-08
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Seisen on 2008-04-08
Or the other option if you don't want everything else is 

```
sudo apt-get install flashplugin-nonfree
``` 

Also make sure that the multiverse repository is enabled otherwise it will say it can't find it.

---

### Post by spiderbatdad on 2008-04-08
> **Seisen said:**
> Or the other option if you don't want everything else is 

```
sudo apt-get install flashplugin-nonfree
```

+1

---

### Post by Tyke91 on 2008-04-08
also, if you had gone to youtube and searched for a video, you would have been given the option to automatically install flash.

---

### Post by X_CheshireCat_x on 2008-04-08
i didnt have mutliverse enabled... thanks

---

### Post by X_CheshireCat_x on 2008-04-08
flash is'nt working anymore... i have ran the code you stated but i cant watch youtube video... :-( this is so much effort for so little reward :-(

---

### Post by por100pre1 on 2008-04-08
Use **Applications**> **Add Remove...** and there select **Macromedia Flash Plugin** and then **Apply Changes**. That should work.

---

