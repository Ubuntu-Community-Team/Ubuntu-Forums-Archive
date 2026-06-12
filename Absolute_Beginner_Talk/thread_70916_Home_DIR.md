---
title: "Home DIR"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by bambala2002 on 2005-10-01
Hi,

just curious... the Home dir is like "My Documents" in Windows? Should I make Music, Filmz, Photos & etc inside it and store my files there? I know that I can create the folders anywhere, but where do you normally store such things?
And for example, if I download a programm, like Eclipse (which doesn't work for me btw, and Java also), where should I extract it to? /usr/local/ or /usr/bin ot something else?

And what about the extra partition for Home folder? Should I do it, and how?

---

### Post by TristanMike on 2005-10-01
[QUOTE=bambala2002]Hi,
just curious... the Home dir is like "My Documents" in Windows? Should I make Music, Filmz, Photos & etc inside it and store my files there? I know that I can create the folders anywhere, but where do you normally store such things?
And for example, if I download a programm, like Eclipse (which doesn't work for me btw, and Java also), where should I extract it to? /usr/local/ or /usr/bin ot something else?
And what about the extra partition for Home folder? Should I do it, and how?[/QUOTE]I would say that the "/home" folder is more like the "Documents and Settings" folder rather than "My Documents". But you can make your Music, Filmz, etc. in there. I do that myself.

As far as programs, first check Synaptic to make sure that it isn't available alread. Second, if it isn't available, I believe you want to find a .deb package. Third, if either are no good, then there usually is install instructions.

For eclipse, I found these, see if they are of any help [http://ubuntuforums.org/showthread.php?t=13270](http://ubuntuforums.org/showthread.php?t=13270) and if you use breezy - [https://wiki.ubuntu.com/EclipseIDE](https://wiki.ubuntu.com/EclipseIDE) and for java [https://wiki.ubuntu.com/RestrictedFormats#head-55315677ab8f9890825549fa2ecebdde4bc68087](https://wiki.ubuntu.com/RestrictedFormats#head-55315677ab8f9890825549fa2ecebdde4bc68087)

---

### Post by bambala2002 on 2005-10-01
thanks ;)

about eclipse, and java... they disappeared recently from repositories.

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package eclipse-jdt

apt-get can't find it. but it's ok. I'll wait for Breezy Final. It's supposed to have Eclipse, PHP5 (also doesn't work now) & other things :)

I really don't need much from my computer. All I need is:
1) Listen to MP3's & Radio
2) Watch DivX, XviD (both with mp3 or AC3 audio), DVDs, WMV
3) Surf the web (i need flash, java applets)
4) Be able to program in Java, PHP5, Perl. Also I need MySQL. For that I need Eclipse, and Apache2 server.
5) Use my Wireless LAN in the university (haven't tried it yet)
6) The OS shouldn't be slow

I don't need games, but need some design software like Dreamweaver. I heard NVU for Linux is pretty cool.
One thing left is Adobe Photoshop. GIMP compared to it is a joke :) Or maybe i'm just not used to it yet.

Well, when I can configure all these things to work well - I'll be happy :)

---

### Post by Kyral on 2005-10-01
Java is gone for the repos because of legal reasons that I don't want to get into.

As for putting /home on a separate partition, the answer is a resounding YES. /home is basically your home (duh!) on the system. I meant EVERYTHING will plant your personal configuration for itself there (turn on "show hidden files and folders" or do a ls -a in your homedir and you will see what I mean). Everything also default saves there (assuming you are running as your user and not root, and you should never login as root, use sudo). Having /home on a separate partition has allowed me to make clean reinstalls and keep all my personal settings. Basically, its a GOOD THING.

As for how to do it, when you get to the partitioner for Ubuntu, manually edit the table. Take your "Linux space" (if you are duel booting, otherwise just take the hard drive)  and make a partition for about 10 GBs. Thats everything OTHER than /home, then just make the rest /home (Its even more fun if you have a bigass HD like I do, 250 GB for Home :D). If you ever need to reinstall, when you get to the partitioner manually edit again, but this time select your /home and choose to mount it at /home. The installer and programs will take it from there.

MP3s, Beep Media Player, but you may need to install codecs.

Videos. VLC. Again codecs are needed. I believe there is a Howto in the Hoary Tips & Tricks Forum.

For programming, there is only ONE choice. Emacs. *Raises flameshield*

---

