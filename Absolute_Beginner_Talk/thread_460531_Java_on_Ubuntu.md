---
title: "Java on Ubuntu"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Jokeaflorias on 2007-05-31
I spent an hour or so last night trying to get Java on my Ubuntu system, and I went through various threads trying things but I just couldn't do it. Could anybody help me out?

---

### Post by taurus on 2007-05-31
If you are running Feisty Fawn, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
java -version
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Jokeaflorias on 2007-05-31
> **taurus said:**
> If you are running Feisty Fawn, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
java -version
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

That worked. I got this when I used the java -version command: [I]java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/I]


According to firefox, I need the Java Runtime Enviroment plugin. Could you help me with that as well? Thanks!

---

### Post by drs305 on 2007-05-31
```
sudo aptitude install sun-java6-jre
```

---

### Post by doogy2004 on 2007-06-01
Java can be installed using Automatix, get it at [www.getautomatix.com](www.getautomatix.com)

---

