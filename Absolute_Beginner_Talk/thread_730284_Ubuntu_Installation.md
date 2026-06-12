---
title: "Ubuntu Installation"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Noob1234 on 2008-03-20
Hey guys,

I have a live copy of ubuntu and I have been playing around with it and now I wish to install it. Im a huge noob when it comes to Ubuntu but I wish to learn. Please help me out with my following questions.

Im running a MacBook with a core 2 duo processor.

1. I want to partition my disk to give an amount to ubuntu only, and if anything goes wrong with ubuntu it wont mess with my more important stuff (using ubuntu for general web browsing and fun). I have music etc on my current unpartitioned disk, how safe is it to create a partition as of now? What is the probability of me losing information? Will Ubuntu create a partition during installation if I want it to? How should I create the partition?

2. When should I install the program to allow me to select between ubuntu/OSX at startup? Before or after Ubuntu installation?

3. When running ubuntu on my live cd I have no internet connection. What program should I use and when should I install it? How should I install it? Same goes for touch pad problems, cant scroll using two fingers and cant right click, how should I fix those problems after installation?

I think thats all of my questions for now, I would appreciate some help. I do know of and have read the wiki but some of it I simply didnt understand. Please dumb down the process for myself.

Thanks A lot.

---

### Post by Noob1234 on 2008-03-20
BUMP anybody willing to lend a hand?

---

### Post by scramasax on 2008-03-20
> **Noob1234 said:**
> Im running a MacBook with a core 2 duo processor.

1. I want to partition my disk to give an amount to ubuntu only, and if anything goes wrong with ubuntu it wont mess with my more important stuff (using ubuntu for general web browsing and fun). I have music etc on my current unpartitioned disk, how safe is it to create a partition as of now? What is the probability of me losing information? Will Ubuntu create a partition during installation if I want it to? How should I create the partition?

My Mac is PPC, so I haven't done this, but you can, apparently, partition the disk for dual booting with Boot Camp Assistant.  However, you don't need to: Disk Utility is fine for the purpose, as is diskutil at the command line.

I couldn't tell you if the Ubuntu installer can itself re-size an HFS+ partition.

> 2. When should I install the program to allow me to select between ubuntu/OSX at startup? Before or after Ubuntu installation?

You *can* install a program called rEFIt, but you don't need to.  AFAIK, you would need if if you were triple-booting.

> 3. When running ubuntu on my live cd I have no internet connection. What program should I use and when should I install it?

That's surprising.  How are you connecting?  If it's through a NAT router, there's no drivers or anything involved; it should just do it, and there's nothing to install.  I wouldn't rush into installing until you sort out the reason for that.

> Same goes for touch pad problems, cant scroll using two fingers and cant right click, how should I fix those problems after installation?

I doubt that's going to work.  It's a pretty specialized thing that that touchpad has been designed to do.  Ubuntu's a pretty general-purpose OS that hasn't been written for any specific hardware, although it does, and necessarily has to, support quite a bit.

> I think thats all of my questions for now, I would appreciate some help.

Sorry I can't help much.  I expect there are a few people who are dual-booting with OS X on a new Mac.  People like to experiment after all.  But I doubt there are a lot.  I hope the question stays high up long enough for someone who has done it to see it.  Otherwise, you might try googling.

---

### Post by Noob1234 on 2008-03-20
Thanks for the help, anybody else?

---

### Post by Sef on 2008-03-20
> I couldn't tell you if the Ubuntu installer can itself re-size an HFS+ partition.

[GParted]("http://gparted.sourceforge.net/features.php") and [Parted Magic]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.VisParted") partially.

---

