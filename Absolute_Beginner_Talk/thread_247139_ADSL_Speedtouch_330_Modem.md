---
title: "ADSL Speedtouch 330 Modem"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by spaarks on 2006-08-30
I have read the "speedtouch howto" guide. It is well beyond my skills.  Is there no easier way to configute my modem?

Modem is a USB Speedtouch 330, no router. ISP is Tesco UK.  I have no problem in connecting in Win XP.
I am booting Ubunto on CD.

---

### Post by bruce89 on 2006-08-30
I assume you mean this - [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
I used it, and it was fine.  Ubuntu has to be installed to disk though to make this work, otherwise it just won't work at all, as you have to reboot in it.

---

### Post by spaarks on 2006-08-30
Thanks for the info.  But I want to run Ubuntu from CD.
The modem works fine under WinxP.

---

### Post by Edgar on 2006-09-03
Hey, I'm following this guide [https://help.ubuntu.com/community/Us...dem/SpeedTouch](https://help.ubuntu.com/community/Us...dem/SpeedTouch) and it was all going quite nicely till I got to the part where I had to copy the secrets.txt to /etc/ppp.

The tutorial says that to do so I should type in the following:

sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets

So I typed in:

edgar@P42GHZ:~$ cd speedtouch
edgar@P42GHZ:~/speedtouch$ sudo install -m 600 secrets /etc/ppp/chap-secrets &&
> sudo install -m 600 secrets /etc/ppp/pap-secrets
install: cannot stat `secrets': No such file or directory

I also tryed copying the file from my home folder but I got the same 'install: cannot stat `secrets': No such file or directory'
message.

What do I do?

---

