---
title: "Networking Belkin Routerwith Ubuntu"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by James0044 on 2006-08-24
Day two of using Ubuntu, and today's problem is 'How do I install my Belkin F5D7000 Wireless-G Router on Ubuntu?' I called Belkin support who were quite unsupportive- 'we don't make any drivers for Linux, so you'll have to write your own'. 

As the only programming i've ever done was over 12 years ago, and on BBC Basic, that presents a bit of a problem for me.

Any help would be great!

Thanks 
James

---

### Post by benfindlay on 2006-08-24
Think your best bet is to download and install ndiswrapper from Synaptic Package Manager. It allows you to use your windows drivers for wifi cards in linux.

---

### Post by James0044 on 2006-08-24
Thanks!

Sounds like there is a solution! 
My Ubuntu PC has no internet access, but i have a laptop running XP with internet. Can i download it using that and copy across using a CDR? 

Also, how do i download ndiswrapper, and what is synaptic package manager?

Sorry, this must be very frustrating for you guys, but i am a complete ubuntu novice.

Thanks again,
James

---

### Post by James0044 on 2006-08-24
OK just found ndiswrapper. 
I'll give that a go.
Thanks!

---

### Post by benfindlay on 2006-08-24
Synaptic Package Manager is a program built into ubuntu that connects to the internet and allows you to get updates easily. It downloads and installs them for you (no need for tar, ./configure, make, make install etc) You just select them from  alist, right click and pick install package. It even sorts out all your dependencies and auto installs them along with the prog you're trying to install!

Its one of the main features that distinguishes ubuntu from many other linux distros.

Synaptic Package Manager = VERY USER FRIENDLY! ;) 

But I'm assuming you've got the tarball form os ndiswrapper. If so, just put it somewhere on your ubuntu pc, go into terminal and navigate to the directory its in (cd /dir/)

Then type this: ($ is terminal symbol)

$ tar -xfvz [ndiswrapperversion].tar.gz
$ cd /[ndiswrapperversion]
$ ./configure
$ make
$ make install

It's definitely worth setting up the internet on your ubuntu pc if possible. It'll make things a lot easier!

hope this helps

---

