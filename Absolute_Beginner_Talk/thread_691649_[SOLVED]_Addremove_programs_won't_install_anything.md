---
title: "[SOLVED] Add/remove programs won't install anything."
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-02-08
Every time I attempt to install anything this is the message I get.

"The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection."

I'm currently on my friend's PC, who is also running Gutsy Gibbon.


Help please!

---

### Post by emarkd on 2008-02-08
Well, it's correct :)  Synaptic downloads software to install from the online repositories.  If you don't have a working internet connection, it can't even check to see what's there.

So do you have a working internet connection?  If not, what sort of hardware do you have?  Maybe we can help you get it going.

---

### Post by nynoah on 2008-02-08
sounds like your net connection is not working.  Check and see if it is.

---

### Post by Presto123 on 2008-02-08
Go into your Software Sources applet in System/Administration menu and make sure that all of your  "Downloadable from the Internet" boxes are checked. I don't have "Source Code" checked, myself.

---

### Post by macogw on 2008-02-08
Is the computer online?  Is there a proxy or anything in the way?

What's the output of ```
cat /etc/apt/sources.list
```?
If the lines that start with "deb" have a # in front of them, remove the #s that are commenting out the deb lines ```
gksu gedit /etc/apt/sources.list
```
then ```
sudo apt-get update
``` will do the same thing as "Reload" except it'll give you more info if it fails.

---

### Post by ladybumavere on 2008-02-08
hahaha everyone is posting about the internet connection but I'm posting from the computer.

:-P

I figured it out from another post.

Had to go to System > Software Sources and turn on all those things and that got it going.


Thanks!

---

### Post by Presto123 on 2008-02-08
> **Presto123 said:**
> Go into your Software Sources applet in System/Administration menu and make sure that all of your  "Downloadable from the Internet" boxes are checked. I don't have "Source Code" checked, myself.

Mmmhmmm...:lolflag:

---

### Post by drunkardivan on 2008-02-16
> **Presto123 said:**
> Go into your Software Sources applet in System/Administration menu and make sure that all of your  "Downloadable from the Internet" boxes are checked.

Thanks. Solved my problem without me making a new post. See, some newbs can use the search box! :lolflag:

---

