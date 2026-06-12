---
title: "Java 1.4.2"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-11-26
Hey I need the java SDK 1.4.2 package installed on my comp, but when i double click it, it says it cannot be displayed? do i have to be in terminal and sudo it? if so how does the code look. i'm sorry about the lame question but i reallyr eally want to get to understsand linux

any help would be greatly appreciated

here's the link if that helps

[http://java.sun.com/j2se/1.4.2/download-netbeans.html](http://java.sun.com/j2se/1.4.2/download-netbeans.html)

d/led package name:

j2sdk-1_4_2_10-nb-4_1-linux-ml.bin

thx,
ad

---

### Post by Xian on 2005-11-26
This package is available via Synaptic.
Just enable the Multiverse repo.

From the wiki: [Synaptic How-To](http://www.ubuntulinux.org/wiki/SynapticHowto)

```
$ apt-cache policy j2sdk1.4
j2sdk1.4:
  Installed: (none)
  Candidate: 1.4.2.02-1ubuntu3
  Version table:
     1.4.2.02-1ubuntu3 0
        500 http://archive.ubuntu.com breezy/multiverse Packages
```

---

### Post by ds[de] on 2005-11-26
The way I understood you, you already have the file but want to install it?

In this case, again ;-) type

sudo chmod 755 j2sdk-1_4_2_10-nb-4_1-linux-ml.bin

and then

./j2sdk-1_4_2_10-nb-4_1-linux-ml.bin

Although you should be using JSDK 1.5.0, it has some neat improvements.

Regards,
ds[de]

---

### Post by adduds on 2005-11-26
[QUOTE='ds[de]']
Although you should be using JSDK 1.5.0, it has some neat improvements.

Regards,
ds[de][/QUOTE]

ya, i'm in computer science at the u of w and our prof reccomends using 1.4.2 just because he's sure their will be no problems with it

would it make a difference if i did us 1.5.0?

thx,
cheers,
ad

---

### Post by Darrin on 2005-11-26
I have 1.5 and dont have any issues with it.

---

### Post by sjh on 2005-11-26
[QUOTE='ds[de]']

Although you should be using JSDK 1.5.0, it has some neat improvements.

[/QUOTE]

I agree.  I used this How-To and had no problems.

[http://www.ubuntuforums.org/showthread.php?t=76754&highlight=install+jre+plugin+firefox](http://www.ubuntuforums.org/showthread.php?t=76754&highlight=install+jre+plugin+firefox)


SJH

---

### Post by adduds on 2005-11-26
Peer pressure is it? lol, well i just installed 1.4.2, can i just d/l the 1.5.0 package and install it on top lol. and fmi how do i see i think it installed in /etc/j2se/1.4
does that sound right? sorry just tinkering trying to figure ish out

thx/cheers,
ad

---

### Post by Xian on 2005-11-26
[QUOTE=adduds]ya, i'm in computer science at the u of w and our prof reccomends using 1.4.2 just because he's sure their will be no problems with it[/QUOTE]
I'd go with the proffessor. You don't want to bork a project and give him/her a reason to say, "I told you so." You'll never win that argument with, "But some folks at the Ubuntu forum said it would be fine."

:)

---

### Post by adduds on 2005-11-26
lol, ya i installed 1.4.2 perfectly fine, i'm just gonna get a java editor. actually are their any java editors built into ubuntu?

---

### Post by ds[de] on 2005-11-27
I don't know about a Java-IDE that comes along with the regular Ubuntu installation, but if you are using Gnome, you can use gedit (gnome editor), it has Java (among others) Syntax Highlightning. If you want more, I can recommend Eclipse SDK 3.11 (the most recent version right now), it really makes things easier for you, if you are working on more than just one file. 

Head over to 
[http://www.eclipse.org/downloads/index.php](http://www.eclipse.org/downloads/index.php)
to get it.

Regards,
ds[de]

---

### Post by adduds on 2005-11-27
Ya i'm working w/ multiple classes (OOP), so Eclipse would be wicked thx man

cheers,
ad

---

