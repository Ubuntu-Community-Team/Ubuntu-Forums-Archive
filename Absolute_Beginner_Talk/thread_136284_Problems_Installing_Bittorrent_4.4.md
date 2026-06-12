---
title: "Problems Installing Bittorrent 4.4"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-25
I downloaded bittorrent 4.4 and did the following:

> user@machine:~/Desktop$ sudo dpkg -i bittorrent.deb
(Reading database ... 116087 files and directories currently installed.)
Unpacking bittorrent-4.4.0.linux (from bittorrent.deb) ...
dpkg: error processing bittorrent.deb (--install):
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Choker.py', which is also in package bittorrent
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bittorrent.deb


What can I do to correct this?

-thx

---

### Post by robust on 2006-02-25
You need to uninstall the bittorrent client that your currently using, otherwise you can't install the new one. Just find bittorrent in Synaptic and remove it.

---

### Post by stalefries on 2006-02-25
It seems it doesn't want to overwrite a file that is owned by another program. 
It is possible to force it, I just can't remember how at the moment. Try googling for it.

---

### Post by Cousindaddy on 2006-02-25
> You need to uninstall the bittorrent client that your currently using, otherwise you can't install the new one. Just find bittorrent in Synaptic and remove it.

I did as you said and it worked splendedly.

Thank-you both for taking time to respond.

---

