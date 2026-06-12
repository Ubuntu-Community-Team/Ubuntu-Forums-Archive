---
title: "launch prog at startup"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by byenary on 2006-04-02
hellow fellows im looking for a way to start a program autmaticly on boot, has to work without logging in to X.
purpose : to start stunnel automaticly when i reboot ubuntu server

Thx

---

### Post by halitech on 2006-04-02
try this out, took awhile to find but should work :)

[]("http://www.ubuntuforums.org/showthread.php?t=117655&highlight=start+program+boot")

---

### Post by byenary on 2006-04-02
Try what out ?

---

### Post by xXx 0wn3d xXx on 2006-04-02
System > Preferences > Sessions. Then click on Start up Programs and add what you want.

---

### Post by byenary on 2006-04-02
And the no X method ?

---

### Post by halitech on 2006-04-02
sorry bout that, not sure what happened to my link but it was basically what Master CHief suggested. 

Try this one if you want it without X

[http://ubuntuforums.org/showpost.php?p=606737]("http://ubuntuforums.org/showpost.php?p=606737")

---

### Post by Zeroangel on 2006-04-02
Have you considered putting a script in /etc/rcS.d/ ?

I'm a linux newbie, but that seems like the most logical place.

---

### Post by patrick295767 on 2006-04-02
Non X version
========
To boot sthg : 
```

echo "myscriptstuff" > /etc/init.d/myscript.sh
chmod +x  /etc/init.d/myscript.sh
ls /etc/rc2.d
ln -s /etc/init.d/myscript.sh /etc/rc2.d/S75myscript.sh
```

(sthg like this )

Greetz

---

