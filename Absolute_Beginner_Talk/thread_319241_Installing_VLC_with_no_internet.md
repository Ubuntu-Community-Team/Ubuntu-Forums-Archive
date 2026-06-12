---
title: "Installing VLC with no internet"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by jbayone on 2006-12-15
I have no internet connection at home and have been semi-successfully installing programs by running a virtual machine at work, then burning the .deb files to a CD, then going back home and installing them.  The only problem I have is with VLC.  When I try to install it, I get a message saying that a dependency is not satisfied:  WXVLC; but when I try to install that, I get another message saying dependency not satisfied:  VLC.  It's a catch-22 or maybe I'm just missing something here.

---

### Post by qamelian on 2006-12-15
If you have them both in the same folder you should be able to:```
sudo dpkg -i vlc wxvlc
```to resolve the circular dependancy.

---

### Post by jbayone on 2006-12-15
Thanks, I'll try that once I get home.

---

### Post by deadgobby on 2006-12-15
OK I been searching for a while to find a off line CD you can do at work and take home with you. There seems to be people with the same voice asking for extra CD for people with no internet.
[https://wiki.ubuntu.com/APTonCD?highlight=%28cd%29](https://wiki.ubuntu.com/APTonCD?highlight=%28cd%29)
  I hope this helps.
Gobby

---

### Post by gblob331 on 2006-12-15
You could use the Ubuntu Bounty Source Dapper Addon CD which has VLC in it. The CD installs other useful programs too.

For a list of progs:
[http://ubuntuforums.org/showthread.php?t=183933&page=7](http://ubuntuforums.org/showthread.php?t=183933&page=7)

---

### Post by jbayone on 2006-12-15
I've burned the Ubuntu Plus .iso so I'll see how that works out.  I'm waiting for the virtual machine torrent for Ubuntu to finish so I can use APTonCD.  Thanks though guys.

---

