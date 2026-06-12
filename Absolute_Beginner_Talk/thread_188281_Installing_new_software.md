---
title: "Installing new software"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Slenkar on 2006-06-03
Hi I cant get online with Ubuntu because my service provider doesnt have a version of their software for linux, 
so I can download linux programs onto a memory stick and get them onto the linux desktop...
but then Im completely stumped on how to install them and I dont know how to get the command line,
I want to install Peng,wings3d and blender
thanks

---

### Post by bluevoodoo1 on 2006-06-03
See if this helps you...
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by meng on 2006-06-03
Ugh, installing without an internet connection, not usually a fun activity (considering dependencies). Although the link may be helpful, may I ask which internet service provider you have? (just in case anyone knows how to connect to them through Linux regardless)

---

### Post by Slenkar on 2006-06-03
someone got me an aol account, lame i know.
i cant install pengaol without the right knowledge though

---

### Post by RRS on 2006-06-03
You shouldn't need special software to to connect, if the account is active your screename and password should be sufficient ( and a phone # for dial-up).

You might want to search the forums under networking for assistance. My own knowledge is limited and I might set you on the wrong track.

In the meantime if you're dual-booting with windows you can download deb. packages to a folder in windows and then reboot into Ubuntu and copy them for installation.

Just finished signing in to AOL using my sbcyahoo dsl connection. Did have to reactivate an old screenname since I haven't had an active account for almost a year but I had no connection issues and all they wanted was to set a couple cookies, no software requirements.

Also to access windows files (read only, no write) follow [these directions]("http://psychocats.net/ubuntu/mountwindows.php").

Edit; more info.

---

### Post by aysiu on 2006-06-03
I have no experience with AOL, but you can try downloading [this file](http://archive.ubuntu.com/ubuntu/pool/universe/p/penggy/penggy_0.2.1-13_i386.deb), copying it to your Ubuntu desktop and then typing this command in the terminal ```
cd ~/Desktop
sudo dpkg -i penggy_0.2.1-13_i386.deb
```

---

### Post by meng on 2006-06-03
Yes I was reading that some folks have had problems with pengaol and prefer penggy. At least trying penggy first is easier to "undo" if it doesn't work out for you.

---

