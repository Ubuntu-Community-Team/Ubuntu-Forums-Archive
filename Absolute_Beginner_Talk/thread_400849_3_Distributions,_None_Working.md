---
title: "3 Distributions, None Working"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Chang3 on 2007-04-04
Ok, today I got some old used laptop from a family member (its a dell latitude cpi with a pII) and since I've never tried linux before (didn't want to partition my existing hard drive) I decided this would be a great time to try linux. I installed Windows XP (with a 3.5 gb of 7 gb partition) and then decided to try to install linux on the remainder. I tried Xubuntu, DSL and Vector Linux. DSL booted from the CD but, like the other two, was unable to install. After deciding to install on the hard drive, each dist. would go through its own version of "checking for setup data", the cd drive would spin heavily, and then all of a sudden stop. I then decided to completely wipe the hard drive and try again without windows. nada. Do you think it's a hardware problem? (It's only got 128 mb ram)

---

### Post by devnulljp on 2007-04-04
Why not try a plain vanilla debian stable install? I put debian woody on an old compaq p2 laptop and it worked great....

---

### Post by carverj on 2007-04-04
Yup, know this problem well at the moment. DSL is probably the only distro which will be worth a try (not sure about vector) due to the lack of resources processor and memory wise. Found a good thread on google which I am attempting now, 
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=5;t=18048;hl=install](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=5;t=18048;hl=install)
You may need to register first.
Right now I am learning how to erase the hard drive so that I may install to HD

---

### Post by mojorising on 2007-04-04
Running pure Debian is a good option. It is pretty fast. If you like Ubuntu, I recommend xubuntu ([www.xubuntu.org](www.xubuntu.org)) since it is lighter and better suited to an older PC or one with low memory. 

A really good idea is to put your computer's model name in google with the word linux (e.g. "Compag x1234" linux) to see what other people's experiences are with Linux on that model PC. You may get really lucky and find someone has even set up a page detailing exactly how to get Linux going on it. 

It would be a good idea to give the make and model of the laptop here too in case someone reading your post knows something about your hardware and can help.

Mike

---

### Post by anaconda on 2007-04-04
one way to install is to do a "poormans" install of any knoppix based distro.. eg. DSL, knoppix, kanotix, cpx mini, and boot to that and do the hd-install from it. 

poormans install is just copying the CD-image to the hd and booting THAT from grub.

that is the only way I have succeeded to install linux to my old laptop without cdrom drive.

---

### Post by carverj on 2007-04-04
I tried to install DSL from Live CD after preparing hard drive with fdisk and mkfs commands from terminal.
A little window appeared, I pressed enter for the defaults, and it just dropped out and nothing happened.
So am going to try puppy linux. If that doesn't work, maybe the laptop just doesn't like linux!?

---

### Post by carverj on 2007-04-04
Nope, so I have a .iso image burnt to CD working fine on PC, but laptop not reading it!
idea's?

---

### Post by trishacupra on 2007-04-04
I just installed Xubuntu on an old machine with 128mb RAM successfully. The CD drive is very slow, so I couldn't use the live CD, but it installed with the alternative CD properly.

So my advice is to try Xubuntu using the alternative CD.

---

