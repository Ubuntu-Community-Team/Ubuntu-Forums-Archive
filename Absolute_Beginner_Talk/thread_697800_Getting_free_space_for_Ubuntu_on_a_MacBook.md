---
title: "Getting free space for Ubuntu on a MacBook"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2008-02-15
Hi!

I've just get a MacBook and now I'm looking forward to put Ubuntu in it, but the whole Hard Disk is "full" with Mac OS. So anyone knows any easy tool on Mac OS (very newbie on this OS) in order to get free space to insert the Ubuntu live CD and proceed with the classical installation so I'd have both Mac OS and Ubuntu?

First time I'm using Mac OS so please be slow :D

Thanks!!!!

---

### Post by James Little on 2008-02-15
try going to Applications > Utilities > Disk Utility. 

Then click on your hard drive on the panel on the left and select Partition from the options on the right. Click the + symbol to add a new partition (obviously you'll need a decent amount of free space available).

I'm not sure how you boot from the Ubuntu CD on a Macbook, but I think Google will be your friend there :)

---

### Post by fredscripts on 2008-02-15
Thanks for answering. I've been cheching arround but as that's a very dangerous stuff to do, I would like some "guided" process, I mean I've gone to Applications Utilities Disk Utilities, but can't really understand how to proceed, because what I want is to set the Mac Os partition to just 20GB, and the rest of the HD as free space, but not intuitive to do that (or I'm too newbie lol) and it's not a thing to play arround because I can crash the whole system.

So I'll be so grateful if someone could explain me how to proceed.

---

### Post by James Little on 2008-02-15
Do you have a lot of work etc. on the Mac? If not then it's really not that dangerous because you can restore OS X from the installation DVD that comes with the Macbook. If you do have work/musi/photos etc. then back them up first. 

In Disk Utility there is a "Size" box where you can set the size of each partition. Once you're happy with the sizes just click 'Apply'. Remember, Macs are designed to be simple to use :)

---

### Post by fredscripts on 2008-02-15
Thank you very much for answering. So if there is a Mac partition of 111.47GB right now, and I go to Disk Utility and on the size box I write like 80GB, it gives me 80GB of free space on disk? and then the mac space is only 31.47GB?

Another question, when I have free space, can I boot with the Ubuntu 7.10 live cd and proceed with the normal installation or I need to configure something as it is a mac?

Thank you very much!

---

### Post by fredscripts on 2008-02-16
Please, I really need Ubuntu installed on the MacBook in order to do college work. If someone could show me some steps to get 80GB of free space on the MacBook I would be very grateful. Also, I've tried to boot with Ubuntu 7.10 live cd and the Ubuntu installation screen didn't appear. Please I really need help on that!!! 

Thanks!

---

### Post by jrothwell97 on 2008-02-16
Booting from a CD on a Mac is done by rebooting, and pressing 'C' as soon as you hear the startup chime.

Depending on what file system Mac OS X is using (it may be HFS+, UFS or (?)ZFS) you should be able to shrink it. Alternatively, you might want to try running Ubuntu in a virtual machine, such as VMWare, or Q. (Q is a Cocoa port of QEMU - Wikipedia is your friend here.)

---

### Post by fredscripts on 2008-02-16
Thanks for answering. I'm on a MacBook with Mac OS X Version 10.5.2. So if I could boot from the Ubuntu 7.10 Live CD I could manage to get the mac partition (now with 111.47GB) down to about 30GB and get like 80GB of free space using gparted or something? or I need to use any Mac OS software?

Thanks!

---

### Post by eldepeche on 2008-02-16
You can use the diskutil command. Something like 
```

diskutil resizeVolume disk0s2 30G
```
should work. Then you can use the Ubuntu CD to create the new partitions you need. 

This worked for me in 10.4, I'm not sure if something's changed.

Afterward, you need to use rEFIt ro synchronize the partition tables. This site should be helpful:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by fredscripts on 2008-02-16
Thank you very much!!!

I've resized the mac os partition to 30G with the command you told me and I've installed refit following this link [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html) in Automatic Installation with the Installer Package. Now I can proceed with the normal installation of ubuntu through live cd isn't it?

Thanks again!

---

