---
title: "Damn stupid newbie question"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2005-12-16
This is kind of unbelivable...

in widows i usualy typed **ipconfig** to check my ip.

What's the unix command for ip checking?

---

### Post by fog on 2005-12-16
i**[COLOR="DarkOrchid"]f[/COLOR]**config

---

### Post by pedrotuga on 2005-12-16
loolll
damn P!
ehehehe
i was right... it's unbelivable, one letter! eheheh

Thx fog.
this forum is cool :cool: :cool: :cool:

---

### Post by pedrotuga on 2005-12-16
Another related question that just came up to my mind.

How can i see the computers in my network using text mode?

---

### Post by fog on 2005-12-16
Take a look [[COLOR="Red"]here[/COLOR]]("http://rak.isternet.sk/linux-netman/commands.html")

---

### Post by pedrotuga on 2005-12-16
Kind of cool... not so much detailed information but it tells a bit about some network commands, wich is very cool for  begginer
thx

---

### Post by souki on 2005-12-16
you can try to ping the broadcast address, let's say you're on the 192.168.0.0 private network, the broadcast address would be 192.168.0.255 and the ping command:
```
ping -b 192.168.0.255
```
if you want to find the windows machines, try with the smbtree command

---

### Post by patrick295767 on 2005-12-16
[QUOTE=pedrotuga]Another related question that just came up to my mind.

How can i see the computers in my network using text mode?[/QUOTE]

did you try nautilus or the kde file manager stuff ? it should be possible with it.

---

### Post by pedrotuga on 2005-12-16
[QUOTE=patrick295767]did you try nautilus or the kde file manager stuff ? it should be possible with it.[/QUOTE]
It has to be in text mode due to being remote access sometimes

---

### Post by Jakykong on 2005-12-16
[QUOTE=pedrotuga]It has to be in text mode due to being remote access sometimes[/QUOTE]

Um ... well i know that there is a technology called "VNC" (i'm trying to set up in another thread) to let another compter see and interact with your desktop ... 

i don't know exactly how to use it (working on it) but there isn't any reason i can see that you couldn't have graphical remote access... X11 was designed with network transparency (check wikipedia if you wanna know more :-P)

---

