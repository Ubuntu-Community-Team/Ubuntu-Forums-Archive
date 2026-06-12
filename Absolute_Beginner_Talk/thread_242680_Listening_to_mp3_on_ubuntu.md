---
title: "Listening to mp3 on ubuntu"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Alpha Monkey on 2006-08-24
Ok, i've read through a few posts and such and such and found a bunch of links to different decoders, programs and all that but not a singel thing tells me how to install it. im working on a dual boot ubuntu, XP computer at school and my I.T. teacher wants me to make it mp3s compatitable on ubuntu i need a complete run down on how it is done and what to use. easyubuntu wont work because of our net provider blocking certain things and making it impossible for the easyubuntu setup to get past a certain point. any help is much appreciated

---

### Post by Amablue on 2006-08-24
Have you tried Automatix?
```

wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```

---

### Post by Jagot on 2006-08-24
Enable the universe reporitory using either of these methods:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then launch a terminal window and copy and paste these lines to it and press enter:

```
sudo aptitude update && sudo aptitude install gstreamer0.10-plugins-ugly
```

---

### Post by PietreWitobi on 2006-08-24
Hey, I'm a new user too, I just wound up installing xmms...

I'm on Dapper Drake, and it's my first Linux OS, so I have no Idea how to do this on any of the other releases, but I did....

Applications>>Add/Remove...

Once that has started (took me a minute):
In the lift window select "Sound & Video"
In the Upper Right Window scroll all the way down and check the box next to "XMMS Music Player"
Finally, click "Apply" in the lower right.

To run after installation, 

Applications>>Sound & Video>>XMMS Music Player

It'll play MP3s, but there isn't much of any sort of library feature.  Currently looking for a way to remedy that ~We'll see~

Hey, Jagot, I tried the steps you detailed, I'm pretty sure I have the universe repository enabled, but when I entered your code, I encountered two error messages:

[INDENT]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/INDENT]

Any insight onto what the heck that means or how to fix it?

---

### Post by Alpha Monkey on 2006-08-24
Cheers for the help guys, that last one looked like it was gonna work, i get a 407 proxy authentication required message all the time so i think its either our server or internet provided because they block alot of stuff. thanks anyway

---

### Post by Catewilliams on 2006-08-24
XMMS works amazingly for me, It seems like someone here already directed you to that. But you can also download google and download easyubuntu, and there seems to be a plug-in that lets Totem play MP3s.

---

