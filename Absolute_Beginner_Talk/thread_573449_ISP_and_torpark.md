---
title: "ISP and torpark"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-10-11
my ISP is blocking some websites, i used to use Torpark in windows to open blocked websites, what is the alternative for torpark in ubuntu ???

---

### Post by Insightfill on 2007-10-11
For Firefox only, Torbutton is an addon for TOR only, while FoxyProxy is more general-purpose (multiple proxies).  I've not used either.

Torbutton: [https://addons.mozilla.org/en-US/firefox/addon/2275](https://addons.mozilla.org/en-US/firefox/addon/2275)

FoxyProxy: [https://addons.mozilla.org/en-US/firefox/addon/2464](https://addons.mozilla.org/en-US/firefox/addon/2464)

---

### Post by Dr Small on 2007-10-11
Tor; [http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

---

### Post by n3tfury on 2007-10-11
> **akkad said:**
> my ISP is blocking some websites, i used to use Torpark in windows to open blocked websites, what is the alternative for torpark in ubuntu ???

just for kicks, would you mind naming your ISP?

---

### Post by akkad on 2007-10-12
Etisalat

---

### Post by Incense on 2007-10-12
Not sure if this will solve your problem, but when Comcast blocks google sites (I have no clue why they do this) I use [OpenDNS,]("http://www.opendns.com/") and things work fine at that point. Maybe give it a shot. All the internet love, none of the slowdown. ... of course there is no anonymity with [OpenDNS]("http://www.opendns.com/") like you get with Tor....

---

### Post by akkad on 2007-10-12
none of the above worked with my ISP :( , by the way am using the web site : [https://vtunnel.com](https://vtunnel.com) to open blocked pages and it is fine but it doesnt allow running some scripts and it has some limitations, do u know any software that at least use the same technique like vtunnel ??

---

### Post by Incense on 2007-10-13
You could just run Tor...have you tried that?

[http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/]("http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/")

---

### Post by n3tfury on 2007-10-13
> **akkad said:**
> Etisalat

i feel bad that you have to use an ISP like that.  hopefully someone can help out.

---

### Post by akkad on 2007-10-13
> **Incense said:**
> You could just run Tor...have you tried that?

[http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/]("http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/")

i would like to go thru the steps in the provided URL but seems it needs an advanced ubuntu user cuz actually from the 2nd point am stuck, i have some output on the terminal where i dont know what to do :(

---

### Post by Incense on 2007-10-15
VIM is just a text editor, you can use gedit instead of VIM so you can edit those files. VIM takes a bit of getting used to. 

so instead of 

> sudo vim /etc/tor/torrc

use

> gksu gedit /etc/tor/torrc

---

