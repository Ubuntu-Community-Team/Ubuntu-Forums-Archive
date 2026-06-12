---
title: "How to remove java 1.4.0"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by IsKall on 2006-10-12
Ho do I remove java 1.4.0? Want to make a clean install of 1.5.0, need it for my studies.


Regards
iskall

---

### Post by Ben Sprinkle on 2006-10-12
```

sudo dpkg -u java

```
Then download latest from thier site.

---

### Post by taurus on 2006-10-12
How did you install it?  Did you install it with synaptic/apt-get/aptitude or did you install it by hand?

---

### Post by IsKall on 2006-10-12
sorry for not giving more information Taurus, I am very tired.


I made a fresh install of my ubuntu again, ubuntu install installs java 1.4.0 but need to remove it and make a clean install of 1.5.0.


sudo dpkg -u java, only unpacks. need to remove it completly.


/iskall

---

### Post by Ben Sprinkle on 2006-10-12
Why don't you just do:
```

sudo rm /usr/bin/java

```
Then install latest JRE from sun's site?
Tis what I did.

---

### Post by taurus on 2006-10-12
If you installed java 1.4.0 with synaptic/apt-get/aptitude, then you can remove it with

```
sudo aptitude remove java (or whatever the exact name is...)
```

---

### Post by Ben Sprinkle on 2006-10-12
He means that Java **came with ubuntu upon install**. (I think.)

---

### Post by IsKall on 2006-10-12
It was already installed when I installed ubuntu.

I will try that what you said Taurus, thank you.


/iskall

---

### Post by taurus on 2006-10-12
I might be wrong but I don't think it comes with java already on your system.  Perhaps you are confusing with the version that comes with gcc...

```
java -version
```

---

### Post by Ben Sprinkle on 2006-10-12
Mine came with Java.

---

### Post by IsKall on 2006-10-12
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

from java -version.

want to remove that and replace with 1.5.0.

---

### Post by Ben Sprinkle on 2006-10-12
Are you even listening to me?

---

### Post by IsKall on 2006-10-12
Sorry Goat Spirit, yes I do, but is it a smart way to do that? by removing its directory?`(just a question)

---

### Post by Ben Sprinkle on 2006-10-12
Just delete the executable: /usr/bin/java
Then download JRE and install.

---

### Post by raul_ on 2006-10-12
iskall where r u from? (just curious)
about ur question...if u update ur repositories i think that java 5 can be installed by apt-get..it's under sun-java or something like that..if ur lucky your old version is uninstallable with apt-get too. If u installed it with a tar.gz, u can download it again and do the same thing but instead of typing "make install", type "make uninstall" (i don't know if this always works, it worked for me)

---

### Post by IsKall on 2006-10-12
Ok so there is no other way that means. Will do that Goat. Thx for your help.

raul_ I know how to install things, just wanted to make a clean remove of java 1.4.0, and I am from Sweden.



/iskall

---

### Post by raul_ on 2006-10-12
When packages come installed with ubuntu they usually are in synaptic..if java is not (i'm sorry but i just doubt it) try adding extra repositories, install java 1.4 with them (yes, AGAIN) and then try removing them (completely), i think that will do the trick. after doing that and BEFORE INSTALLING 1.5, try checking the java version. if that worked, java 1.4 was removed. if u're not sure about that, try typing "locate java" and see if there's anything left

---

### Post by Ben Sprinkle on 2006-10-13
Work?

---

