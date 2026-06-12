---
title: "Network-Manager icon missing [Resolved]"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by conteur on 2007-04-26
I right clicked/removed the panel icon for Network-Manager, and can't figure out how to get it back. nm-applet is running and so is Network-Manager, Does anybody know how I can restore the icon?

---

### Post by jjbean on 2007-04-26
Right click on the panel. Choose Add to panel. Scroll through the list to find what you want. I think this is what you are looking for.

---

### Post by conteur on 2007-04-26
No. The icon that I want is not in that list. Check out this page: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)  This is what you get when you install Network-Manager-Gnome. I tried re-installing and still nothing.

---

### Post by stmiller on 2007-04-26
open a terminal and type:

$ sudo killall nm-applet

then

$ nm-applet &

When logging out of gnome, make sure to check the box 'save session' or whatever it's called. The applet will start next time you enter gnome.

---

### Post by aysiu on 2007-04-26
In [the terminal](http://www.psychocats.net/ubuntu/terminal), type ```
killall nm-applet
nm-applet &
```

---

### Post by medad on 2007-04-26
Is it possible that you removed your notification area?  There should be 2 lines of dots that appear to be almost invisible near your speaker icon.  You might have accidently removed it.

If this what happened to you, once you have added the the notification area back to the panel, you will need to exit and log back in.  This will bring back your network manager icon.

---

### Post by conteur on 2007-04-26
Thank you Medad. That was it.

---

### Post by jaywee on 2007-05-04
I just add the notification area back, but still no icons,really need some help!

---

### Post by jaywee on 2007-05-04
I just add the notification area back, but still no icons,really need some help!

---

### Post by Bram-NL on 2007-05-17
I have manually removed the Network Manager icon (by clicking "Remove from panel"). Very stupid, because now I can't get it back. The tips in this thread didn't help me yet. How can I restore the NM-icon back in de notification area?

> **medad said:**
> [...] once you have added the the notification area back to the panel [...]
Hmm... I'm unsure about this one... How do I add the notification area back?
Still seeking my way thru the Linux (Gnome) Desktop :)


Aaaaah forget my post! I found it in the Add to panel-list. Doh, I was searching too hard for the network-manager. But the Notification Area is over there two! ;)

I'm starting to like this desktop :)

:popcorn:

---

