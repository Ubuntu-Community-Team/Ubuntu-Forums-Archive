---
title: "Installing Openkiosk"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by david_kt on 2007-01-20
It has been quite sometimes I am playing around with this software:

[http://openkiosk.sourceforge.net/](http://openkiosk.sourceforge.net/)

Below is some writing for older version which help me to understand the problem with this software:
[http://www.opensubscriber.com/message/ubuntu-users@lists.ubuntu.com/1956690.html](http://www.opensubscriber.com/message/ubuntu-users@lists.ubuntu.com/1956690.html)

Most of the issue above has been corrected, except it still could not detect QT installation. To solve that problem, please do:

      export QTDIR=/usr

on the terminal before executing 

      ./configure --prefix=/usr

I have manage to install both nodeview and the client, but there is still problem in the nodeview. The problem is additional operators could not login complaining wrong password. So, I could only login using Administrator.

I even try using the rpm package (using sudo alien) but the installation fail. The rpm package I downloaded from mandriva. May be I will try to use mandriva as the server as I could not install it perfectly in ubuntu, and using kubuntu as client. But it is better if I could install nodeview in ubuntu perfectly.


Maybe any of you have some experience installing this software? 

Regards,
DK

---

