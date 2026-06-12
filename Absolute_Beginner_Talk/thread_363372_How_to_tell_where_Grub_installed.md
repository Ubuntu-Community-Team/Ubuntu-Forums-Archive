---
title: "How to tell where Grub installed?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by VraiChevalier on 2007-02-16
I installed a second hard drive and switched IDE cable and jumpers to make second hard drive Master and first hard drive Slave. First hard drive (Slave) has WinXP on it. Second hard drive (Master) is Ubuntu 6.06 install. 

Dual boot works GREAT! At start up Grub lists Ubuntu and WinXP wherein I choose.

My question is: Is the Grub installed on the Ubuntu (Master) disk? Is there any reason Grub would install on the WinXP disk? How may I check this?

I ask this because after doing much Forums reading about Grub I got the impression Grub would alter the WinXP MBR without warning. (This is why I changed my cables and made Ubuntu disk Master).

Everything boots fine and works well as far as I can tell. (Except for my darn printers:confused: )

---

### Post by louieb on 2007-02-16
You can tell GRUB where to install itself. Left to the default it alters the MBR of the master hard drive (hd0).   If you read hex you can use the dd command to dump the MBR (first 512 bytes) of both drives. If GRUB is installed in the MBR you will see a couple of messages GRUB would display if it were having trouble.  I've not done it so don't know exactly how.
Another way to tell is plug your XP drive back in as master. When you reboot It should go straight to XP.

---

### Post by ffifield on 2007-02-16
> Everything boots fine and works well as far as I can tell. (Except for my darn printers )

[http://www.linux-foundation.org/en/OpenPrinting/Database/DatabaseIntro]("http://www.linux-foundation.org/en/OpenPrinting/Database/DatabaseIntro")

This site has lots of great info on printers of all kinds.

---

### Post by PurplePenguin on 2007-02-16
Which printer do you use?  I always had headaches trying to get my Canon Pixma ip1500 working, but then found some .debs that got it going really quickly.  Works great now.

---

### Post by VraiChevalier on 2007-02-17
Thank all of you for your replies and great info. Much appreciated.

I am using a Lexmark Z11 and Dell A920 printers.

Still learning how to use Ubuntu/Linux and so have some more reading and study to do to try to get them working.

---

