---
title: "Linking to scripts"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by joewhite on 2006-04-06
When I make a link to scripts like Python they stop executing when I move them out of the same directory. This seems to defeat the purpose. Please help.

---

### Post by htinn on 2006-04-06
Python scripts really should be installed in the super user area like every other app (like /usr/bin or /usr/local/bin). That way you can not only use them without having to link to them, any user of that computer can also use them.

If you have to run a script in the user area, then you will likely need to modify the PATH variable (and that's probably more trouble than you really want).

---

### Post by joewhite on 2006-04-06
Well I tried both linking and copying the python file into the /usr/bin directory but it still wouldn't execute. It is for the Anatomic bittorrent client and it has a lot of other files. I don't want to drag them all over into the bin directory though because it would look messy.

---

### Post by htinn on 2006-04-06
With something as simplistic as anatomic, you'll probably need to be running from a terminal anyway. If you want a nice trackerless torrent client, there's always Azureus or the latest official BitTorrent client.

---

### Post by joewhite on 2006-04-06
Will the bittorrent client in Synaptic do?

---

### Post by htinn on 2006-04-06
No, you really need to get the newest one from their web page for DHT (the repos still use the old version). Fortunately, they have a deb file on that site.

[http://www.bittorrent.com/](http://www.bittorrent.com/)

You can just use "sudo dpkg -i filename.deb" to install that. You may run into the fact that ubuntu-desktop depends on the old version, so to get past that you would use "sudo dpkg -i --force-overwrite filename.deb" to install. You'll also need to type "bittorrent" into a terminal rather than use the Applications menu to start it.

---

