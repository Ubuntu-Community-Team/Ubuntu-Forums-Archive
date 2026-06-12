---
title: "Wireless for Ubuntu 8.04 on 2 Gen macbook"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by iAppleuser on 2008-04-25
Does anyone know how to fix this? My macbook is a C2D.

---

### Post by jdriessen on 2008-04-25
I have a macbook2,1 and ubuntu 8.04 doesn't recognize my Wireless Card.

---

### Post by cyberdork33 on 2008-04-25
Follow the wiki:
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

---

### Post by jdriessen on 2008-04-26
I could not get the latest svn of Madwifi drivers to work, instead I used the svn of Madwifi Macbook:

svn checkout [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) macbook

I installed this version and my wireless is now working.

---

### Post by piano08man on 2008-04-26
I've tried doing this several times and I am admittedly very limited when it comes to terminal commands.  Is there some way that one of you more experienced people could take the daily snapshots or the svn version of the wireless walkthrough from the link and make it more dumb people friendly?  For example: tell me where, what and when to type.  Every time I get to the last couple lines of code it produces errors and tells me that no such directory exists.  I can give more info, but maybe just a little more in depth walkthrough would be helpful.  Thanks!  Plus, I'm assuming that the Gutsy walkthrough still works for Hardy?

Josh

---

### Post by iAppleuser on 2008-04-26
I figured out my problem about the wireless! Thank you everyone! I used the macbook guide to get my wireless going!

---

### Post by cyberdork33 on 2008-04-26
> **piano08man said:**
> I've tried doing this several times and I am admittedly very limited when it comes to terminal commands.  Is there some way that one of you more experienced people could take the daily snapshots or the svn version of the wireless walkthrough from the link and make it more dumb people friendly?  For example: tell me where, what and when to type.  Every time I get to the last couple lines of code it produces errors and tells me that no such directory exists.  I can give more info, but maybe just a little more in depth walkthrough would be helpful.  Thanks!  Plus, I'm assuming that the Gutsy walkthrough still works for Hardy?

Josh
you need to post your error so we can tell you what the problem is. That guide is step by step, so it doesn't get much easier.

---

