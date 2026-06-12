---
title: "Trouble extracting/compiling tar.gz sources"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by ascherjim on 2006-06-20
I've followed precisely (I think) all the various Linux books' instructions involving installing "build-essential" and extracting and trying to compile tar source programs, but nothing works.  I'm at a loss as to how now to proceed.  Anyone have any useful suggestions?

---

### Post by catlett on 2006-06-20
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) That guide is as good as it gets for an ubuntu how to.
You also have to remember it isn't all about compiling correctly. You have to have all the dependencies correct. There is no "standard" for linux. So the tar file you are extracting and compiling might not be compatable with your ubuntu system.

Only the software in the repositories are guaranteed to work on your system. Sometimes the tarball you are compiling is already a package in Synaptic. Always search synaptic package manager first before going for a tar file. The next thing you should look for after synaptic but before tars is a deb file.
A deb file is a debian file. It is a file made to be installed in a Debian system. Ubuntu is debian based so most, NOT ALL, debs will install no problem. But even debs can have dependency and non-compatability issues.

Don't know if any of this helped but I saw noone offered anything else.

Good luck.

---

### Post by aysiu on 2006-06-20
What program are you trying to install? Can you post a link to the .tar.gz?

---

### Post by ascherjim on 2006-06-20
Catlett:  Thanks for the excellent overview which I've found both reassuring and somewhat discouraging at the same time.  I think I'm a bit wiser as a result -- and perhaps even more successful.  Only time will tell!

Aysiu:  Thanks for your response also.  The source program I'm trying to experiment with is "xmahjongg" at http:/www.lcdf.org/~eddietwo/xmahjongg.

---

### Post by aysiu on 2006-06-20
Do you want *xmahjongg*, or are you just trying to learn how to compile from source... just to learn?

If you want *xmahjongg*, [enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install xmahjongg
``` If you're just trying to learn how to compile (just for the fun of it), try ```
sudo aptitude update
sudo aptitude install build-essential
cd ~/Desktop/xmahjongg-3.7
./configure
make
sudo make install
``` Assuming, of course, the extracted .tar.gz folder is on your desktop.

---

### Post by ascherjim on 2006-06-20
As you probably guessed, I was just trying to practice compiling from source.  (I was able to install the program from the repository.)  I had entered the commands essentially (but not exactly!) as you gave them, but with no result.  I was, though, uncertain as to whether I had extracted the source code correctly.  Tomorrow, I will try again.  Many thanks.  To the extent you'll still be interested, I'll post my results.

---

### Post by ascherjim on 2006-06-20
Aysiu:  Your code for extracting/compiling xmahjongg worked fine.  As I mentioned earlier, it was just a little different from what I'd earlier attempted, but apparently -- vive le difference.  Again many thanks.

---

