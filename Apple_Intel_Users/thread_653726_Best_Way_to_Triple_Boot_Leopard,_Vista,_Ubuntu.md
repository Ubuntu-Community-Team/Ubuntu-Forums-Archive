---
title: "Best Way to Triple Boot Leopard, Vista, Ubuntu?"
date: 2007-12-30
forum: Apple Intel Users
---

### Post by escapedspecimen on 2007-12-30
Hi all, I have a had a pickle of a time setting up Leopard...with my triple boot setup.





I am curious if I went about it "properly"or if there is a better way.



Use instructions at your own peril if you wish. I am not responsible for errors or any problems you may have by using my instructions. This is my individual experience. *I am happy if this works for someone* struggling to set up a triple boot, but am posting this more so to see if there are any improvements to be made, or mistakes that need correcting to this method... 



I had an Intel MBP (SR) with 3 partitions. Tiger, Vista and Ubuntu but when trying to install Leopard it said it would not install and I would have to change my drive to guid partition scheme. 



So, through trial and error this is the only way I could get it to work.Keep in mind I started from scratch with vista and ubuntu, but did make a backup of my tiger drive.



1. BACK UP

2. Wipe everything and repartition internal disk to guid partition map and 1 partition. Install Leopard. 

3. Use either disk utility or carbon copy cloner(my purchased copy of SuperDuper is +still+ not able to do what CCC, a free program can do,apparently because they are trying to figure out time machine and are holding up a leopard compat. version, uuughh, but thats a different post...) to clone Leopard to *external* drive that is set up as *GUID* partition scheme.Make sure you are able to boot this external.

4. Wipe internal, repartition to 3 partitions using disk utility and *MBR* partition scheme in this order from top to bottom(in disk utility partition gui);

  a. Leopard partition: OSX extended journaled

  b. Vista partition: I think there is only one option: maybe Fat? Just make sure you select "windows" format (The vista installer will need to reformat this during install anyway)

  c. Ubuntu partition: "Free Space" 

5. Then to install leopard, (which apparently won't +install+ on a drive set up as MBR partition scheme, but that is what we formatted the internal drive as anyway) clone the external copy of leopard to the internal OSX partition we just made.

6. Then install vista by booting from install cd. During install you may have to reformat the Windows partition using the windows installer, but it should install fine after that.

7. Then Install ubuntu using live cd/dvd to the internal free space partition, splitting/ formatting the last partition using the ubuntu install/partition tool on the "manual"partition mode(make sure you are using the correct free space partition. I confirmed this by looking at the sizes of the partitions that showed up): "free space" into root and swap partitions if you want. I used ext2 for root



     *Side note:*If you have the same MBP as me you may have to change some setting when booting the live cd: Once the cd loads and you get to the preliminary menu window, press F6 to edit. A command will show up on the screen: You have to erase the last two words starting at "quiet" till end. Then write "all_generic_ide" in their space, keeping all of the command before quiet.  then press enter. It should then load to the ubuntu desktop where you can click on the install icon.(this took me a long time to figure out. I have also have to do this everytime I want boot into ubuntu, which stinks. Anyone know how to resolve this? (Linux masters?)



8. boot into osx and install rEFIt



*Issues:*



1. My Leopard partition is not showing up in OSX's startup disk pane in sys pref. but it is booting/ showing up as if it was, if having trouble, try holding option key during startup. 



2. I have also had a few issues with rEFIt not starting up as default menu, but when holding option key at startup it will show up. Then gives me the option of OSX, Vista or Ubuntu once selected. 



3. And the command thing with ubuntu at every startup I mentioned earlier.Is there a way to write all_generic_ide as a default or any other way to fix this?



If anyone has a better way of accomplishing this please let me know. I got to this point through a lot of trial and error and I'm not sure if there is a more stable/better way for a triple boot setup...



I would like for the Leopard partition to show up as the osx startup disk in the pref pane, but regardless it is still working. 



Correct me if I'm wrong, but it seems boot camp makes the drive into an MBR partition scheme anyway, so I'm curious what others who were already running dual or triple boot, boot camp systems had to do when upgrading their boot camp setups from tiger to leopard. Did it not allow you to install to the MBR partition scheme made by boot camp? Did you have to start from scratch as well?



Thank you in advance for your patience and support.

---

### Post by Infinite Recursion on 2008-03-22
I had a similarly difficult time triple booting my MacBook, but finally found a way that works flawlessly (at least for me).  I have a MacBook C2D, and am using Leopard, Vista, and Gutsy x64.

To triple boot, I took cues from the guide found here: [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu) and modified it a little.

I used Disk Utility to partition my HD, as I am not opposed to reinstalling an OS (I have done so probably more times than anyone has a right to =P )  I used the GUID partition scheme, and installed Leopard and Vista normally, and enabled rEFIt through Mac OS X

I then went through the Ubuntu installer as normal, and at the end, under Advanced Options, unchecked the "Install Boot Loader" box.  Once the installer finished, I opened a terminal (still in the LiveCD Session) and entered the following commands from the tutorial:
```

sudo su -
mkdir /mnt/ubuntu
mount /dev/sda3 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash

```

then created a swapfile:
```

dd if=/dev/zero of=/swapfile bs=1024 count=2048000
mkswap /swapfile
swapon /swapfile

```

and added the following line to the bottom of /etc/fstab (entries are tab-separated):
```
/swapfile     swap     swap     defaults     0     0
```

I then installed LILO (the replacement for GRUB):
```
 apt-get install lilo lilo-doc
```

created a configuration file for LILO (/etc/lilo.conf) with the following contents:
```

boot=/dev/sda3
default=Ubuntu

map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda3
label=Ubuntu
read-only

```

Open a new Terminal window and run parted:
```

sudo parted
set 3
boot
on
quit

```

At this point, I found that if I simply installed using the "lilo" command, it wouldn't allow me to get into Vista.  To fix this, I installed Lilo to the Linux partition instead of the root of the drive: (Edit: this should be done from the first Terminal window; the one that has been chrooted)
```
lilo -i /dev/sda3
```

After that, I rebooted, ran rEFIt's partition utility to make sure that the partition tables were synced, and it has worked perfectly ever since.

Hope this helps; let me know if you need anything clarified.

---

### Post by violajack on 2008-03-24
I had a pretty easy time of partitioning just by using the built in gui tools in osx.  

This is how I set up my triple boot:
[http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)

---

