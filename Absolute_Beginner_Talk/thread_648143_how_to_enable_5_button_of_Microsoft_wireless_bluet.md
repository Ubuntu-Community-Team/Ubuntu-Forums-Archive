---
title: "how to enable 5 button of Microsoft wireless bluetooth mouse 8000?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-23
Hi, 

I have been trying to look for a way to enable 5 buttons..     2 button on the side to use in firefox.

Some says to try: 

hcitool scan 

But what I get is "Device is not available: No such device" 

I followed [http://www.funnestra.org/#enable-5button-mouse](http://www.funnestra.org/#enable-5button-mouse)

But the system went crazy.. .  Lucky I backed up /etc/X11/xorg.conf  like the instruction suggested. 


anyway, my Microsoft wireless bluetooth mouse 8000 works fine..   I just can't use the other buttons.. 


Just in case, /etc/X11/xorg.conf

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection



Cheers,

---

### Post by Phurious on 2007-12-23
You might try installing btnx.

```
sudo apt-get install build-essential libgtk2.0-0 libgtk2.0-dev libglade2-0 libglade2-dev pkg-config
wget http://www.ollisalonen.com/btnx/btnx-0.3.2.tar.gz
tar -xvvf btnx-0.3.2.tar.gz
cd btnx-0.3.2
make
sudo make install

wget http://www.ollisalonen.com/btnx/btnx-config-0.2.2.tar.gz
tar -xvvf btnx-config-0.2.2.tar.gz
cd btnx-config-0.2.2
./configure
make
sudo make install
```

[http://ubuntuforums.org/showthread.php?t=455656]("http://ubuntuforums.org/showthread.php?t=455656")

This is what I used to finally get the functionality I wanted out of my Logitech MX Revolution.

---

### Post by taekr on 2007-12-23
> **Phurious said:**
> You might try installing btnx.

```
sudo apt-get install build-essential libgtk2.0-0 libgtk2.0-dev libglade2-0 libglade2-dev pkg-config
wget http://www.ollisalonen.com/btnx/btnx-0.3.2.tar.gz
tar -xvvf btnx-0.3.2.tar.gz
cd btnx-0.3.2
make
sudo make install

wget http://www.ollisalonen.com/btnx/btnx-config-0.2.2.tar.gz
tar -xvvf btnx-config-0.2.2.tar.gz
cd btnx-config-0.2.2
./configure
make
sudo make install
```

[http://ubuntuforums.org/showthread.php?t=455656]("http://ubuntuforums.org/showthread.php?t=455656")

This is what I used to finally get the functionality I wanted out of my Logitech MX Revolution.

Thanks for the advice. I tried it. But this one is only for Logitech MX mouse..  Couldn't get it work.. Not for my mouse

---

### Post by TRAFFICBLOWS on 2008-06-07
Did you ever get the MS BT Mouse 8000 buttons to work?  I'm in the same situation here...

---

