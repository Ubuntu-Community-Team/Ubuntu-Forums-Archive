---
title: "Installation HELP plz!!!"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Amalgamayne on 2007-07-24
Hello:

This is my first time switching over to Linux after working with windows for a long time, and I need some help with installing the desktop version of ubuntu 7.  I can get the start screen to show, but when I choose to start and install from the menu, I get one of the following results:

---i get this message: can't access tty: job control turned off - and I have no idea what to do from there.

---the install will go to a black screen and just sit there, doing nothing

---the install will start, but then the computer will make some noises while the installation loops, doing nothing of interest.

I am trying to put ubuntu onto a slightly older computer (AMD 1000 MHZ, 6GB HD - has windows ME on it, which is why I want ubuntu) that a received from a friend.  I need this to be a computer that I can use to work with and be a stable backup for my laptop.

Thanks in advance! :)

---

### Post by Koybe on 2007-07-25
To install on old computers, you'd better get the alternate version cd.
[http://ftp.belnet.be/packages/ubuntu/releases/7.04/ubuntu-7.04-alternate-i386.iso](http://ftp.belnet.be/packages/ubuntu/releases/7.04/ubuntu-7.04-alternate-i386.iso)

It's a text mode installation so it's not as nice as the desktop cd during the installation but it needs less ressources and once installed it's all the same.

---

### Post by Amalgamayne on 2007-07-25
Hello again:

Thanks for your help, but I am still having trouble installing. I am using the alternate CD and the install proceeds fine until it gets to the point where it loads the floppy module.  At this point, it just hangs and does nothing.

I use Ctrl + Alt + F4 and here is what it says:

kernel: [ numbers, more numbers] hdd: lost interrupt.


If anyone knows what I am doing around or how to get around this, it would be greatly appreciated.  Thanks!

---

### Post by Koybe on 2007-07-26
It's seems to be more a hardware issue.
hdd is the slave device on your second IDE port. Take a look at this device. If easy replace or deconnect it.

---

### Post by Amalgamayne on 2007-07-26
How would I take a look at this?  I have no idea where to start looking.  Thanks for your help!

---

### Post by Amalgamayne on 2007-07-28
I have abeen trying furiously the past day and  a half to fix this, and still no luck.  I pulled out the floppy drive, changed bios settings to try to make the computer ignore the floppy drive, and also tryed to find irq settings to try to figure this out, and still no luck.  I even removed the bios battery to reset it and still no luck.  If anyone else has any ideas about this, I would feel greatly relieved! Thanks.

---

### Post by Amalgamayne on 2007-07-31
Hello again:

Here's a new error message for anyone who's watching this thread:

Buffer I/O Error on device fd0, logical block 0

Can this be fixed?

Thanks for your time!

---

