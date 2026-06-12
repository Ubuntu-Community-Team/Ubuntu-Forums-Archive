---
title: "How to install archmage? [Resolved]"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by niteblind on 2007-02-24
Hi

I downloaded a program called archmage but it was not onthe repositories so i am not entirely sure what to do now. I pull down both versions of the file one ends with a .i686.rpm extension and the other with .src.rpm which one should i use and then what do i have to do to install them?

cheers

---

### Post by v8YKxgHe on 2007-02-24
> **niteblind said:**
> Hi

I downloaded a program called archmage but it was not onthe repositories so i am not entirely sure what to do now. I pull down both versions of the file one ends with a .i686.rpm extension and the other with .src.rpm which one should i use and then what do i have to do to install them?

cheers

RPM packages are not compiling from source. an RPM (Red Hat Package Management) is pretty much like Debian's/Ubuntu DEB files. You'll have to convert them to .deb packages with a program called "Alien", in terminal type:

```
sudo apt-get install alien
```

Or search for Alien in Synaptic (System->Admin->Synaptic ).

Once installed, go to terminal and type "alien /path/to/rpm/file" and wait, it should then create a .deb package. Once done, simply double click on the .deb file.

---

### Post by Maestro23 on 2007-02-24
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by niteblind on 2007-02-24
hi

i did what was advised above and when i tried to double click the file it came up with and error in ARK saying the file is not in your path. The file is located @ /home/niteblind/Desktop/Downloads. Which i though was in my path.

I tried moving it to the /niteblind folder and running from there still the same. So i thought maybe something int he way alien had ported it over was knackered so after a bit of googling I found a newer version that was already a .deb file but it does the same thing to.

Where am i supposed to put the file before i try and run it? Do i need root priveleges to do it? where will it put it afterwards and finally if I do manage to get it installed will it have all dependacies included and if not how do i fine out where to get them?

cheers
niteblind

---

### Post by igknighted on 2007-02-24
use 'alien --help' to give you the syntax.  Most commands you can do a --help to get information about what they can do and what the syntax is.

You need to make sure before you install the .deb created by alien that all dependencies are installed.  The website you got the .rpm from should say what those are.  Do not try to install without the dependencies in most cases because you risk hosing your system.  The .deb's should go in the directory you are currently in.

---

### Post by aysiu on 2007-02-24
I don't know if you'll run into a lot of crazy dependencies, but there's a .deb available for Feisty for that program: ```
wget -c http://mirrors.kernel.org/ubuntu/pool/universe/a/archmage/archmage_0.0.7-2_all.deb
sudo dpkg -i archmage_0.0.7-2_all.deb
```

---

### Post by Jussi01 on 2007-02-24
> **aysiu said:**
> I don't know if you'll run into a lot of crazy dependencies, but there's a .deb available for Feisty for that program: ```
wget -c http://mirrors.kernel.org/ubuntu/pool/universe/a/archmage/archmage_0.0.7-2_all.deb
sudo dpkg -i archmage_0.0.7-2_all.deb
```

Argh, I just tried them to see how he would go... dependancy crazyness....

---

### Post by aysiu on 2007-02-24
> **Jussi01 said:**
> Argh, I just tried them to see how he would go... dependancy crazyness....
Okay. Maybe *alien*ing the RPM is the way to go, then.

---

### Post by Jussi01 on 2007-02-24
Ok, got it figured now - you need to install python-chm and libchm1 together...

So:

```
wget -c http://mirrors.kernel.org/ubuntu/pool/universe/a/archmage/archmage_0.0.7-2_all.deb
```

Then
```

 sudo apt-get install libchm1 python-chm
```

Then
```

sudo dpkg -i archmage_0.0.7-2_all.deb
```

Should work.

Good luck...

---

### Post by niteblind on 2007-02-25
thanks for all the help!

niteblind

---

