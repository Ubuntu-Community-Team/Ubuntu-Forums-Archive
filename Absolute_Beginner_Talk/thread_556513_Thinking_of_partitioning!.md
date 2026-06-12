---
title: "Thinking of partitioning!"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by liamwithers on 2007-09-21
Hi, I'm thinking of partitioning my hard drive so that I have Ubuntu and something else. Is it possible for me to install another Linux Distro? If so, what do you recommend as the best Linux Distro?

If I was to do this, please could somebody give me a link to a simple guide or tell me themselves how to do it. I done it with mums boyfriend on his windows pc, we used Alcohol 120% but how do I do this on Ubuntu?

Thanks In Advance, 

Liam

EDIT: And I don't want something too extreme that would use a lot of memory. I want something popular like OpenSUSE, fast and doesn't use up much memory.

Only have 1.5GB from my 10 gig hard drive left.

---

### Post by bodhi.zazen on 2007-09-21
You can partition with gparted, run from a live CD though : 

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

1.5 Gb is too small for most medium to full sized distros like SUSE

Check out distrowatch [http://distrowatch.com/](http://distrowatch.com/)

Check out something like Puppy linux

---

### Post by liamwithers on 2007-09-21
I don't get it. Gparted is an ISO image. Don't I need a program to burn ISO Images?

---

### Post by mysticmatrix on 2007-09-21
> **liamwithers said:**
> I don't get it. Gparted is an ISO image. Don't I need a program to burn ISO Images?
Under Ubuntu, right click the iso --> Burn. Tad easy! :guitar:

---

### Post by bodhi.zazen on 2007-09-21
> **liamwithers said:**
> I don't get it. Gparted is an ISO image. Don't I need a program to burn ISO Images?

Gparted is included on the Ubuntu live CD, so no need to download or burn anything.

the gparted live CD is a newer version though and has some additional features.

---

### Post by liamwithers on 2007-09-21
I think I might get Damn Small Linux. But how do i partition, somebody please help!

---

### Post by LowSky on 2007-09-21
Use gparted... its easy to use..

WOW 10gig drive... thats like 9+ years old.. I'm supprised the drive is still running.

You could by a new hard drive for $50 now and have over sixteen times the space

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075")

---

### Post by liamwithers on 2007-09-21
Now I have read, I don't want Damn Small Linux because it doesn't have support for flash or java. Does anybody know of a distro thats around 300mb with Firefox, flash and java support because that would be ideal. Thanks, Liam.

---

### Post by rich.bradshaw on 2007-09-21
You can likely install flash + java afterwards... remember Windows doesn't have native support for those things either.

---

### Post by liamwithers on 2007-09-21
Ok Thanks, will stick with Damn Small then :D

How do I install Gparted?

Think its going to work. Trying sudo apt-get install gparted

it seems to be doing the trick ;)

EDIT: AGHHHH! I need root privileges to do it. How do I do this? Root always winds me up!

---

### Post by SpiritIsReality on 2007-09-21
howdy
this work?
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)
partitioning:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

trails

---

### Post by liamwithers on 2007-09-21
Sorry, I really don't understand the partitioning there. Can't make a word out of it.

How do I access Gparted as root? Thats the only way it will run. It says it wont let me run it because Gparted can be a weapon of mass destruction. I didn't think it was a nuclear bomb lol but thats what it said.

---

### Post by bodhi.zazen on 2007-09-21
You should do your partitioning from a live CD as you can not resize a partition if it is mounted (in use).

Gparted is very easy to use.

Open a terminal and enter :

```
sudo gparted
```

See the link I gave you for full documentation, here it is again :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by liamwithers on 2007-09-21
Ok, got it up and running, and read a little bit of that documentation. Do I have to unmount first for it to let me make a partition? And what would happen if i unmounted? Would anything wrong happen? Sorry, I point out I'm 13 lol.

---

### Post by tenjin1 on 2007-09-21
> **bodhi.zazen said:**
> You should do your partitioning from a live CD as you can not resize a partition if it is mounted (in use).

Gparted is very easy to use.

Open a terminal and enter :

```
sudo gparted
```

See the link I gave you for full documentation, here it is again :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Hi liamwithers

You will have to boot from the liveCD and use GParted, because you cannot partition or resize the volume you are logged into, as bodhi pointed out. Booting into the liveCD, you will not be in the hard drive that you want to work on, but on the CD itself rather.

---

### Post by liamwithers on 2007-09-21
Wicked, thanks a bundle for that. Really helped ;)

---

