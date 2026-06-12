---
title: "[SOLVED] Totem"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Terry N on 2008-01-13
Hello again,

I am now having no luck getting Totem to read a DVD. I have installed the gstreamer plugins and when a open about with the movie in this shows up( Movie Player using GStreamer 0.10.14 and GNOME). After a reboot and restarting Totem without the movie in in about I get a list of about 6 gsreamer plugins installed. Can anyone help me on this?

Thanks again,  Terry

---

### Post by edm1 on 2008-01-13
you will need libdvdread3 and libdvdcss2 installed.

For libdvdread3

```
sudo apt-get install libdvdread3
```

libdvdcss2 isnt included in the repositories for legal reasons but can be got [here]("http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb") (i can only find the 32-bit version so if you're 64-bit you may have to do some searching yourself).

Even after this i still can't play DVDs in totem but VLC works fine.

To install VLC

```
sudo apt-get install vlc
```

---

### Post by ajgreeny on 2008-01-13
For some reason Ubuntu still gives us **totem-gstreamer**, which can't play DVDs very well.  Try **vlc,** by all means, but I suggest you also try **mplayer**, which is one of my favourites, or **totem-xine**.  I personally prefer **totem,** if it will play the files I have but some wmv version 9 files will not play in **totem** at all, so I use **mplayer.**

Installing** totem-xine** will remove **totem-gstreamer**, but don't worry, all will be well.

---

### Post by Malta paul on 2008-01-13
HI, Totem-xine may work for you if you want Totem, but as edm1 said +1 for VLC
Have fun:)

Sorry ajgreeny you beat me!!

---

### Post by Terry N on 2008-01-13
Installed libdvdcss2. Thanks alot how do I close this Thread?

Thanks again.

---

### Post by eapache on 2008-01-13
There should be a "thread tools" menu at the top where you can mark the thread as Solved.

---

