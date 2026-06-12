---
title: "Azureus or Ubuntu Slowwwww"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2008-03-08
It seems that every time I start Azureus my whole OS slow incredibly down. I have this problems since I hard wired my System. Any suggestions? Thanks Joseph

---

### Post by jken146 on 2008-03-08
Use deluge.

```
sudo aptitude install deluge-torrent
```

---

### Post by Joseph5000 on 2008-03-08
Thanks, but why I deluge better then Azureus?

---

### Post by Tobi-fp on 2008-03-08
because it runs better, it doesnt slow down the os

---

### Post by Joseph5000 on 2008-03-08
Sweet, I can see Deluge under Internet, but how do I set it as default?

---

### Post by jken146 on 2008-03-08
It's much lighter (doesn't rely on Java, uses less memory and CPU cycles).  If Azureus is slowing down your machine, try a lighter bittorrent client, like deluge.  If you need more features than deluge has (enabling the plugins gives you quite a few more) then many people use uTorrent in wine (it's a Windows program, but excellent).

Transmission is even lighter than deluge but is more basic.

---

### Post by jken146 on 2008-03-08
> **Joseph5000 said:**
> Sweet, I can see Deluge under Internet, but how do I set it as default?

Do you mean as the default for opening .torrent files?  Right click on a .torrent file, click on "Open with another application" and then choose Deluge in the list (or if it isn't there, type in **deluge**) and tick the box for making it the default.

You can also uninstall azureus.

```
sudo aptitude remove azureus
```

---

### Post by ghost_ryder35 on 2008-03-08
Deluge is a very nice program.  And uses very few resources.  I also found Ktorrent (I think thats what its called) to be a very resource friendly torrent application.

---

### Post by Joseph5000 on 2008-03-08
Alrighty, but still, when I open a torrent it wants to open with azureus, how can I open it with Deluge. I can't find the default settings. Thanks guys

---

### Post by ghost_ryder35 on 2008-03-08
change the settings under Firefox options ( I belive its something like "Choose How Firefox handles certain files").  And choose Open instead of Save

---

### Post by jken146 on 2008-03-08
> **Joseph5000 said:**
> Alrighty, but still, when I open a torrent it wants to open with azureus, how can I open it with Deluge. I can't find the default settings. Thanks guys

I just answered that.

---

### Post by Joseph5000 on 2008-03-08
Yap, I found it, but Deluge isn't there. It must have a different name. Azureus is clearly visible, but Deluge???

---

### Post by ghost_ryder35 on 2008-03-08
> **Joseph5000 said:**
> Yap, I found it, but Deluge isn't there. It must have a different name. Azureus is clearly visible, but Deluge???

Found it under "Firefox"
Can you type in "deluge"

---

### Post by Joseph5000 on 2008-03-08
OK, Deluge is my default, but it still opens with Azureus.

---

### Post by ghost_ryder35 on 2008-03-08
IS it the default under Ubuntu or Firefox or BOTH?

---

### Post by ghost_ryder35 on 2008-03-08
P.S. you can just save the torrent file to the desktop and open it under Deluge to work around the current problem.

---

### Post by Joseph5000 on 2008-03-08
> **ghost_ryder35 said:**
> IS it the default under Ubuntu or Firefox or BOTH?

The default is under firefox

---

### Post by ghost_ryder35 on 2008-03-08
> **Joseph5000 said:**
> The default is under firefox

You should also do it under Ubuntu, like how jken146 said on page 1.

> **jken146 said:**
> Do you mean as the default for opening .torrent files?  Right click on a .torrent file, click on "Open with another application" and then choose Deluge in the list (or if it isn't there, type in **deluge**) and tick the box for making it the default.

You can also uninstall azureus.

```
sudo aptitude remove azureus
```

---

### Post by Joseph5000 on 2008-03-08
OK, the download to over the desktop works, but I would like to set deluge up as default

---

### Post by julian67 on 2008-03-08
go to a downloaded .torrent file, right click>properties>open with> choose deluge

---

### Post by Joseph5000 on 2008-03-08
Sweet, very sweet thanks guys. I deeply appreciate your patience

---

### Post by Joseph5000 on 2008-03-08
Hey Ghost_ryder. I'd like to give my thanks to you, but you got no button there. So still, thanks a lot.

---

