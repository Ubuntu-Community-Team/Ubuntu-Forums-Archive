---
title: "Installing g++-3.3 in Ubuntu 7.10"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by LinuxRedux on 2007-10-30
Hi,

I installed linux this morning, so far i've managed to get nvidia drivers working, my twinview set up, but i'm stuck at what would look like the most simple part. installing g++3.3

I enabled all repos in synaptic, and found the closest match to be g.3.4 which would not install due to missing packages.

Next I tried to download deb packages off a debian server manually. this worked for most of the depenancies, but libstdc5(devel) lists g++3.3 as a dependancy, and like wise, g++3.3 lists libstdc5(devel) as a dependancy, meaning i could not install either.

I saw that a way to overcome this would be to let ubuntu install it, but i can't for the life of me find a repo server i can add to synaptic that carries it or it's dependancies.

Can someone please point me in the direction of such a repo? Or any other method they know.

If it matters, it's for being able to run BlitzMAX Linux version, which uses the older compilers unforunately.

Thanks for any help you can give this confused and frustrated coder :)

---

### Post by Seisen on 2007-10-30
Try ```
sudo apt-get install g++-3.3
``` or if that won't work here is a link to the package itself on packages.ubuntu.com.

[http://packages.ubuntu.com/gutsy/devel/g++-3.3](http://packages.ubuntu.com/gutsy/devel/g++-3.3)

---

### Post by LinuxRedux on 2007-10-30
Hi,

thanks for the tips, but neither appear to solve my problem.

1) I have no repo to do an apt-get, they only have 3.4+ and even 3.4 doesn't install because there are missing packages.

2) Same problem as descriped above, g++3.3 depends on libstdc5(Devel) and libstdc5(devel) depends on G++3.3 so i can install neither, no matter of order.


Anything else I can try?

---

### Post by stchman on 2007-10-30
> **LinuxRedux said:**
> Hi,

I installed linux this morning, so far i've managed to get nvidia drivers working, my twinview set up, but i'm stuck at what would look like the most simple part. installing g++3.3

I enabled all repos in synaptic, and found the closest match to be g.3.4 which would not install due to missing packages.

Next I tried to download deb packages off a debian server manually. this worked for most of the depenancies, but libstdc5(devel) lists g++3.3 as a dependancy, and like wise, g++3.3 lists libstdc5(devel) as a dependancy, meaning i could not install either.

I saw that a way to overcome this would be to let ubuntu install it, but i can't for the life of me find a repo server i can add to synaptic that carries it or it's dependancies.

Can someone please point me in the direction of such a repo? Or any other method they know.

If it matters, it's for being able to run BlitzMAX Linux version, which uses the older compilers unforunately.

Thanks for any help you can give this confused and frustrated coder :)

gcc and g++ are installed by default in Ubuntu.  For Feisty and earlier you need to install the build-essential packages.  I believe for Gutsy build-essential is installed by default as well.

---

