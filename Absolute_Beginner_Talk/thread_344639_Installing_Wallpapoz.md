---
title: "Installing Wallpapoz"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2007-01-23
I am really bad at installing stuff and was wondering if someone could help me install wallpapoz. I downloaded this one, Wallpapoz-0.3.tar.bz2, and am using Edgy. Thanks!

[http://wallpapoz.akbarhome.com/index.html](http://wallpapoz.akbarhome.com/index.html)

---

### Post by bodhi.zazen on 2007-01-23
From the document Install:

> To install:

1. Extract wallpapoz package
$ tar -jxvf wallpapoz-0.3.tar.bz2

2. Go to wallpapoz directory
$ cd wallpapoz-0.3

3. Get root permission
$ su

4. Install it
# python install.py install

Later if you want to uninstall it:
# python install.py uninstall

However installation is optional. You can run the program from the directory
directly after you extracted it.

Just run "wallpapoz.py" in src directory to launch the gui for creating
configuration file. Then run "daemon_wallpapoz.py" to launch the daemon it
self.

Enjoy!

In ubuntu for root permission use:```
sudo -i
```

What I would do is make a directory in ~ called src, move the tar ball there, extract there, run as a python script, and then if all is good install":

Assuming the tar ball is on your desktop:

```
mkdir ~/src
mv ~/Desktop/wallpapoz-0.3.tar.bz2 ~/src
cd src
tar -jxvf wallpapoz-0.3.tar.bz2
cd wallpapoz-0.3/src
python ./wallpapoz.py
```

the last cd may be ```
cd wallpapoz.py/wallpapoz-0.3/src
```

If you like install
```
sudo su -i
python install.py
```

---

### Post by kdarkentity on 2007-06-06
did this work for you?

---

### Post by bodhi.zazen on 2007-06-06
Those instructions were following the how-to and the link appears to have changed.

There is also an install script here:

[http://ubuntuforums.org/showthread.php?t=69507](http://ubuntuforums.org/showthread.php?t=69507)

Are you having problems ? If so, elaborate and we will try to help.

---

