---
title: "The Composite extension is not available"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-28
I get the message that the composite extension when I click System > Preferences > Desktop Effects

With synaptic I completely removed it.  Then again with synaptic I installed it.  But it doesn't work.  I have ATI drivers installed.  Can this problem be resolved.

I have had so many problems like this, but most of the time when I have posted here, someone directs me to enter a couple of commands and my system continues to improve and work better.  It is greaat to have a resource like you guys and a system like Ubuntu.

---

### Post by mattva01 on 2007-05-28
If you have the restricted ATI drivers, you can't use compositing.

---

### Post by ICUR2Ys on 2007-05-28
I was afraid that might be the case, that is why I mentioned the drivers.  Well at least I know that I don't have a fixable glitch.

I thank you very much

---

### Post by mattva01 on 2007-05-28
Well if  you don't do much 3d stuff the open source drivers are fine plus they allow you to use compositing.

---

### Post by ICUR2Ys on 2007-05-28
I am so new to linux that I really don't know what I will really be doing.  So many vistas are starting to open up that I am not sure how I will end up using this system.

---

### Post by mattva01 on 2007-05-28
Well welcome to the community !

---

### Post by ICUR2Ys on 2007-05-28
Thank You.

---

### Post by FNDII on 2007-07-11
So if i have the ATI restricted drivers i cant do any of the "cool" desktop effects? 

And if i play alot of games i want the restricted drivers?

---

### Post by Espreon on 2007-07-11
To use the restricted driver (fglrx) to its full potential you need to use an XGL session (unlike Edgy there is no XGL session in Feisty)

So here how:

```
sudo apt-get xserver-xgl
```

(if this the apt-get code does not work than search for XGL in Synaptic)

Now:

```
sudo gedit /usr/local/bin/startxgl.sh
```

Fill the blank file with this:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session

```

Then save.

```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

```

sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop

```

Fill the file with this:

```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME+XGL
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

```

Then save.

Log out and hit sessions and select GNOME+XGL
Now log in as usual.

Make it default if you like. If done correctly you shoud see a grey screen that looks like steel wool with a black X for a cursor (or at with the steel wool in my case at least), the splash should look normal.

Enjoy!

If it looks choppy and garbled Completely uninstall XGL and reinstall it.

---

### Post by lxstoian on 2007-08-09
I tryed what u said but the desktop is still really fuzzy. I have a ATI RADEON 9600 pro.

---

