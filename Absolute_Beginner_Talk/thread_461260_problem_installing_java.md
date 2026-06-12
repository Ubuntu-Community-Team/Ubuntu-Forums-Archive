---
title: "problem installing java"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-06-01
hello,

i just tried installing java on my ubuntu feisty box following a thread in this forum and i got the following error:

```
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
kris@91-190kris:~$ java -version
dpkg --configure -a
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
kris@91-190kris:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
kris@91-190kris:~$ 

```

that appeared in the last part of the terminal message. can anyone please help me fix this? i have no idea what to do.

million thanks!

---

### Post by Sparkster185 on 2007-06-01
> 'dpkg --configure -a'

Did you actually try running that, like it asked you to?

Are you installing it via Synaptic/Adept?  It worked perfectly for me using Adept.

EDIT:  You are going to have to put "sudo" before that command or it will fail.

---

### Post by shadowboxer_k on 2007-06-01
thanks, sparkster!

ok, i guess my problem was that i forgot to write sudo before the command, but here's what i get after writing it correctly in terminal:

```
kris@91-190kris:~$ sudo dpkg --configure -a
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

kris@91-190kris:~$ 

```

i wonder what i shall do next. try installing java from scratch?

---

### Post by jonward0690 on 2007-06-01
Yea i installed java to and broke my synaptic packger i used automatix to install java instaead

---

### Post by Sparkster185 on 2007-06-01
I think it correctly installed.  Try typing
```
which java
```

If that shows a result (something like /usr/java/jdk1.5.0_10/bin/java), then you should be good to go.

---

### Post by shadowboxer_k on 2007-06-01
i think it worked. thanks!

---

### Post by shadowboxer_k on 2007-06-01
ok, it looked liked it worked, but apparently hasn't because even after a restart (which i guess is a nasty habit from windows) the applet tells me to install the missing plugins.

how do i install java from automatix?

---

### Post by Seisen on 2007-06-01
are you talking about the java plugin for firefox?

---

### Post by jonward0690 on 2007-06-01
Go to this link [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)       download and install automatix and then you will see in automatix codecs and plugens and rite there when you launch automatix you can install java.

---

