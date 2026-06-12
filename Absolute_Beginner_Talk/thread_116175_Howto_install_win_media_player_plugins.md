---
title: "Howto install win media player plugins"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-01-12
Hi all,

Was wanting to know how to install windows media player plugins for ubuntu.  I see what others have written regarding the installing on w32codecs, but i get a big warning about it not being authenticated and that it is unsafe  etc etc.

What is the correct thing I should be installing and how safe is it.

---

### Post by kaamos on 2006-01-12
In my opinion this is a good way to do it: [https://wiki.ubuntu.com/RestrictedFormats#head-7a73b076c82c7d7bb567bdac3322e53274f1d1f3](https://wiki.ubuntu.com/RestrictedFormats#head-7a73b076c82c7d7bb567bdac3322e53274f1d1f3)

---

### Post by Sef on 2006-01-12
Here's how to install them:

> The Codecs

mplayer, xine and totem-xine can play MPEG-1, -2 & -4, DivX, Quicktime, Real Media 8 & 9, Windows Media Video 9, and many other formats with the proper support. This support has been bundled into the w32codecs. 

If your country's laws allow you to play media using the w32codecs, use your web browser to download the file w32codecs_20050412-0.0_i386.deb from  here or  here to your Desktop, and, in a terminal, type: 

cd ~/Desktop
sudo dpkg -i w32codecs_20050412-0.0_i386.deb

Note: wmv files encoded with DRM (Digital Rights Management) are not playable by the codecs.

For more info on installing media support, go to click on the following:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by The Pinny Parlour on 2006-01-12
Ok guys cheers and thanks.  Am doing now via Synaptic Package Manager.

---

### Post by TikkiRo on 2006-01-12
[COLOR="Purple"]Can I maybe just jump in to this thread since its semi related.  I already have all the software and codecs installed (I think) but can't get any of the music on the MSN radio site to play - [http://radio.msn.com/default.aspx]("http://radio.msn.com/default.aspx")

Anyone like to perhaps venture possible problems and/or solutions to this as I'm really keen to hook into that service through Linux rather than having to revert to Windows once again?  If it can't be done, that's fine - just so long as I know.  Tks  TKR[/COLOR]

---

