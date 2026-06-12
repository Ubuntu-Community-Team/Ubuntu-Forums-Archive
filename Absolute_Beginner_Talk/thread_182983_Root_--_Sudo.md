---
title: "Root -- Sudo???"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Michiba on 2006-05-27
Hi guys,

Question : How do I log on as root. During installation I don't recall being asked for a root password. I can do every thing with Sudo and my user password but thought one day I may just need to log on as root. 

I understand we don't need to root all the time but occasionally is nice.

Michiba

---

### Post by Koech on 2006-05-27
Check [this]("http://ubuntuguide.org/#usersadministration") out.

---

### Post by Sendervictorius on 2006-05-27
The idea is that there is no root in ubuntu. Sure, you can create a root login if you really must, but sudo is much better, and more secure. 

There has been a lot of discussion about this on the forum. It trips up a lot of people new to Ubuntu - from a windows or other Linux distros - but not, I am told, from a Mac OSX background. People are often wedded to the idea of having a root lolgin, and find it a hard habit to break.

Try using sudo for a bit, and you may come to realise, you don't need root.

If you want to run a number of root commands for a while, try sudo su , or sudo gnome-terminal

---

### Post by mlind on 2006-05-27
There's very good wiki entry about this too
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Michiba on 2006-05-27
Thanks Guys,

I'm ok with the concept, ignorance is my problem, forums are curing me of that.

Michiba

---

### Post by PingunZ on 2006-05-27
In console / or Konsole type :
```
sudo -s -H
Password: <specify user password>
```

---

### Post by Perfect Storm on 2006-05-27
Make a launcher and add this command to it:
```
gksu /usr/bin/x-terminal-emulator
```

It's very handy if you gonna modify something in longer period (but also dangerous).

---

