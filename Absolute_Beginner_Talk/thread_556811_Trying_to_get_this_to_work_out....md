---
title: "Trying to get this to work out..."
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by BigFoofieMan on 2007-09-21
Hey everybody, Ive known about linux for a long time and have been trying to get into it and this is my perfect opportunity. 
The hard drive on my 6(?) year old dell (yeah, its old) died recently and I havent gotten a chance to go and order a new one. More like ive been lazy about it and not sure if i should even spend more money on this.

But the thing is... i had an Xbox hard drive laying around. Dont ask me how i got it and i'll tell no lies :-).
Instead of buying a new hard drive i was thinking of throwing Xubuntu on that hard drive and using the computer.
I think the hard drive is like 4gb but im not so sure.

Now the problem is that, when I go to install this hard drive, no information/hard drives show up in the "Prepare Partitions" section.

Now im not sure if this is because I installed the drive wrong or not, would you guys be able to help me out with it and see if the drive is working or not (through a command or something)

Sorry for the uber long post:)

---

### Post by SOULRiDER on 2007-09-21
It may be thata the xbox drive is not supported by the kernel? I dont know how xbox drives are different from regular hds.

---

### Post by BigFoofieMan on 2007-09-21
Its a western digital hard drive, I was thinking it should be alright.

---

### Post by matthew.lns1 on 2007-09-21
How did you connect the drive? If your drive is connected via usb type: lsusb . If the connection method is through pci: lspci should do the trick.

---

### Post by w4ett on 2007-09-21
Did you boot into your Bios setup manager and autodetect your new drive?...some of the older bios's don't autodetect at the POST (Power On Self Test) and need to be configured within the bios.  To enter into bios on your machine press one of the following keys or combinations of keys at boot:

> Dell® 400  	F3, F1
Dell 4400 	F12
Dell Dimension® 	F2 or DEL
Dell Inspiron®  	F2
Dell Latitude 	Fn+F1 (while booted)
Dell Latitude 	F2 (on boot)
Dell Optiplex 	DEL
Dell Optiplex 	F2
Dell Precision™ 	F2

---

### Post by oilchangeguy on 2007-09-21
aren't xbox hard drives locked?

---

### Post by matthew.lns1 on 2007-09-22
That would make sense.

---

### Post by w4ett on 2007-09-22
I did a little research, and there is a utility to "unlock" the drive so it can be used but (surprise, surprise) is runs in windows....but where there is a will, there's a way.  :p

[http://www.xbox-scene.com/articles/lock-hdd.php](http://www.xbox-scene.com/articles/lock-hdd.php)

There is also this reference wiki.

[http://www.xbox-linux.org/wiki/Xbox_Hard_Drive_Locking_Mechanism](http://www.xbox-linux.org/wiki/Xbox_Hard_Drive_Locking_Mechanism)

---

### Post by BigFoofieMan on 2007-09-23
I got the drive recognized but when the installer goes to partition the swap it fails, so im thinking its because of the lock right?

---

### Post by matthew.lns1 on 2007-09-23
Probably, You could try to get it to work using WINE. [http://www.winehq.com]("http://www.winehq.com")

---

