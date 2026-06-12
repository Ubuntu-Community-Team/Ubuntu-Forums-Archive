---
title: "yes this is another java install help thread !!!!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by smooth3006 on 2008-03-19
okay i have read how to install java through the sudo command in terminal and i did. i installed java 6  "see photo ". but when i go to the java website, it says im running an older version. " see attached photo "   

the version the java page tells me to install is version 6 update 5. i have no idea how to install this package at all. shouldn't ubuntu automatically update java to the most current version ? 

im sorry for making another thread about this, but i have no clue how to fix it ? :confused:

---

### Post by glennric on 2008-03-19
Check your alternatives.  Type
```
sudo update-alternatives --config java
```
and make sure there is a star by the line with java-6-sun in it.  If not enter the number of that line.

---

### Post by Arthur Archnix on 2008-03-19
Are you running Hardy?

---

### Post by glennric on 2008-03-19
Yeah, unless you are running Hardy, the version of java in the repositories is not the newest.  Gutsy is at update 3, not update 5.

Edit:  Actually, it seems that even Hardy will only have update 4 and the developers have already frozen it there for the release.

---

### Post by smooth3006 on 2008-03-19
> **Arthur Archnix said:**
> Are you running Hardy?

no im running gutsy

---

### Post by smooth3006 on 2008-03-19
> **glennric said:**
> Yeah, unless you are running Hardy, the version of java in the repositories is not the newest.  Gutsy is at update 3, not update 5.

Edit:  Actually, it seems that even Hardy will only have update 4 and the developers have already frozen it there for the release.

so theres no way to install the newest version then ?

---

### Post by glennric on 2008-03-19
There are ways to install the newer version using java-package.  There is a tutorial somewhere.
Here is one:
[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package]("http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package")

---

### Post by smooth3006 on 2008-03-19
i guess for now ill just use the version that ubuntu installed, even though it's not the current one. it still works anyways. :)

---

