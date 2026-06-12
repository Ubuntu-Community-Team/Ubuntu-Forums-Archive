---
title: "Sun JDK : after 'apt-get install sun-java5-jdk', where is the jdk source file?"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by matthewyoung on 2006-12-09
where is the jdk source? Under WinXP, it's in a file src.zip

find / -name 'src.*' -print

come up with nothing :(

---

### Post by taurus on 2006-12-09
:confused: 

Are you trying to install Sun's java on your machine?

---

### Post by matthewyoung on 2006-12-09
No, Install is done already using 'sudo apt-get install sun-java5-jdk', now I need to find the jdk's source code files.  You know, all those .java and jni .h files.

---

### Post by matthewyoung on 2006-12-09
Ok, found it:

apt-get install sun-java5-source

---

