---
title: "Macbook pro 4.1 no wireless problem"
date: 2010-05-22
forum: Apple Hardware Users
---

### Post by unagimiyagi on 2010-05-22
Hi, I just installed 10.04 lucid lynx and I don't have any wireless networks.  My broadcom card is not being detected . I have tried to go to Administration -> hardware drivers and nothing shows up. It says I have no proprietary drivers.  Do I need to connect to the internet before I can download these?  It seems circular?  Is there a driver that I can download and install the old-fashioned way?  I have a macbook pro 4.1, the early 2008 Penryn model. The wiki states that wireless should work easily, yet I'm not sure what's going on.  No wireless is a showstopper currently for me.

Can someone help?

Thanks

---

### Post by linuxopjemac on 2010-05-24
Normally the easiest to do is to hook it up to internet via a cable, then update the repository and upgrade and then to do your trick

```
sudo apt-get update
sudo apt-get upgrade
```

---

