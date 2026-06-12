---
title: "No network but Internet works??"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by ThePolemistis on 2007-05-14
HI,

I am new to the linux community,

I was recently using ubuntu 5.10 until now where i have installed ubuntu 7.04

Initially, the internet was not working, and no network was available.
I did the following commands in the terminal:

sudo ifdown eth0
sudo ifup etho0

and my internet works...
However, I get no network connection in the top right hand corner still displayed.

How come it is not updated ??

---

### Post by tgm4883 on 2007-05-14
I'm not totally sure, but i think i read this somewhere. It is because by issueing that command, you bypassed the network manager.

---

### Post by jfinkels on 2007-05-14
> **tgm4883 said:**
> I'm not totally sure, but i think i read this somewhere. It is because by issueing that command, you bypassed the network manager.

I believe that's true also. I have done something similar in the past. I just don't use the GNOME Network Manager at all :P

---

### Post by ThePolemistis on 2007-05-14
> **jfinkels said:**
> I believe that's true also. I have done something similar in the past. I just don't use the GNOME Network Manager at all :P
Fixed it

Had to click on the icon, and click wired for it to work...
I mean it was working before but not proper icon, everything else was working...

I guess this is probably a (little) bug then :P

---

