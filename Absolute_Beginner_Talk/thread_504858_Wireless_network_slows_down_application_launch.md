---
title: "Wireless network slows down application launch"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by toutatis on 2007-07-19
Hi,

I installed Ubuntu Feisty a couple of days ago using Wubi and everything works fine. (BTW: I've made an [[COLOR="DarkGreen"]**online tutorial**[/COLOR]]("http://www.romaniflo.nl/2ubuntu")). I even got Beryl/XGL/Compiz running with desktop cube. 

There's just one little thing I can't get solved. It takes about 10 seconds to launch an application. Even simple small applications like xterm or gedit start that slow. When the program is running, nothing's wrong, it's only the startup. It's not an CPU issue, it's about 80% idle most of the time. [[COLOR="DarkGreen"]**See screenshot**[/COLOR]]("http://www.romaniflo.nl/img/Screenshot.jpg"), taken a few seconds after I started gedit, don't know exactly because the Screenshot utility is slow as well. 

But after I disconnect my wireless network the problem is completely solved: gedit starts in about a second again.

I used Wireshark to watch network traffic. Only my router sends me lots of packages, I guess it's a heartbeat. Average about 400 bytes/sec. That shouldn't be a problem. 

Does anyone have a clue?

Grtz,

Roel

---

### Post by toutatis on 2007-07-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/94048](https://bugs.launchpad.net/ubuntu/+bug/94048) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Found the solution for this problem in [bug #94048]("https://bugs.launchpad.net/ubuntu/+bug/94048").

After I added my hostname to the local loopback address (127.0.0.1) in /etc/hosts and my problem was solved.:grin::grin:

Roel

---

### Post by tak1150 on 2007-08-21
Thank you toutatis!

You made my day! This works.
Just for the record, my machine is Inspiron 1150, P4.

---

