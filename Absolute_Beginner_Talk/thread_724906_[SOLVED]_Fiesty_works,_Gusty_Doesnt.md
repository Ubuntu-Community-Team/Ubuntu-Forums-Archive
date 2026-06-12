---
title: "[SOLVED] Fiesty works, Gusty Doesnt"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-15
I downloaded Gusty about 5 days ago, and I couldnt make it go online, I tried everything, I changed network manager, did things manually and NOTHING worked...
so yesterday I downloaded fiesty and now I can go online automatically!
I have few questions:
1) Why is this happening? Should I file a bug report in gusty? if yes, how?
2) Does fiesty have compiz-fusion installed?
3) The first time i logged in i got the attached image, but i can go online through wireless... does it mean anything?

---

### Post by Gyzome on 2008-03-15
Try disabling IPv6. It worked with me.
At a Terminal type: ```
sudo gedit /etc/modprobe.d/aliases
```
and replace "alias net-pf-10 ipv6" with "#alias net-pf-10 ipv6"
and insert a line with "alias net-pf-10 off"
That's it,

Good luck

---

### Post by ugm6hr on 2008-03-15
@perito:
Please do not repost the same problem in multiple threads.

Have you managed to connect to your router yet?

As mentioned previously, it may well be an ipv6 issue.

---

### Post by perito on 2008-03-16
OMG, I cant believe this, the problem was ipv6 !!!!!
you know I gave up on gusty and installed fiesty and all it was was adding a # !!!!!!!
thx alot guys

---

### Post by ugm6hr on 2008-03-16
No worries.

Glad it works.

Please mark your threads as solved.

---

### Post by DarinB on 2008-03-16
don't forget to thank the person that improved the quality of your life

---

