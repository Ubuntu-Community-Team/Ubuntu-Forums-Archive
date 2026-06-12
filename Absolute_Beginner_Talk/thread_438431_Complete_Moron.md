---
title: "Complete Moron"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by AbsurdParadigm on 2007-05-09
I don't know why, but nothing seems to work for me on my Ubuntu 6.10 Server. For example, I look up directions on how to install things.

For example, I'm trying to install the Java Runtime Environment. I try to follow these directions:
[http://java.com/en/download/help/5000010500.xml#rpm](http://java.com/en/download/help/5000010500.xml#rpm)

I create a java folder, so I have a usr/java/ location on my box. Then, I copy the file over to that directory using Krusader. At this point, I type chmod a+x jre-6u1-linux-i586-rpm.bin
to change the permissions of the file, then ./jre-6u1-linux-i586-rpm.bin to run the file and unpack it.

At this point it says 
[I]Unpacking...
./jre-6u1-linux-i586-rpm.bin: 275: cannot create install.sfx.7680: Permission denied
Checksumming...
/usr/bin/sum: install.sfx.7680: No such file or directory
[: 302: 35015: unexpected operator
[: 302: 18075: unexpected operator
chmod: cannot access `install.sfx.7680': No such file or directory
Extracting...
./jre-6u1-linux-i586-rpm.bin: 305: ./install.sfx.7680: not found[/I]

I copied the files and made new directories in root mode Krusader, but did the command line stuff in a Konsole. This is so frustrating! I can't install anything unless it's with apt-get or Synaptic.   :(    

Brent

---

### Post by aJayRoo on 2007-05-09
First of all i notice you have downloaded the self extracting rpm version. I think you will need just the self extracting version (instructions for installing that are just above those for the rpm version on the page you linked). Also you must use sudo to start the installer with root privileges so type

```
sudo ./jre-1_5_0-linux-i586.bin
```

hope that helps

---

### Post by zvacet on 2007-05-10
Just download self extracting version(no rpm) and follow the instructions.Maybe this can help you too

[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by AbsurdParadigm on 2007-05-11
Using the non-RPM version seems to have done the trick. THANKS SO MUCH!  :-D 

Brent

---

