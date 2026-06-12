---
title: "cannot enable rng"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by vroy on 2007-01-25
Hi,
     I upgraded my laptop from Dapper to Edgy yesterday. There were some problems with fonts in Emacs, but after consulting past posts,  I could fix it. I've a dual booting in my laptop. Now, when I boot with Linux, it's showing a message like
[number, number] hw_random cannot enable rng    [aborted] 

I was wondering what could be the reason for this. It seems to me that it can't find the above in the hardware. But, then was not the previous versions of Ubuntu using it. If it helps mine is a Dell Inspiron 600m laptop with Pantium M processor. Any suggestion or help  will be highly appreciated.

---

### Post by K.Mandla on 2007-01-26
That message is mostly harmless. Certain Intel motherboards used in Pentium III-era machines (if I remember right; I might have that part wrong) had a hardware random number generator; the software is probing for that feature and reports back when it can't find it. 

Since your 600m post-dates that feature by a long shot, you're getting that message. You can safely ignore it. :) (Isn't it wonderful when someone tells you that?)

---

### Post by vroy on 2007-01-28
Thanks K. Mandla.

---

### Post by vroy on 2007-01-30
I understand that the message is harmless.  I was wondering whether I can get rid of this message.

---

