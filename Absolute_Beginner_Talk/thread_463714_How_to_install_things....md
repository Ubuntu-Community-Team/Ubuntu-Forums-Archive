---
title: "How to install things..."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-04
Haha :) Call me a noob but I still dont know how to install stuff..

---

### Post by fenian on 2007-06-04
I would suggest you start by reading the articles [here]("https://help.ubuntu.com/community/SoftwareManagement").

---

### Post by kevdog on 2007-06-04
GUI tools:

Synaptic (Ubuntu Gnome), Adept (Kubuntu KDE)

Command Line tools:
aptitude, apt, dpkg

Probably at the beginning synaptic or adept are far easier to use, but I think aptitude is probably quicker and more powerful once you get your feet wet!

---

### Post by Feba on 2007-06-04
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by Ek0nomik on 2007-06-04
```
sudo aptitude search **programname**
sudo aptitude install **programname**
```

---

### Post by Inxsible on 2007-06-04
1) Applications --> Add/Remove
2) System --> Administration --> Synaptic Package Manager
3) ```
 sudo aptitude install programme-name
```
4) ```
 sudo apt-get install programme-name
```

---

### Post by pappapump on 2007-06-04
You're making the same mistake I did in assuming everything will install like windows.
The methods and programs mentioned above cover all the basic goodies, but if you start getting fancy you'll see that all other unsupported programs install many different ways, some include re-compiling.
Use a program like, wine or cedega and you'll be met with a whole new set of challenges as well.

The key here is to NOT think that there is just one way to install things.
That path quickly leads to frustration and error.

For example, had I even bothered to read some responses to my earlier posts, I could have saved myself from 5 of my hard drive wipes and re-installs of Ubuntu with a simple set of commands executed in the equivalent of safe mode in Linux.

I have since saved these instructions by making a hard copy and it has saved me loads of trouble thanx to people like inxible and spaceguy, who gave me the proper commands to run.

---

