---
title: "small icons on desktop"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by big-hed on 2006-03-22
hi dudes, im a noobie to linux/ubuntu - have used it on and off for the past year or two.  But now ive actually got a fully working linux distro and its ....(no prizes for the right answer).

Well anyway - i dont know what i was doing but now me desktop icons when i log in are miniature.

Anybody know how to fix em????

Also had a prob last night when i was trying to update me system .. kept saying 
that sources was locked by some other program but i dont know how to kill that other program or what was causing my sources.list to get locked. ?????

sorry its a few probs all at once but i hope you guys can sort it - i know u can!

---

### Post by chuckyp on 2006-03-22
2)  I've seen this happen when you aren't using apt-get with sudo i.e. sudo apt-get install packagename.   It can also occur if you have the update manager installing stuff or synaptic open and you try a apt-get from terminal.

---

### Post by PhilOSparta on 2006-03-22
[QUOTE=big-hed]
Also had a prob last night when i was trying to update me system .. kept saying 
that sources was locked by some other program but i dont know how to kill that other program or what was causing my sources.list to get locked. ?????

[/QUOTE]
There may be other reasons, but the one that happens to me all the time is leaving "synaptic" running (usually minimized) and later running a terminal session of apt-get.   synaptic still has the sources.list file locked.

Edit:  If you are using Dapper, your icon problem may be a bug already submitted:
[https://launchpad.net/distros/ubuntu/+source/ubuntu-artwork/+bug/35439](https://launchpad.net/distros/ubuntu/+source/ubuntu-artwork/+bug/35439)

---

### Post by frodon on 2006-03-22
To set the icon size open nautilus (the GNOME file browser) and go to *peferences* there is a tab which allow you to set icon size.
You can't use both synaptic and "apt" or "dpkg" commands that's why you get this error message, so just close synaptic when you want to use "apt" or "dpkg" commands in terminal.

---

