---
title: "How do i install ubuntu from the hard drive?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by harleycomrie on 2007-04-16
I have gotten the ISO of Ubuntu, extracted it and saved it to my new Linux partitioned part of my hard drive but I can't install it and every time i try it just says to put the CD in and restart the computer which I can't do. I can't burn it to a new CD or DVD because i don't have any can you please help?

---

### Post by bullgr on 2007-04-16
first you must burn the *.iso file to a cd and then reboot your pc from the cd...
after the booting is ready you can install ubuntu into hd.

there are many howtos for installing ubuntu.
see here... it's very detailed howto...

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu)

hope i help...

---

### Post by loserboy on 2007-04-16
the iso is made to be burnt onto a cd cuz it's an image, but I think they have made a version that can be installed from windows, maybe google it

---

### Post by bwhite82 on 2007-04-16
Try mounting the ISO file:

First, make a mount directory:

> sudo mkdir /media/iso

Then mount your downloaded ISO (replace myiso.iso with the filename of your ISO):
> 
sudo mount myiso.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0

And see if  you can install it that way. Not sure if that will work though.


EDIT: Ack! This is assuming you're running from Linux already. If from Windows, I have no idea.

---

### Post by Terl on 2007-04-16
> **harleycomrie said:**
> I have gotten the ISO of Ubuntu, extracted it and saved it to my new Linux partitioned part of my hard drive but I can't install it and every time i try it just says to put the CD in and restart the computer which I can't do. I can't burn it to a new CD or DVD because i don't have any can you please help?


Are you trying to run this via daemon tools or some other virtual drive?  If so it won't work that I know of.  Do you not have a cd or dvd drive?  If you have a drive but not a burner you can always ask for a disk to be mailed to you.

---

### Post by harleycomrie on 2007-04-16
im not sure how to create a mount directory

---

### Post by harleycomrie on 2007-04-16
Yeah im running from windows :(

---

### Post by Terl on 2007-04-16
Okay then, I found a place for you to start!  :popcorn: 

Go:  [Here to learn how to install from windows!!]("http://marc.herbert.free.fr/linux/win2linstall.html")

BTW, I found this by just typing "install ubuntu from windows" into google :guitar:

[Edit]:  Also found this interesting link:  [http://sourceforge.net/projects/instlux]("http://sourceforge.net/projects/instlux")  It claims to be a program that runs in windows and will install linux for you.  The screenshot shows ubuntu installation.  Worth checking into...

---

### Post by bodhi.zazen on 2007-04-16
Hmm ...

That is not how one normally installs Ubuntu ...

See here for an install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Or this : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you want to install from the iso, it is possible, but it is a little more advanced : 

[http://ubuntuforums.org/showthread.php?&t=316093](http://ubuntuforums.org/showthread.php?&t=316093)

HTH

---

### Post by harleycomrie on 2007-04-16
> **bodhi.zazen said:**
> Hmm ...

That is not how one normally installs Ubuntu ...

See here for an install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Or this : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you want to install from the iso, it is possible, but it is a little more advanced : 

[http://ubuntuforums.org/showthread.php?&t=316093](http://ubuntuforums.org/showthread.php?&t=316093)

HTH

thank you

---

### Post by loserboy on 2007-04-16
this is actually what i was talking about
[URL="http://ubuntuforums.org/showthread.php?t=396526"]
Wubi[/URL]

but I haven't tried it and I don't know anything about it.

---

