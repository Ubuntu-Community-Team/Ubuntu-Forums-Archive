---
title: "Connecting with an ethnernet cable."
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by PleaseEnjoyThis on 2007-04-23
I am having trouble connection to the internet with an Ethernet cable. With windows there was no configuring needed, it just is automatically connected to the the internet, but with Linux its a different story.  Can anyone help me out?  It would be most appreciated.

---

### Post by devnulljp on 2007-04-23
Are you using a router? Sounds like you're using dhcp, so it should also work the same way in linux.
can you try this (on the command line) 

sudo ifconfig eth0

And see what it says. My suspicion is you're not getting the right gateway info.
Also, can you post the contents of 
/etc/network/interfaces

---

### Post by PleaseEnjoyThis on 2007-04-23
Yes I am using a router.  I'm going to switch over to Linux know and try that stuff out, THANKS!

---

### Post by PleaseEnjoyThis on 2007-04-23
I'm on linux and online!  It was just some stupid error I did, thanks anyways though!

---

### Post by jackmc on 2007-04-23
glad you got it sorted, it took me a while to get mine going too :)

---

