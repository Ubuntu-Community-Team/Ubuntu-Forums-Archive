---
title: "Evolution Freezes"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by dconstruct on 2008-02-03
I tried to a large file to my gmail account so that I could download it later on (800 mB) and when I tried to send it through Evolution, it froze, obviously, and I exited the program.  Well, now that message is in my Outbox (On My Computer) and every time I try to start up Evolution to check my mail, it has to go through the process of sending it again and it freezes again.  I'd like to, if at all possible, go through the backend somehow and remove this email from my Outbox.  Because, every time I just click on it and press Delete, it tries to retrieve it from the server first.  Or it marks a line through it and when I restart Evolution again, it's still there.

I'm running gutsy on an HP 530 laptop that isn't at all fast enough to handle sending large emails.  ;)

Thanks!

Adam

---

### Post by jken146 on 2008-02-04
You could try to find the relevant file for the offending message and delete it.  It'll be somewhere within ~/.evolution I believe.

---

### Post by dconstruct on 2008-02-05
Not finding anything that I can see.  I'm not a Ubuntu expert by any means, but there doesn't appear to be any file associated with particular emails, just an Outbox file that I can't seem to open (i double click it and nothing happens..)

Any ideas?

Thanks!

---

### Post by dcstar on 2008-02-05
> **dconstruct said:**
> I tried to a large file to my gmail account so that I could download it later on (800 mB) and when I tried to send it through Evolution, it froze, obviously, and I exited the program.  Well, now that message is in my Outbox (On My Computer) and every time I try to start up Evolution to check my mail, it has to go through the process of sending it again and it freezes again.  I'd like to, if at all possible, go through the backend somehow and remove this email from my Outbox.  Because, every time I just click on it and press Delete, it tries to retrieve it from the server first.  Or it marks a line through it and when I restart Evolution again, it's still there.

I'm running gutsy on an HP 530 laptop that isn't at all fast enough to handle sending large emails.  ;)

Thanks!

Adam

Disconnect your network connection and start Evolution, when it times out you should be able to delete the message.

---

