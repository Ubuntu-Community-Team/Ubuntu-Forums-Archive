---
title: "need some info"
date: 2005-04-28
forum: Apple PPC Users
---

### Post by Digitallysick on 2005-04-28
I got a mac dual G5 2.0 ghz, wana install ubuntu on it, is there anywhere that has it step by step?? what are the advantages??

---

### Post by bored2k on 2005-04-28
[http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1)

Don't be scared of the non-GUI install ..

---

### Post by farruinn on 2005-04-28
[QUOTE=Digitallysick]I got a mac dual G5 2.0 ghz, wana install ubuntu on it, is there anywhere that has it step by step?? what are the advantages??[/QUOTE]
 If you just go with the defaults you should be ok.  I suggest doing the automatic partitioning (it puts in the boot partition in a logical place and gives you a reasonable amount of swap given your RAM).  It's pretty painless though.

---

### Post by az on 2005-04-29
[QUOTE=farruinn]If you just go with the defaults you should be ok.  I suggest doing the automatic partitioning (it puts in the boot partition in a logical place and gives you a reasonable amount of swap given your RAM).  It's pretty painless though.[/QUOTE]

Er...  By default, doesn't it wipe the first hard drive?

---

### Post by bored2k on 2005-04-29
[QUOTE=azz]Er...  By default, doesn't it wipe the first hard drive?[/QUOTE]
 [http://shots.osdir.com/slideshows/305_or/9.png](http://shots.osdir.com/slideshows/305_or/9.png)
[http://shots.osdir.com/slideshows/305_or/10.png](http://shots.osdir.com/slideshows/305_or/10.png)

It does so, watch out with clicking Next > Next > Next the Win style..

---

### Post by ssam on 2005-04-29
there is a howto at [http://www.ubuntulinux.org/wiki/InstallationHowToPowerPC](http://www.ubuntulinux.org/wiki/InstallationHowToPowerPC) it is slightly old but i dont think the procedure has changed to much. it may be a bit trick if you are new to linux.

you will have to back up all your data, as there is no way to install ubuntu on a mac with out wiping the hard drive. (unless you made the partitions you need when you installed mac os x).

do you want to have the machine dual boot between mac os x and linux?

if so you will need a minimum of 3 partitions.
512Mb - 1Gb for swap (linux uses a partition for virtual memory, rather than a file like mac os x)
a mac os x partition
a ubuntu partition

i am pretty sure it is not possible to resize HFS (mac filing system), so you will need to format you drive. the best way to do this is boot with the mac os x install cd, and go to file -> disk tool (its called something like that). make the mac os x partition (HFS+) with that, and leave the rest of the space free. then in the ubuntu installer you can make the ubuntu and swap partitions.

then reinstall mac os x on the mac os x partition.

then boot with the ubuntu install disk, and follow through that.

feel free to ask for help. do you have a spare computer? you could have someone talk you through the installation on IRC.

---

### Post by farruinn on 2005-04-29
Good point, I forgot about this.  If you want just Ubuntu on the computer, however, doesn't the installer create a bootstrap, /, and swap partition for you?  If not you can always select "customize" or whatever it is, delete the mac os x partition or whatever's there, then select the free space and do an "automatically partition" on that (which I know for sure will give you those three necessary partitions).

---

