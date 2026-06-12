---
title: "phone modem help"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by arif9k on 2007-07-06
i am using a phonemodem (19200 standard bps modem ) which is connected through com cable.

what should i do to install it in ubuntu 7.04( i also downloaded the software "rconnect-cmdline-1.0")

---

### Post by mikeyphi on 2007-07-06
Is the Modem shown under System - Networks? Are you able to configure it ?

---

### Post by theDaveTheRave on 2007-07-06
mikeyphi

Try looking at this forum page, the guy here is having some problems but the advice is otherwise good (and some of it from me :grin: )

[http://ubuntuforums.org/showthread.php?t=488360]("http://http://ubuntuforums.org/showthread.php?t=488360")

Just to re-iterate what I have said briefly on that forum.

I used to use a dialup modem with Suse and used WVDial - which I happen to think may be included in the Fiesty install, as I noticed it in one of the menus the other day.

The main problem from the guy on the other post is that he couldn't get the modem recognised, but I seem to recall that he said it wasn't recognised under windows either?? - but don't quote me on it.

As I say check it out and I'll make more of an effort to find my old modem hidden somewhere in the Loft to have a quick troubleshoot on it.

good luck.

Dave

---

### Post by pistcivet on 2007-07-06
See here:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

If you have an external serial modem, you will not need to download any software.
I recommend you use wvdial. Enter:
sudo wvdialconf /etc/wvdial.conf
Then edit the file:
gksudo gedit /etc/wvdial.conf
In addition to the obvious changes, I always need to add "Stupid Mode = on"

Dial with: sudo wvdial
Leave the terminal window open while online. Disconnect with Ctrl-c.

---

