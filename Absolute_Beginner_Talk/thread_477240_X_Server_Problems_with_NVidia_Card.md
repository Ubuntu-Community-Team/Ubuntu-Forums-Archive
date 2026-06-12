---
title: "X Server Problems with NVidia Card"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by hornypiano on 2007-06-18
Hi

I have just installed Feisty Fawn using a disc sent from Ubuntu. It installed fine but after turning the computer off for the first time it would not switch back on properly. I keep getting a message saying there is a problem with X server and my graphics card and more that I don't understand.

Please someone help me - what do I need to do to correct this? Please can you be specific with any commands that may need typing as I am new to Ubuntu. Any help is greatly appreciated.

Mick

:confused:

---

### Post by Crafty Kisses on 2007-06-18
> **hornypiano said:**
> Hi

I have just installed Feisty Fawn using a disc sent from Ubuntu. It installed fine but after turning the computer off for the first time it would not switch back on properly. I keep getting a message saying there is a problem with X server and my graphics card and more that I don't understand.

Please someone help me - what do I need to do to correct this? Please can you be specific with any commands that may need typing as I am new to Ubuntu. Any help is greatly appreciated.

Mick

:confused:

You can try reconfiguring your X server, try the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

