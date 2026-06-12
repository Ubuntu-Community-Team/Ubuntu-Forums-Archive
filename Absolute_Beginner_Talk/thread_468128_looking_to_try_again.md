---
title: "looking to try again"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ADH on 2007-06-08
I took a look at the 7.04 install, and selected manual.  I got as far
as being asked about mounting the partition I chose, and didn't
know what to select.  There were a bunch of options, including
root, home, /usr/local.  I think I want everything on that partition,
including Grub when I get that far.  Which mount options should I
use, and can I choose more than one before saying "Done?"

I have created two 6.5 gig partitions, plus a Swap partition, on the slave drive.
(eComStation, XP, and IBM Boot Manager are on the master.)

---

### Post by dmfield on 2007-06-08
If you set a basic system, / (root) and /wap should suffice, and everything will appear on the main partition. However if you add /home, on the second partition, what will happen is, your system files and all the linux os will install in / (root) and your (for want of a better word) My Documents, will be allocated to /home

the second option is good if you know you might bork your install up a few times, and you want to reinstall Ubuntu, as your /home partition will keep the files, if you use the same partitioning system.

Let me know if i can write this in easier terms, and i'll try to do so.

---

### Post by ADH on 2007-06-08
Easier terms would be helpful, if possible.  Thanks.  I know nothing of Linux, so this is all new to me.

---

### Post by ADH on 2007-06-28
I'll try /root on one partition, and /home on the other, I reckon.  So I don't need to mount anything else?

---

### Post by Rui Pais on 2007-06-28
> **ADH said:**
> I'll try /root on one partition, and /home on the other, I reckon.  So I don't need to mount anything else?

Hi,
 just to point 2 things. 
There is no /root, just /   
Root is the historical name for the "/", the place where you mount the Linux system. 
And of course it's not optional. You need it to do an install :) (sorry, don't know if you already know this...)

The other things are optional... but having a separate /home is a good practice, yes.

The 2nd point is a swap partition. It's convenient to have one. dmfield mention it but he have a typo, so maybe it's confuse. Installer will take care of format it correctly and mount it for use.

---

### Post by ADH on 2007-06-28
I know nothing, so all advice is helpful.  :)  I'm looking to custom install 7.04 to partitions on my slave drive.  I've formatted a Swap partition, and two 6.5 gig partitions for the OS, et al.

---

### Post by Rui Pais on 2007-06-28
> **ADH said:**
> I know nothing, so all advice is helpful.  :)  I'm looking to custom install 7.04 to partitions on my slave drive.  I've formatted a Swap partition, and two 6.5 gig partitions for the OS, et al.

You mean you formated manually, from outside installer? Great thats the way one learn.
Just be careful with swap. it needs to be in it's special format, not standard ext3 or other Linux filesystem type, ok?

Don't worry much. Just run the installer. It's much easier then one thinks at the beginning. Easier then Windows installation. 

The problems appear later, with use :lol: (sounds mean, he he but don't worry, we are here to help :))
The first thing to learn after install is what is sudo. Here the basic documentation:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


best of luck with your installation 
(i'm preparing to install Arch linux right now, just for fun :))

---

### Post by ADH on 2007-06-28
I formatted using the hard drive utility I use with OS/2.  I created a Swap partition,formatted as such, and the two other partitions are formatted ext/2.    I've been warned that the custom install may format those partitions itself, which is fine, and I now know to place Grub in the partition boot record, not the MBR (which is what killed me the first time I tried an install with 5.10.)  

I guess once I get past the mounting options, I'm close to finished?

---

### Post by Rui Pais on 2007-06-28
> **ADH said:**
> I formatted using the hard drive utility I use with OS/2.  I created a Swap partition,formatted as such, and the two other partitions are formatted ext/2.    I've been warned that the custom install may format those partitions itself, which is fine, and I now know to place Grub in the partition boot record, not the MBR (which is what killed me the first time I tried an install with 5.10.)  

I guess once I get past the mounting options, I'm close to finished?

Uhmm... You get yourself extra work. Installer will propose to format again those partitions (It's the default) and i advise you to accept. Is swap a correct type 82? do  you format partitions with ext2, but with journalizing (ext3)? 
Better start the installer and accept a reformat for those, to avoid  later problems.

God luck with your installations. Post on any problem.

---

### Post by ADH on 2007-06-28
The Swap is correct.  I got the details from the author of my partitioning software, which comes in versions for OS/2, Linux, Windows, and Dos.  The guy knows his operating systems and drives.

I'll let the installer reformat.

---

### Post by ADH on 2007-06-29
With all the help here and elsewhere (my drive software author also helped), I got it installed!  Grub is on the same partition as the root (/dev/hdb2), and eComStation was not killed, nor does it appear XP was.  /home is on /dev/hdb3 - both are formatted ext/3 by the installer.  I can boot Ubuntu from IBM Boot Manager, along with the other two OSes.

So, what do I do now?  What apps should I install?  I see loads of things in add/remove (though no SeaMonkey.)   I have no clue how to use Linux - I'm still more a command line guy than anything, even in eCS.

Can Ubuntu read a Fat16 drive?  I have my Firefox passwords and bookmarks there, which I'd like to copy to the Ubuntu version if possible.

Thanks,

---

### Post by overdrank on 2007-06-29
> **ADH said:**
> With all the help here and elsewhere (my drive software author also helped), I got it installed!  Grub is on the same partition as the root (/dev/hdb2), and eComStation was not killed, nor does it appear XP was.  /home is on /dev/hdb3 - both are formatted ext/3 by the installer.  I can boot Ubuntu from IBM Boot Manager, along with the other two OSes.

So, what do I do now?  What apps should I install?  I see loads of things in add/remove (though no SeaMonkey.)   I have no clue how to use Linux - I'm still more a command line guy than anything, even in eCS.

Can Ubuntu read a Fat16 drive?  I have my Firefox passwords and bookmarks there, which I'd like to copy to the Ubuntu version if possible.

Thanks,

Hi and welcome I believe ubuntu can read the fat16 files so that hopefully wont be a problem and you might want to check out this link.
[http://howtoforge.com/the_perfect_desktop_ubuntu7.04](http://howtoforge.com/the_perfect_desktop_ubuntu7.04)
Good luck and welcome again. ;)

---

### Post by Rui Pais on 2007-06-30
Congratulations for you well succeed installation :)

If i understand you well you have done the alternate CD installations and are now on console only with the base system and no Graphical server or session.

You Need to install X server and a Desktop Environment.
To install a full DE do:
```
sudo aptitude install ubuntu-desktop
```
to get Gnome or
```
sudo aptitude install kubuntu-desktop
```
to get KDE.
Here an article explain the differences:
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

Here some tips for installs from a base system:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)


good luck.
 
keep post on doubts and welcome to forum :)

---

### Post by ADH on 2007-06-30
I seem to have a desktop.  Nothing on it but two hard drive icons, but it is there.

---

