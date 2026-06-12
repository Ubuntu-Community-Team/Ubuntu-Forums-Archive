---
title: "Can not get Desktop (Solved)"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by bobaj on 2006-10-12
When I power up the computer, I only get a terminal.  The prompt asks for a login and password, but I never get a desktop.  Any suggestions.

I know this problem is related to things I have done.  I tried to get the Wifi and soundcard to work and ran into all sorts of problems.  I deinstalled the stuff I remembered putting in and everything went down.  Any suggestions or should I just give up on Ubuntu for a laptop.  Is this system really for novices, or do you need prior experience with Linux/Unix to get it to work?

Frustrated,
thanks
Bobj

---

### Post by aysiu on 2006-10-13
Maybe this will help:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by jordanmthomas on 2006-10-13
log into the terminal and type:
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
You can accept defaults for most of it, but if you see something you know is wrong, change it
Then, try to start gdm
```
sudo gdm
```
If it doesn't work, report back with what goes wrong.

**beaten

---

### Post by bobaj on 2006-10-13
Thank you for the help.

I went to the site you recommended
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)
and it brought back the desktop.

Thank you very much for your help.

Sincerely,
Bobj

---

### Post by bobaj on 2006-10-14
Thank you for the help.

Just to help others, this is how I believe that I got into the problem.

Ubuntu doesn't work properly with my sound card in my laptop.  To try and fix it I used the Synaptics Manager to find libraries with codec's o fix the problem.  I added quite a few entries in my attempt.

The following day, my WiFi card stopped working. I believe because of something that I loaded from the multimedia and multimedia (universal) sections.  To repair the damage, I removed everything from those sections hoping to restore the card to working order.

After removing those entries, the desktop stopped working.

Hope this helps someone in the future.
Bobj

---

