---
title: "inabality to type password [Resolved]"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by eternalwolfman on 2007-04-28
hi! this is my first post, and first attempt at linux. when i open terminal and attempt to enter a code that requires a password, my keypad seems to lock up. i can only press enter. i looked through other threads and faqs without seeing any similar problems. any help would be fantastic!

-greg.

---

### Post by taurus on 2007-04-28
Actually, your keyboard does not lock up.  It doesn't move or echo when you type in your password.  That's normal.  Just type in your password and hit Enter.

---

### Post by aysiu on 2007-04-28
This is a bug that will never be fixed. Just type your password and hit Enter.

More details (with screenshots) here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by Fidelio on 2007-04-28
I know this may sound obvious, but when you type your password into a terminal, nothing appears on the screen, not even asterisks or anything, so it doesn't  look like you're entering anything. This took me by surprise the first couple of times.

---

### Post by DezSP on 2007-04-28
It's an added bit of security. Prevents shoulder-surfers from knowing the length of your password, and (hopefully) its contents will remain well-hidden enough to prevent all the normal modes of password-guessing.

Over the top? Well, Linux was invented by computer geeks...

Oh, and to quote a classic, this isn't a bug, it's an undocumented feature. :p

---

### Post by eternalwolfman on 2007-04-28
thank you all so much for your quick responses! now on to getting ut to work ;P

-greg

---

### Post by aysiu on 2007-04-28
> **DezSP said:**
> It's an added bit of security. Prevents shoulder-surfers from knowing the length of your password, and (hopefully) its contents will remain well-hidden enough to prevent all the normal modes of password-guessing. I've seen this mentioned many times, and it's not true. Maybe that was the original intention when Unix was created, but it no longer applies in today's Ubuntu use.

First of all, if someone is standing over your shoulder, she can look at what keys you're pressing--far more informative than looking at the screen. Or, if she has her eyes closed, she can count (by listening to how many keys you press) how many characters are in your password.

Not to mention the fact that GUI authentication (GDM and *gksu*) does give back visual feedback. Read the link I posted earlier.

---

### Post by helgi on 2007-05-15
Wow, I had this problem as well. So this is the thing? OK GREAT!

---

