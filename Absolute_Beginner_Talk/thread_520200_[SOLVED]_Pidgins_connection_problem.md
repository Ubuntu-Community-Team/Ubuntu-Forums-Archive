---
title: "[SOLVED] Pidgins connection problem"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-07
Hi all, i have a problem with connecting my pidgins when im using my college wireless, i don think it has been firewalled because if i switch to windows i can get windows messenger working

Thx! much appreciated!

---

### Post by FakeOutdoorsman on 2007-08-07
What error messages does Pidgin give you?  Do other programs in Ubuntu have trouble connecting?

---

### Post by kinngg on 2007-08-08
it jus says pidgins is unable to connect, all other programs has no problem. such as skype

---

### Post by FakeOutdoorsman on 2007-08-08
I'm guessing the college firewall is blocking the port Pidgin uses with MSN accounts.  Go to Accounts -> Add/Edit and select your MSN account.  Click the Advanced tab and check "Use HTTP Method".  This should go around your college firewall by using the same ports as HTTP traffic.

---

### Post by kinngg on 2007-08-08
i tried dat  but it stll doesn work.. is there any other way i can use pidgins in my college.. it seems like yahoo n msn messenger in windows wud work but dis wouldn

---

### Post by FakeOutdoorsman on 2007-08-08
Hmmm...perhaps return to Edit Account and change the port to 80 (although "Use HTTP" should do that behind the scenes I would guess).

Are you using the latest version of Pidgin (2.1.0)?  I believe as of a few months ago Pidgin was using an older version of the MSN protocol.  Maybe the newest version has updated this.

---

### Post by kinngg on 2007-08-08
changin port to 80 didn help.. its still da same..

---

### Post by FakeOutdoorsman on 2007-08-08
I think your Pidgin install may not have been complied with SSL support or you do not have the proper SSL libraries installed.  MSN and Google Talk require SSL to connect.  I should have thought of this earlier.  You can check if SSL is working by running "pidgin -d".  You will get an error like this if SSL is not working:
```
(12:32:29) connection: Calling serv_login
(12:32:29) server: pidgin 2.1.0 logging in xxx@xxx.com using MSN
(12:32:29) autorecon: hid error message while connecting (SSL support is needed for MSN. Please install a supported SSL library. See http://developer.pidgin.im/wiki/FAQssl for more information.)
```

1. Close Pidgin and try installing SSL libraries:
```
sudo aptitude install libnss-dev libgnutls10-dev
```

2. If it still fails to connect you need to uninstall and re-compile Pidgin with SSL support.  I can help you with that.

[Frequently Asked Questions About SSL and Pidgin]("http://developer.pidgin.im/wiki/FAQssl")

---

### Post by kinngg on 2007-08-08
oh thx! that helped me.. thx alot!

---

