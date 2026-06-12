---
title: "Java ???"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by trevorsowers on 2007-11-07
I am new to ubuntu (I also use OSX and XP) and I have found the set up of ubuntu quite easy except for java!!  My son plays runescape online so I need to get this working and I have tried downloading from the built in database as well as looking on the sun website.  I am not sure what I am doing wrong.  Any suggestions??

---

### Post by taurus on 2007-11-07
You can install it from synaptic or from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```

---

### Post by trevorsowers on 2007-11-09
this did not seem to work??  I am wondering about the space in you last part of the command.

java -version  or java-version

anyway I can´t get it to work.

---

### Post by Maestro23 on 2007-11-09
> **trevorsowers said:**
> this did not seem to work??  I am wondering about the space in you last part of the command.

java -version  or java-version

anyway I can´t get it to work.

Open up Synaptic, search for sun-java6.  Find each package he told you to and mark for install.

---

### Post by trevorsowers on 2007-11-09
Java works fine in Kazehakase browser but not firefox or opera!!!

---

### Post by mig5 on 2007-11-17
Type this in the firefox address bar to see if it's installed properly:
```

about:plugins

```

---

