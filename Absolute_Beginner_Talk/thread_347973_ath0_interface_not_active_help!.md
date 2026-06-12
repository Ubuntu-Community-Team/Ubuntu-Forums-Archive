---
title: "ath0 interface not active help!"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by pak33m on 2007-01-28
Hello there,

I've just finished a dist upgrade from Dapper -> Edgy through the alternate CD.  

I installed ndiswrapper with the windows driver  & verified through the ndiswrapper -l command.   Then I installed Network-Manager.  This in the same way I did it for my Dapper install & an Xubuntu install, too.  I got connected both times using the same card that I have inserted for my Edgy install. 

I made sure that I cleared the /etc/network/interfaces file for any interfaces listed other than lo.  I tried to bring up the ath0 interface with the sudo ifup ath0 command, but I always get output stating that the interface is not configured or no such device.

If ndiswrapper & the windows driver installed correctly why can't I bring up the ath0 interface.  This after I have followed the wifi docs on the wiki & searched everywhere.

I finally have an Ethernet connection at he moment & will be updating the software.  Maybe there are some files related to ndiswrapper that need updating?

I just don't want to have a bad experience with wireless because I haven't so far.

---

### Post by slybob on 2007-01-28
when I was trying to get wireless working on my xubuntu dapper I saw a lot of posts and bugs with edgy wireless. 

can you do 

```
sudo iwconfig
```

post the output here?

Cheers

---

