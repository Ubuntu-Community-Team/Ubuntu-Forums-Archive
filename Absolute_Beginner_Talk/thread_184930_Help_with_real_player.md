---
title: "Help with real player"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by newhen on 2006-05-30
Hi, I need help with real player I need help installing it I looked at the wiki guide but I dont really understand if anybody else could that make my day :mrgreen: One other question is there like a firefox thats fully loaded with this stuff on it already .


**ps probable gonna need to walk me through stemps I'm major noob:-k **



THANKS NEWHEN!!!

---

### Post by Jagot on 2006-05-30
Go to Applications, Accessories, then Terminal.

Now copy the following commnads into the terminal, pressing enter each time.

```
sudo apt-get install libstdc++5
```
```
wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb
```
```
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
```

Alternatively you could use Automatix which will do all the work for you:

[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by newhen on 2006-05-30
Thanks Much

---

