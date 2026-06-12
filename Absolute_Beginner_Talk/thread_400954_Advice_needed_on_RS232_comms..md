---
title: "Advice needed on RS232 comms."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by skywatcher on 2007-04-04
Hi

Is there anyone out there who can give me some advice on how to set up an RS232 link between, say, a laptop running Dapper, and an external device (such as a logger) that transmits plain text (ASCII) data?

On Windows I use HyperTerminal with COM1/2 etc. and then simply collect the data in a text file to import into Matlab. Can I do the same on Linux?

Please help!

Thanks

---

### Post by freebird54 on 2007-04-04
I am no expert on this - but I used to run an 8 port BBS - and this link might help you out.

[http://www.uni-koeln.de/rrzk/systeme/linux/infos/howto/Serial-HOWTO/Serial-HOWTO-6.html](http://www.uni-koeln.de/rrzk/systeme/linux/infos/howto/Serial-HOWTO/Serial-HOWTO-6.html)

Hope that's all you need!

BTW - ckermit and gkermit (presumably a Gnome kermit) were in Synaptic when I looked.

---

### Post by skywatcher on 2007-04-05
Thanks, freebird54. I'll check it out.

---

### Post by doddi on 2007-04-05
I am new to linux so dont shout if I am totally wrong :-)

I have found this [link]("http://alist.control.com/pipermail/automation/2004-September/030651.html") maybe it will be useful to you.

Basically it appears that you should be able to do what you want by using the dd command and any contents to forward to a file. This is only a guess but looks promising.

doddi

---

### Post by skywatcher on 2007-04-06
Hi doddi

It does indeed look promising. I'll try it. Thanks.

---

