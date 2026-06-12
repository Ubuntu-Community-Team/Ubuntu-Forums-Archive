---
title: "Getting modem to work..."
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by sharong on 2007-03-26
I'm trying to connect my Ubuntu laptop to the internet.  I've tried configuring the winmodem, but it all got too technical and I gave up.  Now I have a Zoom external serial modem which says on the box that it works with Linux.  I've followed all the directions I can find to get it set up, but the computer doesn't even seem to recognise that it's there.
I might have broken something during the winmodem attempts - is that possible?  Otherwise, how can I tell that the computer even knows the modem is there?
Once it has found it, how do I configure it? And then how do I get it to dial up?  Is it like Windows, where I just open Firefox or something that needs an internet connection?
I'm also confused about ethernet vs ppp connections - what are they and which do I use?
And what's all the stuff about 'Dapper' and 'Hoary' in relation to ubuntu?  How do I know what I'm using?  The modem help pages seem to refer to these as if they're crucially important.
Any help would be much appreciated!

---

### Post by Bachstelze on 2007-03-26
Make sure the modem is powered on and connected to the computer, open a terminal, run 

```
sudo wvdialconf /etc/wvdial.conf
```

and paste what you get.

---

### Post by seshomaru samma on 2007-03-26
To know which edition of Ubuntu you are running , paste this into a terminal:
```
lsb_release -a
```

---

### Post by sharong on 2007-04-16
Thanks, got it to work in the end....:D

---

