---
title: "please help me!"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by rarick on 2006-02-06
well i installed ubuntu a few days ago, i have found that my pc is now a paperweight, a very expensive paperweitght, maybe because im new in this linux stuff, maybe because im dumb, but the point is a really need help with this, starting with: HOW THE HELL CAN I RESET THE ROOT PASSWORD, this issue is really making me crazy, second, how the hell can i install the drivers of all the stuff in the OS.  

please someone, help me, or at least, is there something on the internet like: the ultimate guide to linux or how to unmake your pc a paperweight?

again, please i really need help with this ubuntu stuff

thanks in advance.

//rarick

---

### Post by Qrk on 2006-02-06
Ubuntu doesn't have a root password. We use sudo; which for the end user makes the root password in effect the user password. 

When the system prompts you for your "root" password, it is really asking for your user password. If you want to change that password, you can open a terminal and type:

```
sudo pasword *username*
```

and type in your old password, then your new one twice.

Please read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for a longer explaination.

As for drivers, it depends on what they are for. Are these 3d drivers for you graphics card, or windows drivers for wireless? or something else?

---

### Post by rarick on 2006-02-06
when i open the sistem administrator or something, it says you canot change this settings cause' you're not the root, so i was wondering is tehre is a way to go start the sesion as root, like in debian, the drivers i mean, the monitor's driver (yes it has one) the Nvidia Geforce Fx5200 the mouse and keyboard drivers, and the tvcapture card (but i think this one will be almost imposible)

---

### Post by Qrk on 2006-02-06
The way to log in as root is shown on the wikipage. But it is not advised. 

I don't understand your problem; though. Does the system prompt you for a password when you use the administration features? If so you just enter your user password. If not, then either I still don't understand your question or we have bigger problems.

You can run any command as root by just placing "sudo" before it. (well, just about, the wikipage explains it more)

---

### Post by rarick on 2006-02-06
it doesn't ask, just says, in big red, you canot change this settings unless your re the root, however, how can i install those Nvidia drivers, and the like?

---

### Post by Qrk on 2006-02-06
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by rarick on 2006-02-06
yeah i was readding that, thx a lot!! but the monitor's and the tv caption card? it's not Nvidia, and surely it's not from a know brand, so..... I am.... F****

---

### Post by rarick on 2006-02-06
allritght, looks like the wiki stuff is really good, now the question is... is thre any way to install a driver from a cd? or that drivers in cd stuff is obsolete in linux?

---

