---
title: "Help Please"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-04-27
I am new to Ubuntu and I want to install Open song I found How would I do that?

---

### Post by ndefontenay on 2007-04-27
Hi.

First you should try to get a .deb file for this application If you got a deb file, do the following:

1) right click on the fil
2) Go to package management
3) Install package

From there it should work.

Or, if you got only source code, in the form of tar.gx, uncompress it into your home:
```

cd ~/[folder name] 
```
folder name would be where your app is located

```
sudo ./configure
sudo make
sudo make install
```

Or some application got a script to install automaticallyy, open the folder and look for something call install.sh or similar...

then go to the folder the same way as above and call sudo install.sh (or whatever it's called)

if you are new, the sudo command gives administrator's access. It will prompt for a user password which is the password you've entered when installing ubuntu.

If you got any problem installing, post the details here.

---

