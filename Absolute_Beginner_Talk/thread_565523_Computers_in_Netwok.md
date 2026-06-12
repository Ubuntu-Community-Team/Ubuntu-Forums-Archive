---
title: "Computers in Netwok"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by fjoeng on 2007-10-02
Hi there,

An introduction here to all Ubuntu users and developers :D. I am a new user of Ubuntu, I got to know about this from a friend of mine so I decided to give it a try. Installation and system setup, nothing wrong with it, all went smoothly. I did some clickings here and there to get myself familiar and walla it's just simple as the one I used previously :D.

But not till the networking part, in the network I installed 2 Ubuntu with 1 Windows XP Pro. I could see the PC running on Windows but can't see the one running in Ubuntu? Could you guys help me on that?

And 1 more question, I installed 1 PC with CD-ROM attached and installation completed succesfully, I removed the CD-ROM attached it with another PC to be installed. When I boot up the PC with CD-ROM removed it just won't start until I plugged-in back? Why is that?

Hope you guys could help on those problems I faced :D. Thanks for the support guys.

---

### Post by hyper_ch on 2007-10-02
Well, networking can be made through samba or - what I prefer - through ssh...

SSH would be as simple as to install
```

sudo apt-get install openssh-server

```
and then fetch a scp client for windows ([http://www.winscp.com](http://www.winscp.com)) and you can connect to your ubuntu machine. Just use the ubuntu username and password for logging in (it's sort like ftp but encrypted).

Setting up Samba can be a bit more challenging but there are quite a few howtos here. Have a search for it and I'm sure you'll find what you need.

---

