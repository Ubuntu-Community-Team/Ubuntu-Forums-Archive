---
title: "installing limewire."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-13
hey all i downloaded limewire to my desktop and tried to install it (double clicked and its a .rpm file) but it says "archive type not supported". any ideas?

---

### Post by lamalex on 2007-03-13
ubuntu does not support rpm format, see if you can get .deb or .tar.gz files. try frostwire anyway, its a bit better. if you cant find a deb, the program alien will install rpm but its not without risks

---

### Post by noob_saioke45601 on 2007-03-13
oh i see. thanks for the info ill give frostwire a shot.

---

### Post by tipsqueal on 2007-03-13
Honestly I would just not install limewire at all. In my experience I've had much more luck and much more speed using Bit Torrent. I know this doesnt really help solve your problem, but that's my suggestion. On the other hand, to solve your problem there are programs that can be used to convert a .rpm to a .deb. This thread should be able to show you how: [http://ubuntuforums.org/showthread.php?t=304335](http://ubuntuforums.org/showthread.php?t=304335)

---

### Post by psynyd on 2007-03-13
LimeWire is written in Java so:

1) Download the tar.gz
2) Unzip
3) goto the folder using the Terminal and type : 
```
java -jar LimeWire.jar
```

It should be up and running. 

Alternatively you can:

1.) Goto System-> Preferences-> Menu Layout
2.) Choose appropriate menu(usually Internet or a separate option depending on how you want to arrange it)
3) Click New Item
4) Type LimeWire in Name
5) "Java -jar ~/LimeWire/LimeWire.jar" (without quotes and assuming it is unzipped in the home folder. You can change path according to ur needs)
6) Check Run in Terminal option

The LimeWire option should be added to your menu!

oh I haven't used frostwire but i love bittorrent and amule both of which come bundled with ubuntu. try them both.

Hope this helps!

psynyd
fellow newbie

---

### Post by jfinkels on 2007-03-13
just for kicks, to convert from .rpm to .deb:
```
alien -d *packagename*.rpm
```

---

### Post by WishMaster on 2007-03-18
I used the "java -jar .." method:

[IMG]http://img471.imageshack.us/img471/529/schermafdrukav3.png[/IMG]

---

