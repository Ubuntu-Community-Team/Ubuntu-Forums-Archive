---
title: "Download Server?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by loadedk on 2007-12-12
Hello, I have recently set up an Ubuntu server thats is sharing files between my XP machines and acting as the proxy server.  Is there a way to setup the server so that it acts as my download server?  I.E. - When I click a link on my XP machine firefox browser to download the server does all the work?

---

### Post by Origin415 on 2007-12-13
I'm not quite sure what you are asking, but it sounds like you want x forwarding, where firefox  runs on the server and the windows machines to just view and control it, and dont do any of the actual processing. x forwarding is the basic element of thin clients, which dont have a hard drive and barely enough memory and processing power to just x forward an entire desktop ]environment from a server.

When you open an x forwarded program, its just as if you opened it on the server. For example, if you x forward Nautilus, you will be exploring the *server's* hard drive. The window is just displayed on a different computer.

While this is easy to do in Linux, Windows throws a nasty kink into it. On the linux side, just have firefox installed on the server, you dont need an x environment like gnome, just firefox and is dependencies. If you had a linux box, you could x forward now simply by doing
```
ssh -X *server ip* firefox 
```

However on Windows you need a special program to do it. At my university they give us X-Win32 for this purpose free, but I dont know if you can get it free otherwise. Another solution is Xming, which is open source. You can get that here:
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
But I dont know much about it so you'll have to read the documentation for yourself.

Hope this helps.

---

