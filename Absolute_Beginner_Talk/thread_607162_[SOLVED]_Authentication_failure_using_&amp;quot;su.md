---
title: "[SOLVED] Authentication failure using &amp;quot;su&amp;quot; command"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-11-08
I keep on getting an authentication failure when I try to use the "su" command to switch to root. I have had this problem every since I got Ubuntu and I was wondering how to solve it. The reason why I ask is because I am trying to install the Linux drivers for a Wacom tablet based on the Linux Wacom tablet documentation, which requires me to switch to root to make system changes based on the 2.6 kernel of Linux. Any advice?

---

### Post by bodhi.zazen on 2007-11-08
Ubuntu uses sudo :

	[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

To become root :

```
sudo -i
```

---

### Post by mcduck on 2007-11-08
Your problem is that the root account is disabled, but 'su' asks for root password, not your own like 'sudo' does.

The solution is simple, use 'sudo -i' instead of 'su'. :)

---

### Post by sisco311 on 2007-11-08
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
```
sudo su
```

---

### Post by ShadowMKII on 2007-11-08
Alright then! Well that answered my question! I usually always use sudo, but I have never really had to use sudo -i. Thanks a lot!

---

### Post by Dr Small on 2007-11-08
Please remember to mark your threads as Solved from Thread Tools.
Thanks :)

---

### Post by ShadowMKII on 2007-11-08
Sorry, I forgot - thanks for the reminder though!

---

