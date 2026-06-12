---
title: "HowTo: Getting DVD to work on Ubuntu 7.10 Gutsy Gibbon"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by coffen on 2007-12-28
Since there are so many post on this forum dealing with problems playing encrypted DVDs and other media files I thought I'd summarize what i learned from these posts into one simple straight-forward HOWTO:

First you need to install vlc or xine from synaptic.

VLC will play most media files without the need to install extra codecs.

If you like totem then install totem-xine. This will uninstall totem-gstreamer which is no good anyway IMHO.

You can also install xine-ui and/or gxine.

Now you need to install the necessary codecs and libraries.
To do that simply type the following commands in a terminal window.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get update

sudo apt-get install w32codecs libdvdcss2
```

The w32codecs package will install most of the codecs needed for Ubuntu.
libdvdcss2 installs the Medibuntu CSS decrypter needed to play commercial encrypted DVDs

That did it for me. I hope it works for others too.

---

### Post by CypherHackz on 2007-12-28
yup. i using vlc too. it is much better than the rest. but when came to display the subtitle, the text go the right. only half of the subtitle is can be displayed. the half side is out from the monitor screen. do you know how to fix it?

-cypher.

---

### Post by Sbarton on 2007-12-28
coffen, the 'How to' works fine on mymachine, thanks.
regards

---

### Post by yknivag on 2007-12-29
Many thanks coffen. I can now watch dvds. :)

---

### Post by njwiley on 2008-01-03
Thanks for the post Coffen.  My commercial DVD playback breaks when I allow update manager to upgrade libdvdcss2 from 1.2.5 to 1.2.9.  Is anybody else running into this?

---

### Post by ~LoKe on 2008-01-03
I prefer mplayer over VLC and Totem/Xine, personally.  Yep, this guide works just fine. :)  Shouldn't this be in the tips forum?

---

