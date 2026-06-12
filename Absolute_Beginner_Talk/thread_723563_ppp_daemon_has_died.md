---
title: "ppp daemon has died"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Joe Dinmore on 2008-03-13
Recently, I've been having a spate of 'modem hang-up' errors, and the log tells me that the pppdaemon has died.
Please tell me this is not a hardware problem!
(We are in the middle of a heat-wave here - almost two weeks of temperatures over 35C - mostly over 40C. The computer is in an un- air conditioned room. Is that relevant?

---

### Post by SpaceTeddy on 2008-03-13
does the ppp daemon say why it died ? also, what does 
> dmesg |tail
say after it died ?
does a simple restart of ppp (i.e. a pon dsl-provider) still work after the dying ?

---

### Post by Joe Dinmore on 2008-03-13
Thanks for the quick reply.
I'll let you know what that command does next time it happens. 
Yes, mostly if I use Gnomes PPP dial-up tool and get it to "detect modem", it finds it right away and I can go back online.
Sorry if I'm not answering what you asked - I'm painfully ignorant of all this.

---

### Post by Joe Dinmore on 2008-03-16
Wouldn't you know it? It's been working perfectly for days. 
The only thing I'm doing differently is that I have turned a cooling fan on in the room (not a computer fan, just a regular room fan). I blame the heat.

---

