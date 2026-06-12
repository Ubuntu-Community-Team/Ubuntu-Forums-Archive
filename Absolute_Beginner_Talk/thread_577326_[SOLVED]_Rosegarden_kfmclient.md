---
title: "[SOLVED] Rosegarden kfmclient"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by AkiraBergman on 2007-10-16
G'day Ubuntu-Linux lovers,

I got Rosegarden working on Feisty after changing it to low-latency. I played few MIDI files and also switched to the Notation Editor, and it looks very nice indeed.

But the Tutorial button under Help gives the following message;

Could not launch browser
Could not find service 'kfmclient'

I can view the Tutorial from the Handbook. Why does this happen? I searched the web and saw some references to a new Rosegarden source where this problem is solved. Apparently it is related to the switch to low-latency. I tried to compile the source with no success. I had the same problem when I clicked on a URL inside Rosegarden.

Should I worry about this? Would it cause problems in important functionalities?

---

### Post by LanDan on 2007-10-22
you could worry about it offcourse ;)
but if thats all what is wrong then that's all that is wrong i guess

---

### Post by Samhain13 on 2007-10-22
Hummm... the Tutorial link works fine here.
But I'm using Gutsy and the RealTime Kernel. The Tutorial link opens with Epiphany, although my default browser is Firefox. So I'm thinking that "Could not launch browser. Could not find service 'kfmclient'" means it's perhaps looking for Konqueror(?) and if it's not installed, then Epiphany-- which I happen to have installed. Just a guess though.

---

### Post by AkiraBergman on 2007-10-22
Thanks for the replies.

I now got Gutsy and it is not a problem anymore.

---

