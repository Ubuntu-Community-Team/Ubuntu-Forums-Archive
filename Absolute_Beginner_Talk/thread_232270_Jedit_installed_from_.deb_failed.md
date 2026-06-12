---
title: "Jedit installed from .deb failed"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by rpaller on 2006-08-08
After downloaded the .deb from [jedit.org]("http://www.jedit.org/index.php?page=download") and using  GDebi my package manager is hosed. Now when I attempt to remove or re-install via apt-get I received the following:

```
sudo apt-get -m install jedit
Reading package lists... Done
Building dependency tree... Done
E: The package jedit needs to be reinstalled, but I can't find an archive for it.

```

:(

---

### Post by cstudent on 2006-08-08
Did you add the repository to your sources.list?

```

To install jEdit via Debian Linux apt-get, add the following lines to your /etc/apt/sources.list:

deb http://dl.sourceforge.net/sourceforge/jedit ./
deb-src http://dl.sourceforge.net/sourceforge/jedit ./

```

From the jEdit download page:
[http://www.jedit.org/index.php?page=download](http://www.jedit.org/index.php?page=download)

---

### Post by Engnome on 2006-08-08
sudo dpkg --remove --force-depends --force-remove-reinstreq <package name>

if it doesnt work have alook here [http://ubuntuforums.org/showthread.php?t=39563](http://ubuntuforums.org/showthread.php?t=39563)  (google is god [-o<  ;) :p )

---

### Post by rpaller on 2006-08-08
> **Engnome said:**
> ```
sudo dpkg --remove --force-depends --force-remove-reinstreq <package name>
```


Thank you. That did the trick. 

I had looked at dpkg options but obviously not close enough.

---

### Post by muz1 on 2006-08-09
> **Engnome said:**
> sudo dpkg --remove --force-depends --force-remove-reinstreq <package name>

if it doesnt work have alook here [http://ubuntuforums.org/showthread.php?t=39563](http://ubuntuforums.org/showthread.php?t=39563)  (google is god [-o<  ;) :p )

I had the same problem. After doing the force remove, I added the two lines [B]deb [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./
deb-src [http://dl.sourceforge.net/sourceforge/jedit](http://dl.sourceforge.net/sourceforge/jedit) ./ [/B]

to my /etc/apt/sources.list file at the bottom and then after saving, called up the package manage, went into **advanced** and did a search for ***jedit***.

It was on its own. Clicked to install it and it installed perfectly.

After it had installed, I went into my *Applications/Programming/* menu and chose Jedit. It said it was starting up and then just disappeared.

Has this happened to anyone else?

Cheers n propz
muz

---

### Post by cstudent on 2006-08-09
> **muz1 said:**
> After it had installed, I went into my *Applications/Programming/* menu and chose Jedit. It said it was starting up and then just disappeared.

Has this happened to anyone else?

Cheers n propz
muz

What happens if you try to run it from the terminal? Just enter jedit at the prompt. Do you get any error messages?

Do you have the Sun Java 1.5 installed and set as default?

---

### Post by raneksi on 2006-08-10
i have exactly the same problem. it just disappears and nothing happens.
here's what happens when i run it in terminal
```

rane@rane-desktop:~$ jedit
GC Warning: Out of Memory!  Returning NIL!
Exception in thread "main" GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
*** Catastrophic failure while handling uncaught exception.
GC Warning: Out of Memory!  Returning NIL!

```

i don't know which java i have

---

### Post by cstudent on 2006-08-10
> **raneksi said:**
> i don't know which java i have

Enter in a terminal:
```

java -version

```

It should say 1.5.0_06 if you have the newest available.


If not, then open Synaptic. Make sure you have the extra repositories (universe & multiuniverse) enabled. Hit the Reload button. When it gets finished updating do a search for sun java. I believe the package you want to install is sun-java5-bin.

After installing it run update alternatives from a terminal:
```

sudo update-alternatives --config java

```

Make sure the * is marking the java-1.5.0-sun vesrion. If not enter the number for it and hit enter.

---

### Post by raneksi on 2006-08-10
> **cstudent said:**
> Enter in a terminal:
```

java -version

```

It should say 1.5.0_06 if you have the newest available.


If not, then open Synaptic. Make sure you have the extra repositories (universe & multiuniverse) enabled. Hit the Reload button. When it gets finished updating do a search for sun java. I believe the package you want to install is sun-java5-bin.

After installing it run update alternatives from a terminal:
```

sudo update-alternatives --config java

```

Make sure the * is marking the java-1.5.0-sun vesrion. If not enter the number for it and hit enter.

rane@rane-desktop:~$ java --version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

hehe, i did sudo update-alternatives --config java and selected the newest one and now it works. thanks.

---

### Post by chrisbaume on 2006-08-19
Don't try installing sun-java5-bin using Adept! It will fail and provide you with plenty of problems.

Instead, run
```
sudo apt-get install sun-java5-bin
```
from the console.

---

