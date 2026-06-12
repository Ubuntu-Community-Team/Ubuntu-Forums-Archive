---
title: "installing / finding new progs"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by stonecold23 on 2007-04-24
installed winex but cant find where it is on system
also need to know - is it windows 64bit version it doesnt work with or is it the amd 64 processors.

also i have know idea how to install programs that i download!
unless the add remove programs can do it for me
i just downloaded an auto run program but dont know how to make it work?

have amd processor.

---

### Post by mikewhatever on 2007-04-24
Do yourself a favor and slow down. Installing software in Ubuntu is different to the way it's done in windows. There are several ways to do it, and you may get different types of files as an installer. 
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
I'd strongly suggest getting familiar with the concepts first.
To locate a file, use the search function available in the file browser (Nautilus) window.

---

### Post by mlentink on 2007-04-24
> **stonecold23 said:**
> also i have know idea how to install programs that i download!
unless the add remove programs can do it for me
i just downloaded an auto run program but dont know how to make it work?

have amd processor.

You might want to take a look at the wine docs over at winehq.org.
I don;t know about 64-bit versions...

---

### Post by tomcheng76 on 2007-04-24
"which" and "whereis" command can find the location of the software
usage: whereis wine

you can install generic version of kernel for x86/x86_64 instead of i386 version

if you download the deb package (.deb file extension)
you can install them by
```
sudo dpkg -i filename.deb
```

what is your auto run program name and also the filename of the setup?

The best way to install software is to use synaptic
System->Preference->Synaptic software manager

---

### Post by mlentink on 2007-04-24
I'm probably wrong, but I was under the impression that the OP was referring to the installation of progs under Wine/WineX. If not, my suggestion was obviously off the mark...

---

