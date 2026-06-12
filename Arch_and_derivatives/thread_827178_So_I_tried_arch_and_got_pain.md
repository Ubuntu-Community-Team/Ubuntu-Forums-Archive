---
title: "So I tried arch and got pain"
date: 2008-06-12
forum: Arch and derivatives
---

### Post by Twitch6000 on 2008-06-12
Well before I get bashed to death first let me say i kind of liked the installition of arch it seemed a bit easier then what I normally go through.
Now what I did not like was I tried was to make it dual boot with windows I seen it had an option to install on a partition.I did that and hey it went a ok.I did all the other stuff next thing I know when I restart it says error loading operating system.So I use gparted to see what might cause the issue and I seen windows was gone and arch had no boot flag =[.
So I lost my windows and I am at my moms with no ubuntu(downloading now).
I finally did install arch perfectly.Although next thing I seen was a login screen and i am like WTF I was never given a place to do such thing(execpt root).
So can someone please help me?This is starting to seem like one hell of a pain.I thought it would be fun ,but it isn't :(.

---

### Post by chucky chuckaluck on 2008-06-12
> **Twitch6000 said:**
> Although next thing I seen was a login screen and i am like WTF I was never given a place to do such thing(execpt root).

i'm not sure what you mean by this.

---

### Post by Twitch6000 on 2008-06-12
> **chucky chuckaluck said:**
> i'm not sure what you mean by this.

What I mean is i never seen a place to put a password for log in,execpt for root.(during the installition thing)

---

### Post by Barrucadu on 2008-06-12
Did you read the beginners guide? There is only a root user by default, you have to add others yourself.

---

### Post by chucky chuckaluck on 2008-06-12
dude, i think barrucadu has hit the thumb on the nail. my guess is that you just need a little more time with the installation guide (easily glossed over in all the excitement). i'm not exactly mr. thorough, but i managed to get it done. there's more detail than ubuntu and you have to be a little patient, but the info is all in the documentation.

---

### Post by cardinals_fan on 2008-06-12
Follow the beginner's guide religiously and you should do okay.

---

### Post by mips on 2008-06-13
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by K.Mandla on 2008-06-14
> **cardinals_fan said:**
> Follow the beginner's guide religiously and you should do okay.
Amen.

---

### Post by crimesaucer on 2008-06-18
> **Twitch6000 said:**
> Well before I get bashed to death first let me say i kind of liked the installition of arch it seemed a bit easier then what I normally go through.
Now what I did not like was I tried was to make it dual boot with windows I seen it had an option to install on a partition.I did that and hey it went a ok.I did all the other stuff next thing I know when I restart it says error loading operating system.So I use gparted to see what might cause the issue and I seen windows was gone and arch had no boot flag =[.
So I lost my windows and I am at my moms with no ubuntu(downloading now).
I finally did install arch perfectly.Although next thing I seen was a login screen and i am like WTF I was never given a place to do such thing(execpt root).
So can someone please help me?This is starting to seem like one hell of a pain.I thought it would be fun ,but it isn't :(.


Try following this 10 page, step-by-step guide that has pictures for most of the important parts: [http://www.raiden.net/?cat=&aid=276](http://www.raiden.net/?cat=&aid=276)  


...also, when you do your install, make sure to read (and follow) any "notes" that pacman prints out... 


A few more tips- if you have a bcm43xx, the newest kernels don't support the old drivers of fwcutter and ndiswrapper, you need to use the newer b43:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[http://wiki.archlinux.org/index.php/Wireless#b43](http://wiki.archlinux.org/index.php/Wireless#b43)

... I just re-installed Arch and ran into this problem with the new testing kernel.

- my other tip is that you might need to install a package called synaptics: [http://wiki.archlinux.org/index.php/Synaptics](http://wiki.archlinux.org/index.php/Synaptics)

in order to make you mouse work.


and from that guide, this is the part about your password: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7)

---

### Post by LookTJ on 2008-06-20
> **cardinals_fan said:**
> Follow the beginner's guide religiously and you should do okay.

This covers my post for now:D

---

