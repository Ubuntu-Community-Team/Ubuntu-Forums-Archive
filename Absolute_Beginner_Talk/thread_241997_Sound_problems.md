---
title: "Sound problems"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Phaeilo on 2006-08-23
Hello,
I installed Ubuntu and everything was working fine. Now I installed Xmms and I can use it using the alsa or oss plugin.
The problem is that I can't use two audio programms at the same time and the system sounds (startup/shutdown) aren't working anymore. Even the demo buttons in the audio settings gui aren't working. If I try to play a file with the esound plugin xmms just comes up with an error message that it can't access the sound card.
lspci comes up with this line for my sound card:
```
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```
It would be really great if someone can help me!

---

### Post by cocteau on 2006-08-23
As I understand it from my own experience.

When you start programs that uses sound, some will try to grab exclusice control of your sound card, thus making other programs unable to communicate with it. I know that XMMS is one of the offenders in this. One way to get around it is to install jack (or qjack for gui control) and route all programs who can communicate with jack through its server.

---

### Post by 3rdalbum on 2006-08-23
Have you tried forcibly routing XMMS through ESounD?

Do a ```
sudo apt-get install esound-clients
```.

In the menu editor, find the XMMS entry and add:

```
esddsp 
```

to the beginning of the command. This often has some success in routing such offensive programs' sound through ESD.

---

### Post by Phaeilo on 2006-08-23
Wow, thanks! It works for xmms!
Unfortunately the event sounds of Kopete and Evolution still aren't working.

---

