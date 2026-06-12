---
title: "Someone knows how to record ur screen with istanbul ??"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-26
Hi
I installed it, istanbul from the repos... 
```
apt-get -f install istanbul
```
 
And would like to record screen ...

Someone knows how to do  ?

Thank you 

Pat

---

### Post by senning on 2006-02-26
Sure, real easy.  Run istanbul (<alt>+<f2>; then type "istanbul").  A big red circle should appear in your notification area.  Right click for prefs, click to start recording.  You can click the same area (becomes a white box) when you're done recording. 

Look [here]("http://live.gnome.org/Istanbul") for some more (better) advice.

---

### Post by patrick295767 on 2006-02-27
thank you, ...
(I forgot that I had some errors when writing my post) 
(I managed with xvidcap ...)

I got such error for istanbul:
  
```
winwood@Laptop06:~$ istanbul&
[1] 10034
winwood@Laptop06:~$ Traceback (most recent call last):
  File "/usr/bin/istanbul", line 30, in ?
    from istanbul.main import main
  File "/usr/lib/python2.4/site-packages/istanbul/main/main.py", line 26, in ?
    from istanbul.main import prefs
  File "/usr/lib/python2.4/site-packages/istanbul/main/prefs.py", line 18, in ?
    import gtk.glade
ImportError: No module named glade

[1]+  Exit 1                  istanbul
winwood@Laptop06:~$

```
  
(Python-gtk2
is installed )

---

### Post by cutOff on 2006-02-27
Try installing python2.4-glade2 or libglade2-0

---

