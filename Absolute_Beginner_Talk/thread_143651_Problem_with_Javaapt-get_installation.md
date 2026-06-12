---
title: "Problem with Java/apt-get installation"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-03-12
Hi,

I attempted to install azereus following [this guide](http://www.ubuntuforums.org/showthread.php?t=75272).

Here is the error I am getting:

```
root@gibson:~# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate
```

I searched the thread and found 1 other person who mentioned the error, but nobody replied to them with a solution. What is the solution to this error? :-?

---

### Post by kaamos on 2006-03-12
Did you do the "sudo apt-get update". If yes, and you are still getting that error, you can download the package and install it manually. Open a terminal and

```
wget http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/java/sun-j2re1.5_1.5.0%2bupdate05_i386.deb
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
```

---

### Post by Kurt` on 2006-03-12
Excellent, works perfectly! :)

For future reference, what exactly would cause the error I received above? Was the package removed from the (I guess 'multiverse') repository?

And how would I go about locating the .deb files manually?

---

### Post by kaamos on 2006-03-12
I'm not sure. Packages.freecontrib.org is obviosly working just file, so if you added the line to sources and updated, I see no reason why it isn't found. You could try changing sources line to
> deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
Seems to be working fine for me.

---

