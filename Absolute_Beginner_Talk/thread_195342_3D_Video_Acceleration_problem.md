---
title: "3D Video Acceleration problem"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Andenium on 2006-06-12
ok so i followed the steps on 3D ATI Video Card Driver but it asks me to sudo dpkg-reconfigure xserver-xorg and it opens a blue screen asking me a bunch of stuf i dont know can somebody plz help me (im doing this cuz i did glxinfo | grep rendering to see if it was working fine [it isnt])


PS: if u think Instant messaging is easier my msn is [email]Andenium@hotmail.com[/email]

---

### Post by Andenium on 2006-06-12
any1 plz im desperaaate!!!

---

### Post by u.b.u.n.t.u on 2006-06-12
I got your PM and your question is easy to answer. I use Nvidia but I will post more of a reply to your question in a moment.

This is a forum and not a chat. So instant answers are not normally the situation. If you haven't got a reply within an hour for a common question or a day for a complex question then you can ask again.

But posting and within a few minutes posting again as you don't have an answer is too soon.

This is a very helpful community but it isn't instant.

I'll look for the ATI driver info for you now.

---

### Post by u.b.u.n.t.u on 2006-06-12
Here is an ATI driver guide.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

If you get stuck then ask again, detailing where you are stuck.


Edit:

Another ATI how to:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29)

---

### Post by drink on 2006-06-12
I am having the same problem - but I have a card not supported by fglrx, the ATI Rage Pro (Mobility M3) AGP2x 16MB. It's in an IBM Thinkpad A21p. I've tried to use drivers from the Linux DRI project, but they don't work, possibly in part because things are not in the traditional locations but more importantly because the driver built from them does not load. It's gotten really amazingly irritating.

How can I get DRI and MesaGL-hardware working with an ATI Rage Pro under Ubuntu Linux 6.06?

---

### Post by u.b.u.n.t.u on 2006-06-12
Drink, I think you need to post a new topic or your question may not be seen by enough people.

"How can I get DRI and MesaGL-hardware working with an ATI Rage Pro under Ubuntu Linux 6.06?"

That deserves a new post. Just a suggestion.

---

### Post by Andenium on 2006-06-13
Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

how do i enable the restricted repository in /etc/apt/sources.list

---

### Post by halfvolle melk on 2006-06-13
Here are two flavors of doing that:

[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Doesn't matter which you use, just pick the one you like.

Edit: after you're done, download [this file](http://www.ground-impact.com/libGL.so.1.2) to your Desktop. Then in a terminal, do this:
```
sudo cp ~/Desktop/libGL.so.1.2 /usr/lib/libGL.so.1.2
```

---

### Post by woopud on 2006-06-16
halfvolle melk ?
I like the 2% myself !

Bert

---

### Post by 3rdalbum on 2006-06-16
Andenium: If you don't know what a particular item in the xorg reconfigure program is/does, it's usually safe to just hit Enter. (except in the stage where you select the video card driver).

If you've backed up your old /etc/xorg.conf file, and know how to use the terminal if necessary to restore it, then it's doubly safe.

If you're still intimidated by the reconfigure program, then maybe you should try installing the driver later on when you have more experience?

---

