---
title: "Need help with Nvidia 6600GT"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by wilsonisme on 2006-01-31
Sorry guys, just realised this would probably be better suited in the hardware section, so I posted [there]("http://ubuntuforums.org/showthread.php?p=696826#post696826")

---

### Post by o_fortuna on 2006-01-31
[QUOTE=wilsonisme]Sorry guys, just realised this would probably be better suited in the hardware section, so I posted [there]("http://ubuntuforums.org/showthread.php?p=696826#post696826")[/QUOTE]
If you get to the ugly screen, hit Ctrl+Alt+F2 on your keyboard (like Ctrl-Alt-Del in Windows). This will bring you to a black-and-white console (you'll need to log in probably, and note that you won't see your password as you type it in). Then you just type
```
sudo apt-get install nvidia-glx
```
When that's done, type
```
sudo nvidia-glx-config enable
```.
Now you need to restart the X server. Type this:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo /etc/init.d/gdm start
```.
That should do it.

---

