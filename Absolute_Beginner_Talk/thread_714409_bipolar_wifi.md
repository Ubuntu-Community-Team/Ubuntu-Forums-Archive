---
title: "bipolar wifi"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by R13120(1&lt; on 2008-03-03
yes it is bi polar.
one day it loves me the next day it hates me. 
it will work fine and I'll take my laptop with me 
some where out side of my wifi range and then
 it needs set up all over again when i get back. 
does any one have a more reliable adapter than 
the built in one? or Kwifi? i'm getting so tired of this.

---

### Post by Joeb454 on 2008-03-03
Well you say does anybody have a more reliable adaptor...

What Wireless Adaptor do you have in your laptop?

---

### Post by Rocket2DMn on 2008-03-03
I have yet to find a good wireless program either.  Most people use nm-applet to control their wireless, and you can store settings in there under different profiles.  I've also heard of wifi-radar among others, but I don't think they are really any better.
Sometimes running some of these commands can help you out:
```
sudo /etc/init.d/networking restart
sudo NetworkManager restart
```
They tend to only work some of the time though.

---

### Post by empthollow on 2008-03-03
the most solid wifi connection i had was when i followed a how to and did wpa supplicant manually in terminal.  i had zero disconnects.  it was great, however that doesn't work for me in real life situations cuz i like to take my laptop with me when i travel and i'm not going to spend 10 minutes at a hotel hoping i can get my wifi working.  SO... i use nm-applet,  it disconnects on me when the computer is idle and it loses my network key but it's better than it was in feisty.  in feisty it would disconnect and when i came back i would have to do a 
```
killall nm-applet && nm-applet
```
before it would let me reconnect.  now the worst that happens is i have to enter my long network key in and try to connect twice.  I like the interface though.

---

