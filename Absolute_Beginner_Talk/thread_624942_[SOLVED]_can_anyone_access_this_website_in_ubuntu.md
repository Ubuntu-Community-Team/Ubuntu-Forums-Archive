---
title: "[SOLVED] can anyone access this website in ubuntu?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-11-27
hi guys, i havent been able to get into my college website to access notes for a while now so im not sure if its ubuntu or network, the website isnt down or anything so should work

its [www.abcol.ac.uk](www.abcol.ac.uk)

could someone see if they can access it and let me know so i can try sort it?

cheers

alex

---

### Post by overdrank on 2007-11-27
> **darkeale said:**
> hi guys, i havent been able to get into my college website to access notes for a while now so im not sure if its ubuntu or network, the website isnt down or anything so should work

its [www.abcol.ac.uk](www.abcol.ac.uk)

could someone see if they can access it and let me know so i can try sort it?

cheers

alex

Yes I can few the page.

---

### Post by Paul820 on 2007-11-27
Works fine here, no problems.

---

### Post by darkeale on 2007-11-27
ok thanks, any ideas why i cant?

---

### Post by Nano Geek on 2007-11-27
I can't seem to, but I'm in Windows.

---

### Post by jfinkels on 2007-11-27
> **darkeale said:**
> ok thanks, any ideas why i cant?

Can you ping the address?```
ping www.abcol.ac.uk
```

---

### Post by FuturePilot on 2007-11-27
Hmmm. Another site that gets stuck at Transferring data. I saw another thread similar to this and the same thing happened. Got stuck at Transferring data....
```
 ping -c4 www.abcol.ac.uk
PING www.abcol.ac.uk (194.82.239.33) 56(84) bytes of data.

--- www.abcol.ac.uk ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3009ms

```

Edit: Hmm works now :confused:

---

### Post by bobpur on 2007-11-27
I can't get onto it either.

---

### Post by darkeale on 2007-11-27
ping doesnt work, any other ideas?

---

### Post by NullHead on 2007-11-27
> **darkeale said:**
> hi guys, i havent been able to get into my college website to access notes for a while now so im not sure if its ubuntu or network, the website isnt down or anything so should work

its [www.abcol.ac.uk](www.abcol.ac.uk)

could someone see if they can access it and let me know so i can try sort it?

cheers

alex

The page won't load for me ... when I try to ping it I get this output.```
33 packets transmitted, 0 received, +15 errors, 100% packet loss, time 32410ms
```

:shock::-s

---

### Post by Grey Box on 2007-11-27
It's possible, if you can't access it at all nor ping it, that somehow there is a net-split between your ISP and the target server. The site might even be blocked (eg: because lots of spam was coming from that address or something, or there might be a rude word on the lingusitics page ;), but either way you can get around that problem.

Try using a proxy to access the site, eg: [http://www.megaproxy.com]("http://www.megaproxy.com") which offers a limited free service. Good enough for testing anyway.

If you find it's accessible via proxy, then consider setting up a proxy system for yourself, like Tor (it will anonymize you very effectively too). There are good HOWTO's around for that.

---

### Post by darkeale on 2007-11-27
just set up tor and its working fine, a lot slower than with no proxy, but hey it works, and its only this website i need the proxy for so its all good.

thanks a lot

alex

---

