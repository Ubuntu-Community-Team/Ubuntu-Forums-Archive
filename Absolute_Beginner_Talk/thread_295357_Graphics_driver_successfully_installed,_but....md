---
title: "Graphics driver successfully installed, but..."
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by flotsaminthecosmicsea on 2006-11-07
So I've successfully installed my grtaphics driver, but my graphics still kinda, well, suck. The driver is installed, it has been configured, I believe it should be working. Things work fine in small windows. I can drag boxes around without them ghosting, which is nice. But screensavers still look choppy and so does video at fullscreen. Whats the deal? I have a top of the line graphics card (ATI x800) and an otherwise top of the line setup; why don't I have top of the line graphics.

P.S. I have the latest version graphics driver from ATI (8.30.3)

---

### Post by Ecthelion on 2006-11-08
I dunno if this make sense asking, but are you sure your Ubuntu is using the correct driver?
You could try to reconfigure your xserver once to make sure the correct driver is being used...

```
sudo dpkg-reconfigure xserver-xorg
```

If your driver wasn't correctly installed maybe you could look at [this link]("http://ubuntuforums.org/showthread.php?t=190133&highlight=ATI+x800") for tips

EDIT: make sure to backup your xorg.conf before doing this!

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

