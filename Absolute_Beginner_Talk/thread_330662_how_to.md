---
title: "how to?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by JParkus on 2007-01-03
i need to be su to add a file but i dont know how im trying to fix my sound and i found this

[http://www.oliyiptong.com/blog/2006/07/15/old-hardware-help-in-ubuntu/](http://www.oliyiptong.com/blog/2006/07/15/old-hardware-help-in-ubuntu/)

---

### Post by nunomiguelmota on 2007-01-03
try: 
> sudo gedit [path of the new file]

---

### Post by Tomosaur on 2007-01-03
If you're playing in the command line, you use sudo for command line apps, and gksudo for graphical apps:
```

sudo nano

```
```

gksudo gedit

```

In the command line, you will not see your password being entered, so just type it out carefully and hit enter.

---

### Post by benuski on 2007-01-03
To do this, you can either do ```
sudo nano /etc/modprobe.d/soundcard
``` 
to edit it in an editor on the command line, or you can do ```
gksudo gedit /etc/modprobe.d/soundcard
```
 and edit it graphically with gedit.

---

### Post by JParkus on 2007-01-03
GNU nano 1.3.10        File: /etc/modprobe.d/soundcard              Modified

alias sound-slot-0 snd-card-0
 alias snd-card-0 snd-es18xx
$×330 irq=5 dma1=1 dma2=5




                                  [ New File ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

im this far how do i save it

---

### Post by benuski on 2007-01-03
Hit Ctrl+O to "Write Out" and the Crtl+X to exit.

---

