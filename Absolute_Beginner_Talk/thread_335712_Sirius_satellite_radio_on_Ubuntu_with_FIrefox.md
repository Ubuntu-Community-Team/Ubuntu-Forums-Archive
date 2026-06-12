---
title: "Sirius satellite radio on Ubuntu with FIrefox"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-01-10
I am using linux (Ubuntu 6.10), and tried to play the Sirius satellite radio, which I can do without problems under windows running on the same machine (dual boot).   After I log in, I am told that I need an additional plugin to play the music, but there is no hint on which plugin is needed.  I already installed on the machine RealPlayer (the Linux version).  Can anyone help?
Thanks,

---

### Post by cmo220 on 2007-01-10
I'm having the same problem.  It uses a windows media player plugin.  Don't know how to get that working on anything but windows media player.  Sorry.

---

### Post by Pobega on 2007-01-10
Try [http://eli.criffield.net/sipie/](http://eli.criffield.net/sipie/), it works well for me.

To get it working I'll assume you're downloading into ~/downloads
> sudo aptitude install mplayer python-beautifulsoup
cd ~/downloads
chmod +x sipie
./sipie

It will only ask for your username/password once, which will then be saved for future use. All you will ever need to enter is the caphta password, which can be quite annoying at times.

---

