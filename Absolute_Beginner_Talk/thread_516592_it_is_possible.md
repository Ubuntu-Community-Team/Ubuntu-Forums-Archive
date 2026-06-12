---
title: "it is possible"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-08-03
can you have one computer - that can be used as two?

two monitors - one computer - two users both surfing and doing two different things etc..

might be a stupid question but worth an answer lol

---

### Post by Cypher on 2007-08-03
You can have many remote users, and provide full graphical capability through VNC or similar software. But you cannot have two physical users on the same machine.

---

### Post by reckless2k2 on 2007-08-03
Cypher, Isn't it possible to somehow bind a terminal session to a video output? For instance, i run an x session on another terminal. I thought I saw something about that session being on another terminal. Almost like as if you were running LTSP. I can have several users logged in running x at the same time. it's just how to get server 0 on one video output and server 1 on the other.

---

### Post by silent1643 on 2007-08-03
that would be awesome, but what would this require? two of everything in order for this to work - mouse, keyboard, and monitor? how could linux tell the difference on which is for each terminal?

i basically just want another terminal for web browsing in my house instead of buying another (although cheap) computer

---

### Post by Hospadar on 2007-08-03
It sounds like you are talking about plugging in two keyboards/mouse/monitor and I really have no idea how to make that happen.  It would no doubt involve having two sets of hardware, (mouse/kbd/monitor) plugged in, and then some oh so tricky editing of you xorg.conf as well as probably some other startup scripts.  I've never heard of any software to do this easily although it may be out there.

I suspect the best way to do this would be to get another (really cheap if you want, it doesn't really matter) machine and put linux on it, connect it to your home network, and then connect to the main machine with ssh or the remote desktop provided by linux.

You can configure it in System->Preferences-Remote Desktop

---

### Post by Cypher on 2007-08-03
Most video cards these days support 2 video out's and it should be possible to have XORG send seperate sessions to those two outputs. But that doesn't solve the issue of how you're going to have two people controlling their own individual sessions.

There is still one computer which means that you'd have a single set of keyboard/mouse.

Most PC's these days are so cheap that it doesn't even make sense to try what you're doing. One of the things from a while back that some people still kinda look at is Thin Clients. You essentially have a single beefy (and I mean REAL beefy) server that sits in the middle of a network that houses all of the applications and so on. You'd then have a bunch of thin clients, essentially nothing more than  monitor/keyboard/mouse that connect to this server through the network and have all the application served to them.

In a home environment this is truly overkill. So multiple PC's might be the best course of action here..

---

### Post by reckless2k2 on 2007-08-05
yeah i was under the impression that this was going to be a local solution. i didn't realize that the need or use would be related to having a terminal in another area. in that case, think client is what you're looking for. they are cheap but for a few bucks more you can get a cheap pc. sounds more like the way to go but you can use it with LTSP and get a central server control point if you want.

---

### Post by sdowney717 on 2007-08-05
[http://desktop-multiplier.userful-corporation.qarchive.org/](http://desktop-multiplier.userful-corporation.qarchive.org/)

I found this and claims up to 10 concurrent users. I was wondering if there is a free option.

---

### Post by overdrank on 2007-08-05
> **silent1643 said:**
> can you have one computer - that can be used as two?

two monitors - one computer - two users both surfing and doing two different things etc..

might be a stupid question but worth an answer lol

HI have you seen this link
[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

---

### Post by sdowney717 on 2007-08-05
[https://wiki.ubuntu.com/MoreUbuntu](https://wiki.ubuntu.com/MoreUbuntu)

moreubuntu project

---

### Post by silent1643 on 2007-08-06
wow great links, thanks guys
i also found this these
[http://oldwiki.linux-vserver.org/MoreUbuntu](http://oldwiki.linux-vserver.org/MoreUbuntu)
[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

---

### Post by Scipio_Publius on 2007-08-07
[http://userful.com/products/free-2-user-faq](http://userful.com/products/free-2-user-faq)

I found this link too since I am thinking to do the same thing.  I have not tried it yet though.

---

### Post by jbarry on 2007-08-10
Here is one more link,m this one is a six-in-one setup

[http://www.linuxtoys.org/multiseat/multiseat.html](http://www.linuxtoys.org/multiseat/multiseat.html)

---

