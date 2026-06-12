---
title: "Help!?!?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by ihappen on 2007-01-17
When trying to load from the the ubuntu disk, I keep getting the message "failed to start the X server (your graphical interface) It is likley its not set up correctly"


Any ideas!?!?

---

### Post by bodhi.zazen on 2007-01-17
sounds like a hardware recognition problem.

Not to ask the obvious, but check the md5sum of your iso and CD

If that is OK, well we may be able to guide you on fixing from the CLI.

Hardware ? video card ? monitor ?

Change to tty2 : Ctrl-alt-F2

Enter:

```
sudo sudo dpkg-reconfigure -phigh xserver-xorg
```

Select resolution with up an ddown arrows, to select a resolution use teh space bar ...

The re-start X:```
sudo /etc/init.d/gdm restart
```

If needed, Ctrl-Alt-F7 to return to your GUI :p

---

### Post by ihappen on 2007-01-17
Sorry..,  but I really am a complete beginer, so I have very very little clue of what i need to do.

The iso and CD are fine as far as I know..!

---

### Post by jvc26 on 2007-01-17
This explains checking md5 sums and the cd to make sure that they are ok:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
Then, if you could tell us what your video card/hardware specs are that could also help,
And finally, like Bodhi says you can change into the second terminal thing via: Ctrl-alt-F2 and type the lines that he posted up.

Hope that clarifies some things :)
Il

---

### Post by jd65pl on 2007-01-17
[LIST=1]
[*]Please list your graphics card.
[*]Boot using the live cd
[*]Wait for the system to halt and give you an error
[*]Press [Ctrl] + [alt] + [F2]
[*]Do the command {1.} below
[*]Configure the xserver as instructed on screen
[*]Run command {2.} below once you are returned to the command line[/LIST]```
1. sudo sudo dpkg-reconfigure -phigh xserver-xorg
2. sudo /etc/init.d/gdm restart 
```

---

### Post by ihappen on 2007-01-17
CD checks out fine, 

I dont know what graphics card I'm useing, Is there any way I can find out.. Its a Dell dimension 5150 if thats any help

---

### Post by Repent on 2007-02-24
ihappen  do I know you?

---

