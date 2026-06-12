---
title: "Weird Networking Problems"
date: 2006-06-14
forum: Apple PPC Users
---

### Post by jakestah7 on 2006-06-14
-on old imac with breezy-

I have three computers, two pc's(laptop&desktop) and the old imac hooked to  a wireless g game adapter in kitchen. The desktop pc has a lot of data that I use and shares a lot of folders with laptop. When I try to look at the folders, there are some that don't show up and most that show up ask me for authorization. Why would I need authorization when the laptop doesn't and I don't know what to put in for auth; I tried things that didn't work. I can find the missing ones if I type there path but there are is nothing in it and it has a little lock emblem. What do I have to do do make all this stuff work for the imac. Also I have the same user name for the desktop and laptop which is jake and the hostname or what ever for imac is imac and the desktop's is jake (confusing) I don't know if this affects the computers. Could anyone tell me what is wrong with this.

---

### Post by bmckee on 2006-06-15
It's hard to help too much with the information you've provided.  When posting questions like this, post OS information for everything involved, it makes a big difference....

Here's how to start straightening things out....

   I'm _guessing_ you are using Samba/CIFS with a mixed crowd of Macs, Windows boxes and Linux boxes.

1 -    Are they all on the same subnet?  Can you ping all of the other boxes from all of the boxes?

2 -    Are the firewalls on all the boxes set to allow Windows File Sharing through?

3 -    Are they all set to the same workgroup?

4 -    Do they all have distinctive host names?

Start there...  then post specific cases of something that doesn't work with all the relevant info included...

HTH get you started

---

