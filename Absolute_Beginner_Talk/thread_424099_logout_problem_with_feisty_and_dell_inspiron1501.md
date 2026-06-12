---
title: "logout problem with feisty and dell inspiron1501"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by purpleleave on 2007-04-26
I successfully install feisty on my dell inspiron 1501; 
but when I logout or switch from session, the screen just go dark,
and the machine just sleep so well that I can't wake it up in no means.
I must press the shutdown key and again to restart.
What's wrong with that?

btw, inspiron1501 with edgy just working well when logout.

---

### Post by AaronMT on 2007-04-26
Hello,

I have the same laptop, I resolved this problem very recently by performing the following.

I went to 

[list][*]System
[*]Administration
[*]Login Window
[/list]

and placed a checkmark in **Restart the Xserver with each login**

I applied and rebooted the machine and tested it an it fixed it for me.

Let me know how it goes.

- AaronMT

---

### Post by purpleleave on 2007-04-26
I never expected I can get the answer so soon.
Thank you very much, 
It works !

---

### Post by 787b on 2007-05-07
Unfortunately, this doesn't work for me on Kubuntu. There is no option to restart X after every logout. Any ideas? 

Thanks.
 -b

---

### Post by gigabz666 on 2007-05-15
I'm having the same problem using Kubuntu,

---

