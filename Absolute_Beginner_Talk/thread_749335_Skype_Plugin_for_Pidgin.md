---
title: "Skype Plugin for Pidgin"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-04-08
I am using the following plugin to enable the use of skype in pidgin: 

[http://myjobspace.co.nz/images/pidgin/](http://myjobspace.co.nz/images/pidgin/)

It works great, just have one issue with it. When I click to start pidgin it just starts skype, and then I have to again click to start pidgin. According to the user docs its supposed to start skype automatically (if pidgin is started) not sure why pidgin itself doesn't open though.

---

### Post by buried on 2008-04-09
Why don't you just install Skype, add the medibuntu respo's and type in terminal
```
sudo apt-get install skype
```

---

### Post by Crafty Kisses on 2008-04-09
> **buried said:**
> Why don't you just install Skype, add the medibuntu respo's and type in terminal
```
sudo apt-get install skype
```

You could also just go to the official Skype website and download the .deb package.

---

### Post by misfitpierce on 2008-04-09
I would prefer if I used skype more to just use all in 1 program... That is why I love pidgin over downloading AIM for linux or so on. I like to use all messaging services inside 1 dialog box. :)

---

### Post by abhiroopb on 2008-04-09
I think I need to make it a bit clearer. Basically I've had skype and pidgin running side by side for a long time. Recently I read about this plug in and thought I would try it out. Now I have all skype contacts in my pidgin. I also have skype installed, but it just runs in the background and I just use pidgin for all chats and when I call someone it puts me through to skype. Basically when I start pidgin, skype starts. I need to wait for it to load, and THEN I have to start pidgin again to start pidgin itself.

---

### Post by BigBrownChunx on 2008-04-11
Sorry, there's a bug in the Linux version of the Pidgin plugin that causes Pidgin to silently crash on startup when it tries to start Skype.  I'm still working out why this happens.  Until it's fixed, you might want to just leave Skype running in the background.

---

### Post by abhiroopb on 2008-04-11
Ah ok, that makes a lot of sense. Actually now what I do is when the computer starts up my skype automatically starts up, and then I can start pidgin at my leisure. So essentially I don't have to ever worry about skype. And I've turned off the auto-start skype, if not running option, generally makes life easier.

Otherwise a fantastic plugin, and thanks a lot for answering my question!

---

### Post by ArtPulse on 2008-05-26
Hey there! I've been using this for a few days... well, trying to, but it's impossible. Pidgin crashes every time I enable the Skype account. I'm using the very latest stable version of Skype.

I have to close Skype to open Pidgin again, or it just crashes on startup before I can see anything.

That's with the D-Bus one. Choosing the normal Skype at Protocol, I can connect but when sending a message, crashes.

But I just had a 10 lines conversation before Pidgin crashed, that's a record!

Still I need it to last more :( the idea is just awesome, I can still use skype for calls but I keep the conversations in the same pidgin window =) plus I still dont like the Skype look.

I'm on Ubuntu 8.04, Gnome

Does anyone know why? =( anyone had this? fixed this? =( help T_T

---

