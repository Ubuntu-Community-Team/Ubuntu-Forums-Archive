---
title: "Proper way to start / stop xinetd"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by tcdmail on 2007-06-25
I've installed Ubuntu Server 7.0.4 and followed the instuctions for installing cvs from the server guide.
The guide mentions the use of XINETD to control the CVS service

My question what is the proper way for stopping the CVS Service in XINETD. E.g for backup purposes. Is it by changing the parameter "disable" in cvspserver (service declaration fileà or is there another/better way.

As i see it now i should do the following.

1. Copy and replace cvspserver file with disable=yes
2. sudo /etc/init.d/xinetd restart
3. Execute eg backup
4. Copy and replace cvspserver file with disable=no
5. sudo /etc/init.d/xinetd restart

Tnx for any advice on how to do this properly

Kind regards,
t.

---

