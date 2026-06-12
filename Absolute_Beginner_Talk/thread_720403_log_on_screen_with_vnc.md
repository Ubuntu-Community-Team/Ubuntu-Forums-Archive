---
title: "log on screen with vnc"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2008-03-10
how can i make vnc start so that i can see the login screen when i vnc in?

---

### Post by Ecclesia on 2008-03-10
Hi There,

Here's a solution that I found here: [http://ubuntuforums.org/showthread.php?t=42941](http://ubuntuforums.org/showthread.php?t=42941)

basically you make sure that you've installed vnc4viewer, and then go to your login manager, click on "remote" and enable the login window (I've clicked "same as local).  I couldn't find the XDMCP tab, but there is a configure button, in which I deselected "Honor Indirect Requests".  

Then you put this code at the end of /etc/inetd.conf:

```
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
```

You can play with parameters here if you like to get something that works well for you.  I changed the size of the x window to match my nokia tablet by putting this in the above code: -geometry 800x480

After restart I was able to access the login window with vncviewer.

Hope this helps

---

