---
title: "Trouble installing (partitioning HD issue)"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by kpraytor on 2007-03-01
Ok, please have consideration for the fact that I am about as new to this as one can get. I just discovered Ubuntu yesterday morning. Been having problems with Vista on my new computer and the drivers are not back compatible so Ubunutu seems like a good option. Ok, enough of that: Whenever I try to install Ubuntu onto my computer, I get stuck on step 5 of 6, partitioning the hard drive.

I have read through a lot of the forums and I did defrag my hard drive twice before trying to install it, but to no relief! I have found quite a few solutions on the forum but I don't understand. Everyone keeps talking about going into a terminal (?) and putting in some code to figure out what's going on or wrong with the installer. I have no idea what this "terminal" is or how to use it! By the way, ya'll are great and thanks for all the help in advance!

---

### Post by rajeev1204 on 2007-03-01
hi

u r probably using the automatic partition option from live cd .That did not work for me either.

U should select manual partitioning option during installation. If u want to dual boot , then install ubuntu on a different partition, for example - if u have c and d partitions , install on d.

For example , when installing from live cd , gparted will show ur partitions as sda if u have sata harddrive etc. It will show windows partition as boot lba .***Do not touch this partition.***.This is where ur windows is installed.

The rest of partitions will be probably listed as sda5(extended) - or something similar.

Install to these partitions or create new parttitons on this . For example - if u have C and D partitions , U can split D into 3 more for storing root swap and media/home respectively.

After install is complete, GRUB bootloader will automatically detect windows and give u dual boot option

Also visit [www.ubuntuguide.org](www.ubuntuguide.org) 


regards

rajeev

---

### Post by kpraytor on 2007-03-01
Ok, I think I understand what I have to do to make the partitions that I need. That's not the problem, forgive me for being unclear. It appears that the installer is hanging up somewhere. A smaller indow pops up and tells me that it's scanning my hard drive or preparing my hard drive to be partioned or something. That thing appears to finish and then it tells me to pick automatic or manual partitioning but there are no options to choose from. The cursor was telling me that it was processing, but nothing happened for like an hour!

---

### Post by kpraytor on 2007-03-02
Someone please help me out. I really want ubuntu and ya'll are avoiding me like I'm the plague!

---

### Post by mahiyar on 2007-03-02
What I did was when moving from windows to linux is that before I started installing linux, I created empty space preferably contagious, this can be done by using Partiton Magic in windows, or by using "Gparted live cd boot disc" to create empty space (I guess it can even take care of NTFS partitions). This is a very good visual site for help in installation steps. [http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html)

---

### Post by rajeev1204 on 2007-03-03
hi

when u say it is preparing the hard drive , after selecting which option does it do that? automatic or manual partitioning?


Follow this -------> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by kpraytor on 2007-03-04
> **rajeev1204 said:**
> when u say it is preparing the hard drive , after selecting which option does it do that? automatic or manual partitioning?

Ok, after I click next on Step 4 of 6, the partitioner opens and is "detecting the file systems", then that small window disappears. At this point it tells me that I am on Step 5 of 6 and the pointer is telling me that it is still processing an does not change anything for over an hour.

Also, I have Vista on this computer and I cannot seem to find the Partition Magic or whatever it was called on my computer. If you have a general idea of where it would be on the Vista platform, please throw me a bone here! :confused:

---

### Post by tiki28 on 2007-03-04
Hi
This is not a reply so much, but a question. I have not tried yet to install Ubuntu, but I gather from this forum that during the installation process there will be a step to parition my disk drive. Will this allow me to have dual boot system (xp & linux)? tanks!

---

### Post by Jakkle on 2007-03-04
NEVER EVER EVER resize vista with a third-party linux jobbie. a new ntfs filesystem is incompatable so will destroy you! [or so i am told by t'internet...]  Go into 'manage disks' or some such in vista, and you can then resize safely, and create new partitions for ubuntu to go on.  remember to backup and take note of free space so you dont kill any files.  aalso, you dont have to reboot :)  [;inky linky]("http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php")
hope i am of service,
jack

---

### Post by annda on 2007-03-04
vista can resize partitions and it's a good idea to use its disk manager to do that. however, i'm pretty sure it cannot create linux ext3 and swap partitions - this is what you need.

so i'd suggest using vista to shrink its own partition and then boot with ubuntu cd again. if installing on the free unpartitioned space doesn't work, use the gparted live cd to prepare 2 partitions for ubuntu. you will be working on unpartitioned disk space then, so there is no danger to your vista files anymore.

---

### Post by Jakkle on 2007-03-04
could just make one big partition for Ubuntu and a small one for swap, then mount in Ubuntu installer. simpler IMHO.
jack

---

### Post by rajeev1204 on 2007-03-05
hmm

So it seems ubuntu has problems detecting the existing partitions and file systems on ur machine .Generally after it says detecting file systems , it will show all ur partitions.

Ok, this i cannot help u with.

COuld u provide exact details of ur system -  for ex. how many partitions , system configuration etc

Maybe its a vista thing .With XP , it isnt that much trouble if all ur partitions are FAT 32 .

HANG IN THERE 



regards


rajeev

---

### Post by jjalocha on 2007-03-05
Hi, maybe you can try this: when starting your ubuntu CD (desktop or altenate) press F6, and add the following to your kernel parameters:

```

   
pci=nomsi


```

By doing so, linux detected my previously invisible hard drive. I don't really know how it works, though.

---

