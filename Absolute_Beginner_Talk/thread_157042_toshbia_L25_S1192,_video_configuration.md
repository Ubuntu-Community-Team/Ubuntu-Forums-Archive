---
title: "toshbia L25 S1192, video configuration"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by xxFelixDCatxx on 2006-04-08
Alrighty, I have this Tosiba L25 laptop and am trying to install ubuntu (obviously).  I figured I would try to get it working via the live cd, so I knew all the basics would be compatable.  Sure enough, there's an issue with the 'xserver', I assume to be a video configuration issue.  

So here's my video card information.
it's an ATI Radeon xPress 200M series.

I am completely new to linux as a whole, but would love to try out the OpenSource software available, and seeing as how ubuntu is the most preferred version out there, I figured this would be  a good place to start.  If anyone can help me I would greatly appreciate it.

---

### Post by sn123 on 2006-04-08
[QUOTE=xxFelixDCatxx] Sure enough, there's an issue with the 'xserver', I assume to be a video configuration issue.  

So here's my video card information.
it's an ATI Radeon xPress 200M series.
[/QUOTE]
somebody should be able to help you out if you provide more details about the "video configuration issue" i.e. what's the issue, what kinda error you get, do you get the graphical interface at all or xserver doesn't even start? etc. etc.
most probably it's got something to do with incompatible driver, try reconfiguring xserver and select a generic video driver like "vesa" and see if the problem goes away.
```

sudo dpkg-reconfigure xserver-org

```

---

### Post by cwmccabe on 2006-04-10
I have some basic info for a Toshiba L25-S119 at the following URL:
[http://cmccabe.freeshell.org/ubuntu_l25_s119.html](http://cmccabe.freeshell.org/ubuntu_l25_s119.html)

Maybe that will help?  I had a video card issue when I first installed Breezy, but it was easy enough to fix after a bit of googling.  There's a bit of info and a useful link my page (which was made for [www.linuxforlaptops.com)](www.linuxforlaptops.com)). 

Also, I should add that I'm not sure how similar the L25-S119 and L25-S1992 are, but I suspect that they are similar.

---

