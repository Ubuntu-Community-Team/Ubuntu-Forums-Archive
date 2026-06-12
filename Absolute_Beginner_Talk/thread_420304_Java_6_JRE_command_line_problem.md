---
title: "Java 6 JRE command line problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by TehKobe on 2007-04-23
I just did a clean install of Feisty Fawn and, and used Synaptic to get Java 1.6.0 JDK, JRE, etc. When I check the version of Java from the command line, I'm still using 1.4.2. Typing "javac -version" gives me 1.6.0, though. Any help on getting Java 6 JRE running right from the command line?

---

### Post by tbfr on 2007-04-23
You can select your VM using this command:

> sudo update-alternatives --config java

---

