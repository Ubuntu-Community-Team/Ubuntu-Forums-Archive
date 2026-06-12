---
title: "Can I forward a Mac OS X session to my linux box?"
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by skelooth on 2008-07-31
Hi, I recently made a thread about emulating mac os x and decided the hoop jumping and law breaking wasn't worth the time... especially when I'm in an office with legitimate Mac OS X boxes. 

Here's my question, can I create an account on one of our mac os x leopard machines, then forward it to my box? (similiar to forwarding gnome-session over an ssh connection)

How can I go about doing this... if it's at all possible? Thank you SO much for any help you can give.

---

### Post by pytheas22 on 2008-07-31
It's really easy to forward an Ubuntu session to OS X, but not so the other way around.  Apple goes out of its way to keep its protocols proprietary and undocumented--even though OS X is based on an open-source Unix kernel that Steve Jobs jacked from academia, he doesn't like sharing when it doesn't benefit him.  As a result, since most OS X applications don't use X11 (they use proprietary Apple protocols), you can't forward them over ssh to an Ubuntu box, as far as I know.

What you could do, however, is use vnc to remotely connect from Ubuntu to your Mac.  This should work fine.  Ubuntu already comes with a vnc client installed (I forget exactly what it's called and am not at an Ubuntu machine now, but I can look it up for you later if you can't figure it out), so you just need to install a vnc server on OS X, note the IP address of your Mac, and plug that into the Ubuntu vnc client to connect.

You can also of course still use ssh to connect from Ubuntu to your Mac over the command-line--you just need to run an ssh server on OS X--but I assume you want the whole graphical interface.

---

### Post by skelooth on 2008-07-31
Yes, I need to be able to forward firefox and safari, as we've come across a few mac only bugs here in the office. Specifically I need to be able to debug javascript and css without hijacking my coworker's computer. 

Is VNC my best option?

---

### Post by pytheas22 on 2008-07-31
Yes, in that case, I think VNC is the best way to go.

By the way, I'm pretty sure that you can run the Windows version of Safari in wine, in case that helps you.  But I guess you probably need to test on the Mac version...

---

### Post by skelooth on 2008-07-31
Yes, it HAS to be a mac. I ran my web app on identical versions of firefox on all three operating systems (mac,lin/win) and it's just mac that has the weird behaviors. (all code validates as xhtml strict and I can't find any reports of these 'bugs' on google)

---

### Post by cyberdork33 on 2008-07-31
I use this:
[www.logmein.com](www.logmein.com)

---

### Post by tiresia on 2008-08-01
You don't really need to install anything in Leopard. In OS X Leo you have a Server Client VNC service called Screen-Sharing (/System/Library/CoreServices/Screen-Sharing). You can configure it via System Preferences > Sharing > Screen-Sharing. It works quite well with Ubuntu. It is  at the same time a Vnc Client.

---

