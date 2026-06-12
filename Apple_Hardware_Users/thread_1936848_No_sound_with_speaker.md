---
title: "No sound with speaker"
date: 2012-03-06
forum: Apple Hardware Users
---

### Post by johnPB on 2012-03-06
Hello, 
I have an iMac with Snow Leopard and Ubuntu 11.10 installed.

The sound with Snow Leopard works fine and before it worked equally well with Ubuntu but suddenly no longer works with the speaker but when I put the headphones I have the sounds.
Perhaps because of updating Ubuntu?

Can you tell me how I can solve this problem?

Thank you

---

### Post by johnPB on 2012-03-08
Can you try to help me, this is very important.
Thanks

---

### Post by Splooshie123 on 2012-03-08
Run this in the terminal:
```
alsamixer
```
At the bottom of most bars, there should be 2 digits (like 00). If it says "MM", select it and press "M" on your keyboard. For some reason it may have been muted. That happened to me just yesterday, too.

If that doesn't work:
Are you using the generic kernel? I had no sound at all when I installed the realtime kernel.

---

