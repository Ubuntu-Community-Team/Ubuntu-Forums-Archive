---
title: "How do i install ubuntu in my second HD???"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by warrior85 on 2005-12-12
I have two hard disk and in HD0 i have Window$ and in the other i would like to install ubuntu 5.10. i put the install CD in the Cd drive and i restart the PC and then i press F1 and a menu pops up, then i freeze because i don't know in what HD i'm installing it and i don't want to loose the info i have on the first HD. So my question is .... how do i install it (step by step)???? on the secon HD. :confused:?????? (i',m new at this!!!!)

thanks!!!

---

### Post by Sutekh on 2005-12-12
At some stage of the isntallation you will get the chance to choose how you want to partition your disc.  There are several ways to determine the disc you want to install on.  

Firstly, how are they plugged onto your motherboard, are they IDE or SATA?  
What is their manufacture, are they seagate? western digital?  
What is their size?  

These should help you differentiate the difference between your hard drives.  

Then we can help with the actual installation (but tell us your hdd info first)
There are lots of good graphical guides (with photos of the installation) that will help immensly

---

### Post by warrior85 on 2005-12-13
Thanks for the information.... both HD are IDE, 40 GB and both are Maxtor.
I'm interested in the graphical help. I think i'm sharing my e-mail address but here it is anyway: [email]warr_85@yahoo.com[/email]

Thanks again.

---

### Post by Sutekh on 2005-12-13
Both are the same huh?  How are they connected to the main board? Do you know which is the master and which is the slave? And what's on them?

If not, that's okay, the installer has a dead easy partitioner, which will identify the master/slave, and the formatting of the disc.  So if your first (Windows) disc is formatted NTFS and the second has nothing, it will be clear to see.

Here are some graphical guides for installing Ubuntu.  

[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

Go down to the picture with "8th ntfs" underneath, those next steps are for the partitioning.  You should have something similar, just with an extra line for your second hard dirve.  If you know which drive is the master and which the slave AND/OR you know the formatting between drives is different, then here you will be able to tell which is which and select the correct disc for formatting.

There are similar sections in the other guides aswell.  

NOTE: The first guide chooses to "manually edit the partition table", the second and third guide let the installer do it automatically.  The auto-partitioning is good so long as you are sure which disc to do.

Read them all and get familiar with the process, it makes it easier when you actually go to do it.

_The other guides:_

[http://www.mrbass.org/linux/ubuntu/install/]("http://www.mrbass.org/linux/ubuntu/install/")

[http://www.ccs.neu.edu/home/jabra/breezy-docs.html]("http://www.ccs.neu.edu/home/jabra/breezy-docs.html")

Also if you like; start the installation, get up to the step where it lists the discs you can install from, write them down and we can help you choose the right one (you may have to abort the installation, but that's not a problem)

---

### Post by warrior85 on 2005-12-13
thanks... that guide was helpfull... it really helped me :razz: 
thanks.  but now I'm having another problem ... my problem is that I don't know how to install new applications.  Let me explain, I went to a cyber and i downloaded a game to my flash memmory (Frozen bubbles). When i came home i didn't know what to do... I doble clicked the icon and nothing happened when i clicked execute, it just worked in text mode, then i gave up went to the cyber again and post another thread.... if you can help me it will be great... :D  thanks.

thanks again for helping me how to install it. :razz:

---

### Post by cstudent on 2005-12-13
I think Frozen bubbles is in the repositories. Open they System Menu>>Administration>>Synaptic Package Manager and then search for it.

---

### Post by Sutekh on 2005-12-13
Glad to hear that you isntalled Ubuntu no problems.

Yeah I'd check Synaptic for Frozen Bubbles.  Synaptic is really easy to use.  Especially since Frozen Bubble requires some extra packages to be installed, Synaptic will do this for you as well.

---

### Post by warrior85 on 2005-12-13
ok, thanks again... i will try synaptic. if i have another question (and i'm sure i will) i will post again.... thanks:smile:

---

### Post by warrior85 on 2005-12-13
Told ya I'll be back... ;) 
I did what you said, and i went to the synaptic.  then a window pops up asking for my root password, i wrote it.... and then nothing happened :???: 
the same thing happened when i click on add application in system >> adminstration... nothing happend. :confused:

---

### Post by Mustard on 2005-12-13
Its asking for your user password, not your root password.

---

### Post by Sutekh on 2005-12-13
Have you tried running Synaptic from a terminal...

```

sudo synaptic

```
Are there any errors following this command?

---

