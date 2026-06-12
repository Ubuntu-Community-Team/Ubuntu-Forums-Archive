---
title: "installing ubuntu desktop live with only 128mb physical ram"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by dflives on 2007-01-03
hi im new to ubuntu. i recently installed a copy of the breezy badger onto my system and it worked like a breeze! needless to say without predefined installation restriction everything went smooth, everything that is to say the grub loader, which turned out to be quite annoying given that i want to boot directly into windows as the default option.
however this is not my concern anymore, since i have deleted this 5.10 installation to make way for 6.10 desktop live. since i had a swap drive of 500megs from the previous installation, i was able to get through the install without any lockups. alas this was not the case when i rebooted! i kept getting a frustratingly irritating grub 17 error with some reference to stage 1.5 or something. now at this point i was unable to load windows, forcing me to do a mbrfix through windows cd. after that i couldn't get the ubuntu install to run. i deleted everything in the ubuntu partition, and tried things over, which resulted in an endless loop as in above.
heres how my system is configured now :
---------------------------------------------------------------------------------------------------
hda1; windows xp 12gb NTFS
hda2; free space 10gb (previously with 500mb SWAP on extended partition with the rest EXT3)
hdb1; 20gb FAT32 (previously NTFS)
hdb2; 60gb NTFS


ubuntu version im using: ubuntu desktop live 6.06 
---------------------------------------------------------------------------------------------------

how could i get ubuntu to run with only 128megs ? if without a swap drive i try to install i cant even get to the desktop to install. on the other hand if i manually created a swap using something like knoppix live i am able to get the setup to finish at 100%, reboot and get the same grub error 17 as in above. ](*,) 

now i now there is an alternative version for download... but i can see a number of people stating a running ubuntu 6.06 or even 6.10 on 128 ram. can i possibly do the same thing with this 6.06 LTS? or is it even possible to update a system with the above configuration to 6.06 using apt-get, without having to update the ram??

pls pls help. every other forum has failed me :( 
any help appreciated in advance.

---

### Post by aysiu on 2007-01-03
Running Ubuntu on 128 MB of RAM is not the same as running a live session of Ubuntu on 128 MB of RAM while trying to install Ubuntu through a GUI on top of that live session.

You're not going to be able to do it. Sorry.

You need the Alternate CD. That will still install Ubuntu, but it will create a minimal session (with three-color, text-based graphics and no live session).

For Grub, you should install it to the MBR. There's a really easy way to make it to boot directly into Windows instead of Ubuntu.

---

### Post by dflives on 2007-01-03
what about this :

[http://cutecomputer.wordpress.com/2006/07/18/ubuntu-606-installation-on-legacy-pc-low-ram/](http://cutecomputer.wordpress.com/2006/07/18/ubuntu-606-installation-on-legacy-pc-low-ram/)

i have no idea what have of the things in that article means. and yet i was able to install 100% thanks to the existing swap drive. but it was on ly after the install that i got grub 17 error at stage 1.5. why do i see this?? is there a way to solve this?? since i already have a *disfunctional* ubuntu installed on hda2.


thx for the quick reply btw

---

### Post by MkfIbK7a on 2007-01-03
try to enlarge your swap space that may help...

---

### Post by macogw on 2007-01-03
> **wert613 said:**
> try to enlarge your swap space that may help...
It won't help.  The computer can only use up to 3X the amount of RAM you have.  With 128 MB of RAM, the usable swap maxes out at 384 MB.  

Install from the Alternate CD while we try to figure out what GRUB error 17 is.

Can you hit ESC on GRUB and tell us what it says the options are and look in them to see what partitions it's mapping them all to?  first partition on the first hard drive is (hd0,0), second partiton is (hd0,1) etc.  It starts counting at 0, not 1.

---

### Post by dflives on 2007-01-03
thx macogw.

but i've run mbrfix using windows cd. so i dont see grub or anything now; just plain boot into windows.
btw how can i fix the grub thing, and then go about your suggestion?

thx again mate. ;)

---

### Post by dflives on 2007-01-04
can anyone give a little help on how i could restore the grub menu, and then prevent it from displaying error 17. as i have stated previously, the installation was finished at 100 %. beats me how rebooting will give an error, since i have already setup up a swap space using installation screen 5 of 6 which was automatically making use of the first free space available to create a root partition and swap space. the one i had ubuntu make use of in the installation process was the swap space from the previous installation of 5.10. 

so now i have a complete ubuntu installtion which refuses to boot, windows fixed using mbr command and two swap spaces...

edit: i am now downloading an alternate copy of 6.10 which i plan to install if nothing else helps.

---

### Post by energiya on 2007-01-04
Hi,
I have 128MB RAM and tried the liveCD, but never managed to finish instalation (tried even with XUbuntu 6.10). So I installed from ISO (without burning a CD, loaded the iso from hdd) using the alternate version, and it worked perfect! And error 17...  I think that apperead once or twice, when I modified some partitions...

---

