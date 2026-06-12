---
title: "duel booting and partitioning"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by becklesfb on 2007-06-17
Dear Team
My friend has just introduced me to this new software, I am running Windows XP home edition on my system at the moment I do not wish to over write this Os, but desire to duel boot this copy of linux, I would appreciate some guidance as to how I can partition the free space on the disc, what it means to name a root director? what it is to mount the drive? and how to configure my hardware a well as my wireless internet connection.
I should basically say that I need my hand held until I become familiar with this Linux Os and any root commands that I may have to use with your help I may be able to come more proficient in using this Os and if this is as good as my friend has said then I may eliminate windows Os completely, thank you for your help in advance.

becklesfb

---

### Post by steveneddy on 2007-06-17
You could use the partitioning tool in XP or buy Partition Magic and use that to partition your HD.

Partitioning means to divide the HD into smaller parts, like cutting a pie.

Make a place for Linux and a swap partition, which you can do with Partition Magic.

OR, load the Ubuntu Live CD and use gparted to do this. It will cost you nothing and should be available on the CD.

Be sure you back up your important files from XP in case you bork something.

You will need at least 512 MB of installed memory (RAM) for Ubuntu run also.

This should get you started. Search the forums for dual booting and partitioning and there should be something there for you to read.

Educate yourself on every step from partitioning to installation. After you partition, restart Windows and see if everything worked well, then carry on to the next step.

Take small baby steps and fix problems as they come along and you should have a trouble free installation.

You also may try installing a second HD to install Ubuntu on. This may be the easiest way to get this done.

---

### Post by acowboydave on 2007-06-17
Hello I am new also, you might want to visit this site for a video on how to partition your hard drive. It's, [http://www.irongeek.com/i.php?](http://www.irongeek.com/i.php?) page=videos/soho-server-1-installing-ubuntu ,or you can also try Wubi 7.04 and install ubuntu 7.04 into windows and not even partition your hard drive. But you will have to download ubuntu 7.04 alternate. Put wubi and ubuntu in the same folder for the installation. One note it also uninstalls from xp in about 3 seconds if you run into problems. Defrag your disk first it really helps. wubi site is [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html).  Note: Irongeek, on the main page click the Hacking illustrated Videos and look for installing Ubuntu Linux Soho video.

---

### Post by bodhi.zazen on 2007-06-19
LOL

Partitioning is intimidating at first :)

Check this out : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)


AND YOU DO NOT NEED TO BUY ANY FANCY PARTITIONING SOFTWARE !!!!


use gparted. Gparted is included on the live desktop CD :

guide : Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

You can do all your basic partitioning and formatting from the command line, with fdisk :

[http://www.linux.com/howtos/Partition/partition-5.shtml](http://www.linux.com/howtos/Partition/partition-5.shtml)

BUT if you need to do more advance things like copying, moving, or resizing partitions, use gparted.

You may also look at gparted-clonezilla :

[http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/)

This is a live CD with gparted and clonezilla for all your partitioning needs, including backup.

---

### Post by buuntuu! on 2007-06-19
who's the team??
we're the community!! ;)

---

### Post by bodhi.zazen on 2007-06-19
> **buuntuu! said:**
> who's the team??
we're the community!! ;)

+1 on that sentiment.

I consider the community to be my "extended team" if you will. Some members choose to donate additional time focused on the forums and improving the experience of new users, thus the Beginners Team.

We are not an exclusive or elitist sub-group and all are welcome. We have a mix of new of experienced users on the them. The main criteria for joining the team is the willingness to commit some additional time to work with the team.

Drop on by any time, let me know if you are interested in joining the team.

[http://ubuntuforums.org/forumdisplay.php?f=215](http://ubuntuforums.org/forumdisplay.php?f=215)

~Please read the "Welcome" sticky~

---

