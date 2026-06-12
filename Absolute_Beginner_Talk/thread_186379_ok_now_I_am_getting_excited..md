---
title: "ok now I am getting excited."
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by jodear on 2006-06-01
Now I am getting excited!!!  Now with all the distros I have installed and gave up on prematurely, I now have ubuntu playing xvids!  
Now is I am using terminal to launch mplayer (preferred way I presume), gui not working great yet.  but anyway, back to the point . . . I know about the -fs switch to switch to full screen but this does not actually stretch the video across the screen.  The video I am watching now is 576x240 and I am running a 1280x1024 res on my lcd. Mathematically this makes for a small window to watch from.  How do I stretch the video across the screen. can I do this with switch from the command-line?

---

### Post by aktiwers on 2006-06-01
```
sudo gedit /etc/mplayer/mplayer.conf
```
Find this line:
```
 vo=x11,         
```
Replace with the following line:
```
 vo=xv,         
```

That should work.

---

### Post by jodear on 2006-06-01
out-freaking-standing.

such simplicity I love this stuff!

---

### Post by uzi09 on 2006-06-02
[QUOTE=jodear]out-freaking-standing.[/QUOTE]

**ROFLMFAO!!!!!!!!!!!**

ahahahahahaha, oh man!
(sorry for spammin, but i just had to get that out!)

---

### Post by jodear on 2006-06-02
[QUOTE=aktiwers]```
sudo gedit /etc/mplayer/mplayer.conf
```
Find this line:
```
 vo=x11,         
```
Replace with the following line:
```
 vo=xv,         
```

That should work.[/QUOTE]


ok now I have to ask, why did that work?  what are the inner workings of such a small edit make a difference?

---

### Post by uzi09 on 2006-06-26
sorry this is so late, i was hoping someone who knows more about this stuff would better explain it, but since they haven't....

basically, you're just telling mplayer what type of video output you want it to use. it's just as simple as plugging in the leads from ur DVD player to your TV. if you plug in the wrong one, it isn't going to work, but if you put it in the right place, it'll work flawlessly :D

---

### Post by siccness on 2006-06-26
[QUOTE=jodear]ok now I have to ask, why did that work?  what are the inner workings of such a small edit make a difference?[/QUOTE]

Basically the program reads from the configuration file to see what settings it's using, and then performs, or behaves the way it should with the configuration.

---

