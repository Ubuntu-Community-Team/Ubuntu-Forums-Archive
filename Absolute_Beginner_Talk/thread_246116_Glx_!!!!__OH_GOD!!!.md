---
title: "Glx !!!!  OH GOD!!!"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Mazehero55 on 2006-08-28
Hrey I got a friend here to tell me how to get glx working, a little bit. But direct rendering is turned off. Does anyone know how to get an Intel 82810 working compleatly with OpenGL? 

Oh yes and one more thing. Then only thing that's keeping me from going Ubuntu fully is, internet. Can anyone help me get an Intel 537EP chipset working? I've looked up some stuf about it and nothing they say to do works. Plus I also need to know how to install my Kernal headers or source or something for it.

I would be sooo... happy if someone told me how I could fix these or at least just one one them. Thanks.

---

### Post by philipgm on 2006-08-28
Google has this:

[http://www.worldwindcentral.com/wiki/Video_Card_Compatibility#Intel](http://www.worldwindcentral.com/wiki/Video_Card_Compatibility#Intel)

---

### Post by janbockaert on 2006-08-28
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#Intel_Cards](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#Intel_Cards)

if your card is not listed, go buy a new one :)
if u are new to linux, you may want to use a distribution that supports xgl 'out of the box'. The only big distro with built in support for xgl is opensuse. In opensuse, installing xgl is just pushing a button. There are a lot of excellent threads in this forum and on compiz.net to help you set up xgl in ubuntu, but do not expect it to be a walk in the sun. 

this is the thread that did the trick for me: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) it is for ati, but it worked for my nvidiacard. So, who knows, maybe it will work with intell.

If xgl doesn't work, aiglx should work with recent intell cards.

---

### Post by Mazehero55 on 2006-08-28
Hey I found a binary driver for my card, But it says Xfree86 on it, But doesn't ubuntu have xorg. Does it make a difference?

---

### Post by janbockaert on 2006-08-29
yes, your driver moest support xorg 7.0 But i don't believe you need binary drivers for intel cards. Intel drivers are open source.

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

---

### Post by Metacarpal on 2006-08-29
> **Mazehero55 said:**
> Hey I found a binary driver for my card, But it says Xfree86 on it, But doesn't ubuntu have xorg. Does it make a difference?

xorg is a fork from xfree86, so it should be compatible.

---

### Post by PingunZ on 2006-08-29
Seriously, if you create a topic google first.
And if that doesn't help, make a topic with a DECENT title.
Then make a DETAILED description.

---

### Post by Mazehero55 on 2006-08-30
sorry, if my post was bad in any way. I've just found that any post I make with a weird name gets the most replies. In fact those are probably the only ones of my posts that get replies. 

I'm sorry if my discriptions weren't the best, I'm a newbie and that's all I knewe about the problem so far.

---

