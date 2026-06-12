---
title: "[SOLVED] Adding .jar programs to Applications menu"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Evmax318 on 2007-10-20
Ok, so I just downloaded a program called "jmemorize" I used this program on windows but it downloaded as a .jar file and I am not sure where to extract it so I can access it from the Applications menu

---

### Post by Frak on 2007-10-20
Goto System->Preferences->Main Menu, click the appropriate menu group, then "New Launcher", then give it the appropriate locations and command option, and Icon. Close, then check the Applications menu for the new program.

---

### Post by Evmax318 on 2007-10-20
So It really makes no difference where I extract the file?

---

### Post by Frak on 2007-10-20
You shouldn't extract the file.

---

### Post by Evmax318 on 2007-10-20
Ok, let me rephrase that: So It really makes no difference where I put the file? Is there a specific place I should drop it?

---

### Post by Beggar on 2007-10-20
Jar files are java executable files, just like with an exe everything you need is stored inside them, but you dont need to uncompress them in order to run them. From the command line you want to run```
java -jar <target>.jar
```. Just add a launcher that runs that command and you are all set.

Example if I place the jar in my home directory run ```
java -jar /home/beggar/myJar.jar
```

---

### Post by Evmax318 on 2007-10-20
Thanks beggar, it worked

---

