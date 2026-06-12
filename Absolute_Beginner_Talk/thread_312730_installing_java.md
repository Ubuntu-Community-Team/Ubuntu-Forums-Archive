---
title: "installing java"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-12-04
Azureus seems to keep crashing when I load it and I'm wondering if it has to do with the java I'm using. Does anyone know how to install the latest java runtime environment? Thanks

---

### Post by taurus on 2006-12-04
What version do you have right now?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by nickburns on 2006-12-04
To get the latest jre type:

sudo apt-get install sun-java5-jre

in a terminal, you can also get the jdk with:

sudo apt-get install sun-java5-jdk

---

### Post by soulful1 on 2007-12-05
I'm going through almost the same problem. I load everything on the terminal and it gets to  the "Configuring sun-java6-jre" blue screen and then it's just stuck there. I don't know where to go from here. I'm just at the point of throwing my laptop...but I digress..lol

---

### Post by soulful1 on 2007-12-06
I am really having the worst time trying to install java...lol. I've done everything from the terminal instructions to synaptic. It will just not install. Then I do the restricted extras and I get on the blue screen and it just sits there. What should I do?

---

### Post by soulful1 on 2007-12-06
*hourly bump*

---

### Post by SOULRiDER on 2007-12-06
As far as i can remember you have to agree to a licence to finish installing Java. Dont you see a lcience window? If you still cantinstall you could gget the bin package form java.sun.com although i think its to be used as a last resort.

---

### Post by dimbulb1024 on 2007-12-06
Have you tried using Add/Remove to install JRE? Maybe Synaptic Package Manager will enable you to remove any part of JRE and then you can try installing it again.

---

### Post by soulful1 on 2007-12-06
All it has is <ok> at the bottom. I hit enter and nothing happens..

---

### Post by SOULRiDER on 2007-12-06
Try pressing tab until you select it or try selecting it witht he arrow keys and then press enter, Also, what version of ubuntu are you using and what are you using to isntall it? Synaptic, apt-get or aptitude ?

---

### Post by soulful1 on 2007-12-06
7.10 and apt-get

It finally went through and I got this:

> Setting up sun-java6-jre (6-03-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 jde
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

