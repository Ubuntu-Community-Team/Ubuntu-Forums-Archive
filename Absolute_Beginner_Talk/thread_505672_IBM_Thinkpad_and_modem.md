---
title: "IBM Thinkpad and modem"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by glx5667 on 2007-07-20
I installed Ubuntu 6.06 on a used IBM thinkpad.  I have Win XP on a second partition.  I hooked up an external USR 56k dial up modem (known to work with Ubuntu) to the serial port, but Ubuntu will not recognize it.  This set up works when using Windows, so the port and modem work.  Linux does not seem to recognize the serial port (it is listed in the device manager as  tty s0).  Any help is apppreciated, thanks.

---

### Post by Bartender on 2007-07-21
glx -
You didn't say how you configured the modem.  Did you go into Network and try to set it up there?  The Network utility for dial-up is broken in Edgy & Feisty.
You should be fine with a true hardware external.  Take a read thru [this]("http://ubuntuforums.org/showthread.php?t=480717") and see if it doesn't get you going.
Whoops - you say you're using 6.06?  The Network GUI should work. Well, try using wvdial or ppp-config anyway.  You're sure the modem works properly?

---

### Post by glx5667 on 2007-07-23
thanks for the reply.  I live in the counry and only have dial up connection.  The modem I'm trying to use on the Thinkpad is the one I use on my main computer, so it works (using it now).  Plus, because I have Win XP also on the Thinkpad (dual boot), I can access the internet in Win XP using the USR external modem, and it works fine.  So the problem is probably not the modem, nor the serial connection.   Ubuntu does not seem recognize the modem, apart from System - administration - networking, I have no idea how to configure the modem.  On my main computer I just plugged it in, selected the proper port and it worked.
Thanks again

---

### Post by Bartender on 2007-07-23
glx -
I've got 3 USR externals.  Two beige 5686-03's and one 5686E.  Plus one very odd Boca 56K serial modem.  They've all worked with KPPP, gnome-ppp, wvdial.  PCLOS, Ubuntu, Kubuntu, MEPIS, etc.
The only difference was that in 6.06 I could use the modem set-up in Network.  In Edgy and Feisty Network is broken and had to figure out how to use other methods.
But the point is, the serial external was about as straightforward as you could hope for in Linux.

You say the modem works fine in Windows.  With the modem on and securely connected to the PC, what happens when you type
```
sudo wvdialconf /etc/wvdial.conf
```
into terminal?  The modem should be recognized on ttys0...

Do you have another PC that you could try?  Toss in a LiveCD, type that command, see if the modem is recognized?

---

### Post by glx5667 on 2007-07-26
thanks, I'll try this tonight and be back to you tomorrow.

---

