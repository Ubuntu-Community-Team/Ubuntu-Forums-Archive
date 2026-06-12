---
title: "Whoa...VPN?!  Is anything &quot;easy&quot;?"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by bigbadblo on 2005-05-24
Ha, this Linux business is kinda fun... if your lines between pleasure and pain are blurry!

No, really -- thanks to everyone who helps us newbs in here.  I appreciate it greatly.

Now, the next baffler.  I live in a college residence hall.  All of our networks are VPN'd, and on a Windows machine that's no problem for me.  However, like I said earlier -- this linux-speak is all foreign to me.

I've been hunting around for a couple of days now trying to figure out what I need to do in order to setup a VPN connection in Ubuntu (or Linux in general).  I'm stumped.  Completely.

Any pointers?  Places to look that'll describe it in somewhat understandable jargon?  Everywhere I look, I end up with this pained/confused look on my face.  Ahh, the joys of learning a new language!

Thanks for all your help,

blo

---

### Post by f.prisson on 2005-05-24
For documention see about the cisco vpn client have a look at this:

[http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/](http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/)

and this

[http://security.sc.edu/tools/vpn/instruct/vpnclient_linux.html](http://security.sc.edu/tools/vpn/instruct/vpnclient_linux.html) 

But may me hard to setup for a beginner. You could also try ```
sudo apt-get install vpnc
``` but I don't know it and never tried it.

---

### Post by bigbadblo on 2005-05-24
Wouldn't using the command "sudo apt-get install vpnc" require me to have an internet connection?  I'm not really sure yet how apt-get functions, but I was under the impression that it pulls packages from central webservers and builds packages as needed...

Just wondering

blo

---

### Post by Mez on 2005-05-24
most of them it will pull from the webserver, but if you've never had an internet connection, then it will pull from the CD

If you've had it connected to the web, but dont anymore, then edit your /etc/apt/sources.list so that all lines except for the line similar to

deb cdrom:[ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

have a # at the start

then do

sudo apt-get update

and it will make it so it will only pull packages from the CD.

However, most likely, the package you need wont be on the CD, as the CD has only the base system, plus a few extras.

---

### Post by bigbadblo on 2005-05-24
How about the DVD edition?  I went all out when I decided to try this Ubuntu business...  ;-) 

If I pop the DVD in, and follow your instructions... might I get somewhere?  I'll go try it!

blo

---

