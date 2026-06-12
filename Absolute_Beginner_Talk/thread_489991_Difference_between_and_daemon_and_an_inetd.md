---
title: "Difference between and daemon and an inetd"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by ndefontenay on 2007-07-01
Hi.

I'm currently configuring samba, and I would like to know what would be the difference between a daemon and an inetd.

The default is daemon.

What would make you choose to start your service as an inetd or a daemon?
Is there any pros and cons etc...

It's all blurry right now.

Thanks in advance for your enlightenment.

---

### Post by buzzmandt on 2007-07-02
[http://www.windowsecurity.com/whitepapers/The_Unofficial_Web_Hack_FAQ__Section_03.html](http://www.windowsecurity.com/whitepapers/The_Unofficial_Web_Hack_FAQ__Section_03.html)

dunno, kinda over my head but this might help

---

### Post by bodhi.zazen on 2007-07-02
A daemon is any (system) process detached from a terminal and running in the background.

[http://en.wikipedia.org/wiki/Daemon_%28computer_software%29](http://en.wikipedia.org/wiki/Daemon_%28computer_software%29)

inetd is an example of a daemon.

[http://en.wikipedia.org/wiki/Inetd](http://en.wikipedia.org/wiki/Inetd)

---

### Post by ndefontenay on 2007-07-02
Hi.

Thanks a lot for your answer.

I will just read what I got on inetd because this part is still not clear yet.

If inetd is just an exemple of a daemon, I don't understand how samba can give me the option of starting it with either a daemon or inetd...

---

### Post by Bachstelze on 2007-07-02
Basically, inetd is a daemon that will let you manage and run several services. Common services run through inetd are FTP daemons, ident daemons or time daemons. For each of them, you have the choice to either run it through inetd, or run it in stand-alone mode. Running it through inetd makes it easier to manage, but at the cost of a performance loss, especially on high load servers.

I don't know much about Samba, but if you're unsure, I think you should run is stand-alone, instead of trying to mfiddle with inetd.

---

### Post by ndefontenay on 2007-07-02
Hi.
Thanks a lot for the answer.
You've cleared a part of my understanding on Linux which was for a long time pretty dark : )

And for once, I'm sure I've created a thread that will be useful to others too :)

---

