---
title: "Linux DC++ does not properly connect"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-07-05
Hi,

I have read [http://ubuntuforums.org/showthread.php?t=76643](http://ubuntuforums.org/showthread.php?t=76643) and installed Linux DC++ succesfully. However, when I added a hub to my favorite hubs list it didn't show up. Therefore I also read the part of [http://ubuntuforums.org/showthread.php?t=28378](http://ubuntuforums.org/showthread.php?t=28378) about dependecies and I installed them. It worked!

But then another problem popped up. Once connected, I don't receive the message of the day, I can't seem to communicate with others, I can't connect to other users by trying to browse their files and it seems to take ages to get the user list of connected users!

Does anybody know what could be wrong?

---

### Post by bartkl on 2007-07-05
Also tried Passive mode, doesn't change a thing :(

---

### Post by bartkl on 2007-07-05
Okay, I downloaded the newest version and a lot of other libraries.
Now I can do the following:

Chat succesfully and when passive even search and connect to some users, but very little.

Anyone has a suggestion now?

---

### Post by bartkl on 2007-07-06
It seems people are able to download my filelist! Perhaps I should do something with Port triggering? I never understood what that was.

Please help :(. I'm getting closer and closer to the problem but I need help.

---

### Post by Ek0nomik on 2007-07-06
> **bartkl said:**
> It seems people are able to download my filelist! Perhaps I should do something with Port triggering? I never understood what that was.

Please help :(. I'm getting closer and closer to the problem but I need help.

Port Triggering is essentially opening up certain ports on your firewall.  If you are connected to a router, chances are it has a built in firewall.  What you need to do is specify certain ports within the router ([http://192.168.1.1](http://192.168.1.1)), and then specify those *same* ports in your software so it makes use of them.

For an example, if I was behind a firewall I would open port 52600 (just a random port # I made up) on my firewall, and then in DC++ port trigger 52600.  If the software allows, you can also specify a range of ports.  Ex: 52600-52610

---

