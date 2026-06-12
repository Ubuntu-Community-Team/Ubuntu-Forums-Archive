---
title: "Can`t open xorg.conf"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by plopp on 2006-04-17
I Changed my monitor and obviously screwed up something because now X-server won`t start. I changed the refresh rate and monitor name in xorg.conf and rebooted and then I got an error message on a blue screen which said that x-server could not start. Looking at the error I`d say the problem is in the monitor name. And the error:

Data incomplete in file /etc/x11/xorg.conf
Undefined monitor "generic monitor"
referenced by screen
"default screen"
(EE) problem parsing the config file
(EE) problem parsing the config file
Fatal server error:
noscreens found


After this I only get a black screen with the text: "ubuntu 5.10 "breezy badger" plopp tty1", from here I can login to something, don`t think its the terminal because I can`t open /etc/x11/xorg.conf with the command "sudo gedit /etc/x11/xorg.conf ". No idea what to do now and because I don`t really have the slightest clue what I am logged into perhaps someone cuold tell me what to do...

---

### Post by christhemonkey on 2006-04-17
it is a terminal.
The Xserver (GUI type thing) isnt runnning so you cant use gedit.
Try using nano
```
sudo nano /etc/X11/xorg.conf
```
Note that its X11 not x11.

The controls for nano (i forget what they are, more of a vi person myself) are listed at the bottom.

---

### Post by christhemonkey on 2006-04-17
Forgot to say what you should do, if their is an obvious error, change it, if their isnt:
Exit nano, then type from the command line:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Which will give you back to your default setup.

---

### Post by zerhacke on 2006-04-17
Gedit won't run because it requires X.  You can't load an X program if X won't start.  Try this : 

```
sudo apt-get install pico
``` at the command prompt.

Once you've got pico installed, at the command prompt type 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo pico /etc/X11/xorg.conf
```

Pico will open your xorg.conf file.  Make the changes you need to make, then press Control+O at the same time then Enter to save the file.  Control-X quits.

---

### Post by plopp on 2006-04-17
Got my screen back now and thanks for this.

---

