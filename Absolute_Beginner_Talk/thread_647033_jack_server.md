---
title: "jack server"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2007-12-21
what  is a jack server and how do i install it . several audio progams require it to run

---

### Post by spiderbatdad on 2007-12-21
[http://www.linuxdevcenter.com/pub/a/linux/2007/08/02/an-introduction-to-linux-audio.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2007/08/02/an-introduction-to-linux-audio.html?page=3)


google is your friend

---

### Post by blueridgedog on 2007-12-21
Here is a start:

[http://jackaudio.org/](http://jackaudio.org/)

[http://qjackctl.sourceforge.net/](http://qjackctl.sourceforge.net/)

Also, see the 12/2007 issue of the Linux Journal, page 62, for a nice article on creating a portable hard disk recorder.  The use of JACK, installation and much more is in the article.

---

### Post by sedge on 2007-12-22
Hi
I am trying to use Jack but I get the following message

Could not create JACK client

Is the jackd server running?

How do I start jackd server?

Merry Christmas
Best regards
Ken

---

### Post by CatKiller on 2007-12-23
On Gutsy, there's an application in the Sound and Video section called "JACK Control". If you run that and press the Start button, it will start a JACK server for you. I think the package, if you don't have it installed, is qjackctl.

EDIT: And it seems that you can start a JACK server with the **jackd** command. There's more information at **man jackd**.

---

