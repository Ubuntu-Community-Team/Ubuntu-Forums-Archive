---
title: "qtorrent"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-05-14
how come qtorrent installed from synaptic packer manager is different from the one in [http://thegraveyard.org/qtorrent.php](http://thegraveyard.org/qtorrent.php)
and i can't get qtorrent from graveyard installed
i got error like this 
oot@zerobinary:/home/zerobinary/Desktop/qtorrent-0.9.5# qtorrent
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
Traceback (most recent call last):
File "/usr/bin/qtorrent", line 15, in <module>
w = TorrentWindow()
File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentmain.py", line 383, in __init__
torrentwindow.TorrentWindow.__init__(self, parent)
File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentwindow.py", line 55, in __init__
self.setSizePolicy(QSizePolicy(3,3,0,0,self.sizePo licy().hasHeightForWidth()))
TypeError: argument 1 of QSizePolicy() has an invalid type
root@zerobinary:/home/zerobinary/Desktop/qtorrent-0.9.5# qtorrent
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
Traceback (most recent call last):
File "/usr/bin/qtorrent", line 15, in <module>
w = TorrentWindow()
File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentmain.py", line 383, in __init__
torrentwindow.TorrentWindow.__init__(self, parent)
File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentwindow.py", line 55, in __init__
self.setSizePolicy(QSizePolicy(3,3,0,0,self.sizePo licy().hasHeightForWidth()))
TypeError: argument 1 of QSizePolicy() has an invalid type

---

### Post by Aberrix on 2007-05-17
why can't you install the version from their website?

---

### Post by zerobinary on 2007-05-17
i don't know help me plz

---

### Post by mikewhatever on 2007-05-17
Different versions of every programs exist, why is it surprising. What is wrong with the version from the repositories?

---

### Post by zerobinary on 2007-05-18
i can't change the port setting that's all

---

### Post by Anaximander Thales on 2007-09-27
> **mikewhatever said:**
> Different versions of every programs exist, why is it surprising. What is wrong with the version from the repositories?

While I normally don't reopen a topic that's not been posted in for 6 months, I'm rather intrigued by this topic.

I d/l'd qtorrent3 from the repositories, and noticed it's lack of features.  Not a big deal, but I was sure there were some settings that I could set command line.  Browsing the web, I found the graveyard site as well.  The qtorrent that you can download from the graveyard site looks NOTHING like the qtorrent you get from the repositories.  Normally I would say, well the program has evolved as the programmer has worked on it - however, Version numbers generally go up.  When you look in the repositories about qtorrent3, you get version 2.9.1-6.  Graveyard's qtorrent is v 0.9.5.

It seems as if these two packages are completely different, but a search on the web would make it seem as if they are the same thing.

---

### Post by malathion on 2008-01-20
What you are looking for is the "qbittorrent" package, not the "qtorrent" package. They are actually completely different apps.

---

