---
title: "[SOLVED] Missing boot record on new hard drive"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by MrClark on 2007-12-29
I started out w/ Xubuntu 7.10 installed on a 4gb hard drive. Played around but decided I wanted to go w/ Ubuntu.

I installed a 40gb hard drive and mounted it in Xubuntu to copy some stuff off of it. No problems.

My plan was to install Ubuntu on the 40gb hard drive and then remove the 4gb drive to make space for a different, larger drive.

I booted from the Ubuntu live cd and installed Ubuntu on the 40gb drive (choose to use the whole drive for the installation). No problem.

Removed the 4gb drive w/ Xubuntu on it and tried boot Ubuntu from the 40gb drive. This is where I ran into trouble.

I got the message that the boot record missing from IDE-0.

I tried booting from the live cd and re-installing Ubunutu on the 40gb drive, but the drive is not detected or shown during the installation process.

If I reinstall the 4gb drive, I can choose to boot Ubuntu and it works just fine. 

What do I need to do to install Ubuntu on the 40gb drive and not need the 4gb drive w/ Xubuntu on it?

I've read some stuff that points to the bios settings for the 40gb drive as being the reason that it is not showing during installation. It is detected by the bios just fine. What should I change?

Any help would be much appreciated.

---

### Post by clayt0njknight on 2007-12-29
You need to make this drive the primary on the chain.  Some drive/motherboard instructions sets are funny about this.  I've ran into this many time with a few boxes i've built where i've removed the primary drive and it can't see the slave drive on the channel.  Goofy I know.  

The MBR is always stored on the Primary Drive on the Primary Channel (disk 0,0).  That's where the problem is.  if you stick that 4 GB drive back in it's going to boot a-ok.  But if you're going with a different drive...  i'd recommend simply making your 40 GB your primary and installing ubuntu on it.  Then put that big ole' second drive in you want to install, and use it for storage.  Hell, you can go as far as formatting it and mounting the entire drive as your <i>home</i> path...  in case you decide to wipe and reinstall Ubuntu or another flavor of linux even.

---

### Post by MrClark on 2007-12-29
Thank you very much for the quick reply Clay. 

I think I've tried that.

I've changed the jumper on the drive to master and I tried using the first IDE plug on the cable that the two drive were plugged in with.

Is there anything else I can try? (I'll try that again too)

As far as putting  my /home dir on the newer, bigger drive, that sounds like exactly what I need/want to do, but need to get over this hurdle first.

---

### Post by clayt0njknight on 2007-12-29
When you put that drive on primary channel, primary drive, did your BIOS find it?  If so you're in business.  Of course, you don't exaclty have access to the drive since you're still missing the MBR.  two ways around that:  boot your live CD and reinstall Ubuntu on that drive, or boot livecd into terminal and try to reinstall GRUB to that drive (not entirely sure of the process, in all honesty i'd just recommend the live CD/reinstall for convenience matters depending how down and dirty you wanna get with this.)

---

### Post by MrClark on 2007-12-29
I just tried again.

The BIOS has not problem detecting the 40gb drive but the partition step in the installation process still does not detect/show the drive.

Any ideas on what could be causing this?

---

### Post by clayt0njknight on 2007-12-29
What does the bios detect it as?  Primary Master, Slave; Secondary Master, Slave?

---

### Post by MrClark on 2007-12-29
Primary Master.

Thank you again for your time this evening!

---

### Post by clayt0njknight on 2007-12-29
Anytime pal.


If it's primary master your LiveCD should be seeing it.  Have you got the jumper on the drive set for master or Cable Select?

---

### Post by MrClark on 2007-12-29
Master. Was going to try Cable Select after the game if I can. Worth a try?

---

### Post by clayt0njknight on 2007-12-29
definitely worth a try.  some of those drives are goofy on their jumpers, printing labels upside down and such...  and offering what is called an "8 GB clip" option which just restricts the size of the drive to 8 GB of storage only...  makes no sense.  What game ya watchin?

---

### Post by MrClark on 2007-12-29
Pats Giants. Its not lookin good right now. Buts the Pats have been in worse spots before. We'll see. I hope to mess w/ the drive more after the game, but it may have to wait til tomorrow.

---

### Post by clayt0njknight on 2007-12-29
feel free to email me at [email]knight.clayton.j@gmail.com[/email] or [email]claytonknight@sprint.blackberry.net[/email] if it's tomorrow.  i'll hop online and we'll see if we can't get this goin.  I myself, however, and a Chicago fan :)


-Clay

---

### Post by MrClark on 2007-12-30
Using Cable Select worked!

---

