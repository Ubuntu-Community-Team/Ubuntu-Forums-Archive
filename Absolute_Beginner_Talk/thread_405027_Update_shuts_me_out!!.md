---
title: "Update shuts me out!!"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-04-09
Hi,

I downloaded an Ubuntu update a couple of days ago and iit appears to have caused a problem with my nvidia driver.  Each time I try to boot up Beryl kicks in... it cannot find my graphic card (I think) and so I get logged out.  I've tried booting in Failsafe mode and get the same result.  Could someone please advise how I might get round this.  Is there, in Failsafe terminal mode for example, a line of code I could enter to close Beryl down?

I tried installing an nvidia driver using Envy, but this has not worked at all.  My graphics card is a Geforce 7300GT.

Thanks for any help.

---

### Post by Perfect Storm on 2007-04-09
```
sudo nano /etc/X11/xorg.conf
```

Find the line;

 Option         "AddARGBGLXVisuals" "True"

and remove it.

---

