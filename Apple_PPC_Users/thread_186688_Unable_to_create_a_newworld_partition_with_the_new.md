---
title: "Unable to create a newworld partition with the new graphical installer"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by jaumedejuan on 2006-06-02
Hi buddies this is my first post around here,

I think that this is a big BUG in here. After partitioning my disk with the custom mode, the installer warns telling that there isn't a newworld partition available to boot the system. Even though, there was a previous one that used to boot ubuntu 5.10

The I tried to reformat this partition located in /dev/hda2 with hfs using GParted (within the installer), but I would still get the warning.

The next step, has been to delete and create the partition, and this brought up another possible bug. The second stage of the partitioning scheme (where mount points are assigned) wouldn't recognize the new size of the partition. 

After cancelling the installation and starting all over, the new size of the partition was detected successfully but I keep getting the same warning asking me for a valid newworld partition.

The situation now is that the existing newworld partition has been destroyed without being able to create a new one. So I won't even boot the old 5.10.

As a temporal workaround, I could do with the good old ncurses-based installer, that allows me easily to setup up the newworld partition. I've checked all the boot modes from the desktop-live cd and I haven't seen anything that could allow me to do the ncurses installation.

Now I'm downloading the server cd, not sure if it's possible to do the ncurses install with this one.

Any ideas? Is there any proper way to create a newworld partition with GParted, so I can actually start the installation?

Ps: The Installer could also do with some "help" menu during the partitioning bit. Explaining the basics and what the process will do to the system. 
I known what I'm doing because I'm an experienced user, but every time I recommend somebody to try a linux distribution I always end up helping them out on the phone explaining what all the partitioning thing is about.

---

### Post by jobezone on 2006-06-02
I think the ncurses text install is the ISO file called alternative on FTP's . If you manage to make it work with the ncurses install, remember to report a bug against the ubiquity package in launchpad.net.

---

### Post by Ford Flox on 2006-06-02
I'm having the same problem. Ubuntu won't install, and no "newworld" partition can be created. Running on an Ibook G4.  I guess I'll look for alternative install modes.

---

### Post by sulobanks on 2006-06-02
I just told it to go ahead and install anyway when it got to that point and it worked fine for me.  I'm wondering if the error might simply be an errant error message.

---

### Post by Ptero-4 on 2006-06-02
It might just be that the new partitioner is shot.

---

### Post by yojimbo-San on 2006-06-03
Yeah, same problem here; the Live installer would neither locate nor create a bootstrap; my machine already had an Ubuntu bootstrap on it, although I'd blown away the actual Linux partition ...

Switching to the Alternative CD, and running an 'expert' install allowed me to create a boot partition, and use it. So all seems well.

I haven't tried booting OSX yet though ... sure it'll be OK, and if not ... well, I'll be installing MoL anyway ;-)

---

### Post by colinhayes on 2006-06-03
this is a recognised bug with the ppc graphical installer, there's a note on one of the main pages before you can download it.

just hit continue, you'll be fine... if there is a boot partition really.

---

### Post by EuroCity on 2006-06-03
Yes, the graphical installer definitely needs to be more powerful in the future: sofar, from the partitioning and formatting point of view, the Fedora Core 5 installer seems to be the best one, at least on the PPC...

---

### Post by kellogs on 2006-06-04
I had to use the Osx disc to create the newworld partition, once you have it, the ubuntu installer detects it and yaboot does it work and everything goes ok. 

Thats the problem with the ubuntu installer, it cannot create HFS or make newworld boots as far as I know. Maybe in a next installer version.

---

### Post by Sipheren on 2006-06-05
I am new to mac, would you be able to tell me how you made the 'newworld' partition, I am haveing the same problem trying to install ubuntu on my second hard drive on my G4.

---

### Post by colinhayes on 2006-06-05
[QUOTE=Sipheren]I am new to mac, would you be able to tell me how you made the 'newworld' partition, I am haveing the same problem trying to install ubuntu on my second hard drive on my G4.[/QUOTE]

do you have one hard drive or two?

---

### Post by Sipheren on 2006-06-05
I have 2, I have OS X 10.4.6 installed on the primary one and I want to install ubuntu on my second hard drive.

---

### Post by kellogs on 2006-06-06
cant help a lot if you want to conserve osx. I whiped it out completely (dont like propietary oses anymore).

What I did was, put the osx disc on the drive, reboot, press C key, wait a little, then from the tiger installation menu there is a disc utility. from there I created a little HFS partition, marked as newworld( in my case it takes 4 mb or so), then rebooted and installed again ubuntu disc. this time it recognized the partitions, even the hfs one as newworld mac).

Just to add, all this was with breezy a month ago, now with dapper everything should work better.

cheers.

EDIT: you will need to keep the newworld mac partition intact, and create the other partitions (root(type ext3) and swap(type swap)). just let ubuntu installer create root and swap in the free space or add them by hand. dont forget to mark newworldmac one as bootable if it does not recognize it.

---

### Post by jsonder on 2006-06-06
I wound up having to go back to the 1st Dapper beta, install the New World partition, etc.  on my mac mini.

I had decided to shrink the OSX partition to 9 gig while installing the final release of 6.06 (just enough to view videos, movies, etc.), and put the rest of the HD into Ubuntu partitions (NWboot, swap, /, and /home).

The partitioner with the release candidate and final release won't set up your New World partition.

John

---

### Post by nuke on 2006-06-06
I have also just finished messing around with getting the partitions sorted out.

I also used the Apple Disk Utilities from the OSX installer disk to create the partitions as the Disk Utilities can create the hfs+ and ufs partitions that I use for OSX and OSX swap partitions.

I did try Ubuntu-Desktop, Kubuntu-Desktop and Xubuntu-Desktop versions of gparted.  The only one that worked was Gnome partition/gparted in Xubuntu.  But as you already know it won't create the hfs+ partitions ... so I went back to the Apple installer disk.

---

### Post by ilhyfe on 2006-06-07
I had the same problem today, here' what I did:

1. Let the installer create the partitions itself.
2. Cancel the installer while it is copying files (at least after the partitions are created)
3. Start the installer and create the Partitions the way you like it. Then you'll find the "magic" HFS partition.

It worked with the normal installation CD.

But watch out: I wanted to use a XFS but I got a kernel panic while booting. I guess there aren't any AFS drivers in the initrd?! Ext3 worked fine...

Regards,

---

### Post by marc00o on 2006-07-18
I just wanted to add that I just went through this because of the erroneous, need a NewWorld boot partition of at least 819200 bytes.

I erased the good boot partition using the graphical installer's gparted, and was stuck with no way to get a boot partition back.  It's been years since I had OSX disks.

Turns out it is quite easy to create the partition from within the ubuntu live cd.

first using mac-fdisk to create the boot partition (menu option b)
  mac-fdisk /dev/hda
then use mkofboot to format the partition to hfs
  mkofboot -b /dev/hdaX (replace the X with what ever partition you just          made)

I had a hope that I could just make a yaboot.conf file (man yaboot.conf) and run ybin, so that I wouldn't have to wait for ubuntu to reinstall but this did not work.  A second installation of ubuntu found the Apple_boot partition I had just created and ubuntu installed ( I got the error again but clicked continue)

---

### Post by Bikerbob on 2007-07-27
Ok, I am trying to install Ubuntu on a G4 tower.

It already has OS X and OS 9 on it.. each on their own partitions.

they both boot fine..

SO would I not already have a Newwold bootstrap partition on it?

I have about 17 partitions on this drive... WOW.. hda 10 is swap at 500mb and hda 16 is a 9 gig partition for /

it accepts that fine, but gives this famous error, then crashes at the end of the install complaining it cannot find that bootstrap partition.

There are a tonn of tiny partitions on the drive.. 3 little 125mb hsf partitions.. but they dont have names.. 

Anyone help me with this??

James

---

### Post by pxwpxw on 2007-07-27
If you use the  Alternate install cd (text based menus) the partitioner should allow you to use and format one of those small (124MB ) partitions as New world boot partition, you just need to make the right selections, you can check results in the list the paritioner shows before finally writing to disk. I have done that sometimes, use the extra space to hold spare kernels sometimes. But that was on g4 ibook and g5. Cant quite remember if you have to change the partition type to Apple_Bootstrap in mac-fdisk first.
Edit:
Remembered, setting the Apple_Bootstrap partition type with mac-fdisk is the essential step.

---

