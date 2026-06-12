---
title: "no workgroup computer running linux on my home network ???"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by verby on 2006-11-01
I'm having ms network running at home. 3 pc's. 1 of them runs ubuntu. the thing is that i can browse shared folders from ubuntu, BUT can't browse shared folder running on ubuntu (from win). i have set up one shared folder on desktop and nothing. what am i missing?

---

### Post by verby on 2006-11-01
anyone???

---

### Post by RudolfMDLT on 2006-11-01
Hi there!

I'll try and help... :)

Please post back with the following info:

1) Your network architecture, ie, are you using a router? DHCP?

2) On the Ubuntu machine, in the terminal:
> ifconfig


> smbtree

3) Have you added the windows users to to your samba server?
If you don't what i'm talking about:


i) "sudo smbpasswd -e yourname" (you're user name)
ii)Type and retype new Samba password
iii)"sudo smbpasswd -a XP windowsusername" (kitchenpc)
    (the usernames of your network users)
iv)Type and retype their passwords

4) Are you running a firewall? If so switch it off and try again.


I'll check back later and see if you got sorted! :)

Cheers,

Rudolf

---

