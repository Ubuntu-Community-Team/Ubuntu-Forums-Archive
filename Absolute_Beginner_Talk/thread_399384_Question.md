---
title: "Question"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Coinnach on 2007-04-02
Probably a very stupid question but can you install 32bit Ubuntu Server 6.10 on an AMD64bit Server?

I need a 32bit version so that I can run a mail server suite that only runs in 32bit.

---

### Post by johnnymac on 2007-04-02
Yes you can - people do that quite often.  Most software you'll find isn't quite tuned for 64-bit usage.

---

### Post by teaker1s on 2007-04-02
simple answer is yes, but you will not benefit from using the processors full potential.
I would post a question in server section and see what people running 64bit servers say as there may be a 64bit program for what you wish to do.

Welcome to the forums

---

### Post by jvc26 on 2007-04-02
Yup in the same way you can run a 32bit desktop OS on a 64bit processor :) All you will lose out on is the extra gain in processor speed.
Il

---

### Post by Coinnach on 2007-04-02
Thanks guys, I appreciate it. The alternative is running the mail app in a vmware environment and I don't particularly want to do that for a production box.

---

### Post by johnnymac on 2007-04-02
Don't mistake using a 32-bit OS on a 64-bit OS as being "lower performing" processor wise - that's not the case.  You still get the full potential "computing" power your now just limited on your addressing space.  
 
The biggest advantage of 64-bit over 32-bit is the extended addressing in memory.  64-bit will allow you to break the 4GB of RAM; whereas, 32-bit is still suck below that mark.  The reason is the math applied to the addressing.  By moving the addressing scheme from 32-bit to 64-bit your possible memory address space grows from 2^32 to 2^64.  You will ONLY get the benefit of this if the application you are running is optimized for 64-bit addressing (right now not many truly are - they are just ported).

So, in all honesty - if you don't have the RAM - why bother with running 64-bit OS and incur the headache of finding stuff that works....for the most part.

---

