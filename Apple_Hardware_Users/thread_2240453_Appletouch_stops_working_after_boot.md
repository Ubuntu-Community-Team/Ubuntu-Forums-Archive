---
title: "Appletouch stops working after boot"
date: 2014-08-20
forum: Apple Hardware Users
---

### Post by peyu on 2014-08-20
Hi,
I've installed Xubuntu 14.04 on my macbook 2,1 in April when it was released, and everything was working fine. But since a few weeks, The touchpad pointer start to freeze after entering session in xubuntu (between 30 seconds to some minutes after opening session, randomly). 
To make it work again, I switch to tty1 and I execute:
```
sudo rmmod appletouch
sudo modprobe appletouch

```
And then it works perfectly (I never had to do it twice).

Do you know if there is some kind of log from appletouch driver ? I checked kernel.log but i didn't see anything.
Am I the only one with this problem ? Any suggestions for an easier workaround ?
Thanks !

---

