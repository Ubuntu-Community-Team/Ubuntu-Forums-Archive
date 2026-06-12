---
title: "Bootable G++?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by 7Priest7 on 2007-11-08
I am looking for a Distro that I can boot...
I then use the shell to locate my C++ Code in my HD...
I then use G++ to get a linux distro...
I then eject cd and use my regular OS (Windows)...
This is mostly so I can expand my program/programs to linux user base...

I do not need a GUI as I know the linux hiearchy...
/mnt/hda1/...

Please And Thank You

Alex

---

### Post by ByteJuggler on 2007-11-08
Running GCC/G++ off a liveCD will be horribly slow I think.

I'd suggest you either 
1) install Linux on a seperate partition and then just install GCC/G++ and use it there (and mount your windows partition)
OR
2) Install Linux in a Virtual Machine and run GCC there

---

### Post by 7Priest7 on 2007-11-08
I have a powerfull PC
I think my PC can handle a shell with some G++ better than vista with a virtual machine with linux...
I do not want to use hard drive space on Linux...

Any distros that can do what I explained?

Please and Thank You

Alex

---

### Post by loell on 2007-11-08
interesting, i would imagine that it can be fast, given a fair amount of memory.
but i don't know of minimalist distro that includess g++ by default, anyone?

but probably you can use ubuntu and costumized it using reconstructor, striping all desktop related stuff :)
and include g++ , and an ascii IDE i'm not just sure if there is one.

---

### Post by amingv on 2007-11-08
Hi,

Well, for this purpose you can use **[Knoppix]("http://www.knopper.net/knoppix/index-en.html")**, it is a reasonably fast live distro, plus it has the GCC preinstalled (Verified on v5.1).

I know you said you don't want to use up space for Linux, but since you say you don't need the GUI, maybe you can spare some 500MB and install a distro without any X server and without most of the programs it includes. And I mean what's 500MB for the flexibility your HD will give you? Heck you can't even fit a decent movie in 500MB.

---

### Post by ByteJuggler on 2007-11-08
> **7Priest7 said:**
> I have a powerfull PC
I think my PC can handle a shell with some G++ better than vista with a virtual machine with linux...
I do not want to use hard drive space on Linux...

Any distros that can do what I explained?

Please and Thank You

Alex

Well off the top of my head I'd have a look at [Knoppix]("http://www.knopper.net/knoppix-info/index-en.html"), also google turns up [this ]("http://bccd.cs.uni.edu/")which seems promising. Also have a look at "[Damn Small Linux]("http://damnsmalllinux.org/wiki/index.php/FAQ")"

Aside: A minimalist command line only install of Linux (Ubuntu server maybe) can be done in very little diskspace (say 50-100Mb or so) into which you can then very easily install just the compilers and languages you want.

---

