---
title: "amaroK 1.3.xx.9 and not 1.4.2"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-10-27
I installed amaroK via get-apt install amaroK and got version 1.3.something.9. It looked great! Lyrics, wiki's and everything else you ever wanted from a music player. 

Unfortunately it froze 3 times in one session. Not very tolerant of this, I went looking for reasons. I found that I ended up with two questions.

Is amarok compatible with Gnome? I get a lot of KDE info but couldn't find very much on Gnome. Is this a factor that could influence it's stability? 

Second Question?
Why didn't I get the 1.4.2 version? I assume this has to do with the repositories. How can I get version 1.4.2 on Ubuntu/dapper?

---

### Post by orb9220 on 2006-10-27
You should of used synaptic and add repos from the menu instead of apt-get.

And no it runs fine under gnome which I have run under dapper and edgy. Versions 1.3.9 thru 1.4.3

---

### Post by Belgatom on 2006-10-28
Before I started this thread, I had already uninstalled version 1.3.9. When I now want to install amaroK by selecting it within Synaptic, I keep getting warnings and impossibilities. 

In "simple mode" :
> 
Cannot install "amarok"

This application conflicts with other installed software. To install "amarok" the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict. 


In "advanced mode" : 

When I select "amarok" and mark it for installation, I get: 

> amarok:
 Depends: amarok-xine but it is not going to be installed
 Depends: libtunepimp3 (>=0.4.2) but it is not installable
 Depends: libvisual-0.4-0 (>=0.4.0) but it is not installable

What worries me is the "it is not installable" thingie. How do I sort this out?

---

### Post by Bachstelze on 2006-10-28
Those packages exist only in Edgy. If you're running Dapper, it's normal you can't install them. Instructions to install Amarok 1.4.3 on Dapper are [here](http://kubuntu.org/announcements/amarok-1.4.3.php).

---

### Post by Belgatom on 2006-10-28
Thx.

I did all that was written on that page and received the OK the text talked about. But how do I now install amarok? Will I get the correct 1.4.3 version if I do get-apt install? 

Only the third day on Ubuntu, so I am walking carefully...

---

