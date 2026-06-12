---
title: "Architecture"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by carverj on 2007-02-23
Hi all,
        Just wondering if i386 and i686 are classed as architecture types, and if so how do I locate this type of information on my machine?

Basically I'm trying to install wine from these instructions
[http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a](http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a)
and am unsure of which libc6 libraries to install
I have 64 bit AMD.
Thanks for that.

---

### Post by nickoli_02 on 2007-02-23
That guide is specifically for building wine on a 64-bit machine. You should just be able to follow the steps to the T

---

### Post by carverj on 2007-02-23
Thanks for prompt reply... getting this output in terminal

```
jeremy@jeremy-desktop:/$ sudo apt-get install gcc flex bison libc6-i386 libc6-dev-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
flex is already the newest version.
E: Couldn't find package libc6-i386

```

When I look in Synaptic, I have libc6-i686 installed. So I was looking for an explanation for 
what the difference is and if I have the right one installed!?
Cheers

---

### Post by carverj on 2007-02-23
Oh, just typed the following:
jeremy@jeremy-desktop:~$ uname -r
2.6.17-10-386

---

### Post by nickoli_02 on 2007-02-23
The i386 architecture refers to Intel's 386 processor and newer. i686 refers to the Pentium-class architecture. i386 libraries are generally preferred because they support hardware as far back as the 386 and, well, i686 libraries don't. Performance gains from using i686 libraries on Pentium-class architecture are in the 1-5% range, negligible in day-to-day usage.

Try updating apt and see if it'll find the 386 libraries after that... there's no way they aren't in the repos. Also make sure you have universe and multiverse repos enabled in your sources.list.

```
sudo apt-get update
```

---

### Post by nickoli_02 on 2007-02-23
Oh, the architecture identifier for AMD64 is x86_64, just so you know. In most cases you'll want the i386 libraries.

---

### Post by carverj on 2007-02-23
VERY informative response, thank you..
alas, i386 libraries still unavailable..
I do have libc6    libc6-dev     and libc6-i686 installed...
Oh, and there is a libc6-amd64 unchecked!! Perhaps that is the one I need ??!!

---

### Post by nickoli_02 on 2007-02-23
Possibly... but if wine depends on the i386 libraries it probably needs those libraries in particular. You can try just installing all the other stuff and see how far the build goes, but most likely it'll say you have missing dependencies. 

You should be able to download and build the libraries manually... I don't understand why you dont see them in the repos.

---

