---
title: "Forced Installed to second partition w/o swap"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by ccacioppo on 2006-08-08
I have an HP Pavilion 1.6 ghz, 384mb ram, 60 gb Hd system with winXP in primary boot partition 1 - /dev/hda1 (~30 gb). Installed Ubuntu 6.06 from Live Cd manually (edit partition during install) to second primary (reseirFS) partition 2 - /dev/hda2 (~27 gb) on same drive. 

Ubuntu would not recognise this second partition on 2 install attempts. I 'forced' the install manually putting / root on the second partition and IT installed without swap space. It warned me it was doing this but I am evaluating it so I went ahead.

Install was fine, GRUB dual boots machine fine, no issues.

Ubuntu is quite impressive and ran flawlessly for me on this initial install. 

Question is can I make (or remake a swap area) in the current filesystem Ubuntu resides in? (the root fs is ~ 25 gb, so room is not an issue) and what is the process to do that?

Is it simpler to blow away partition and start over, re-install.
(At this point, I can do this w/o problem). How do I get Ubuntu to auto install to second partition? Leave space unallocated?

If I can 'fix' my current install by adding a swap area that would be great. I look forward to learning and participating more in the Ubuntu community.

Thanks, 
Charlie:confused:

---

### Post by anaconda on 2006-08-08
You can make and use a swap-file, which is just as good as a swap partition, so no need to make a swap partition....

in terminal type:

sudo su
dd if=/dev/zero of=/swap bs=1024k count=512
mkswap /swap
swapon /swap

that will make a 512MB swap file named swap, and take it to use.

the "swapon /swap" command has to be run each time the computer boots, to make it active. the other commands are run only once.

---

### Post by anaconda on 2006-08-08
Oh. and to run the "swapon /swap" command automatically each time the computer is booted you have to add "swapon /swap" to some file, which is loaded each time the machine is booted. (I think it has to be run as a root..)

There is such files, but cant remember the names of them.. hope someone can point you to it..

---

### Post by ccacioppo on 2006-08-08
Thanks for the quick help, much appreciated.:p 

WHat I did is read the Wiki which points to other directions and plans 
for setting the partitions correctly. I wiped the installation away and
used Gparted to make the proper partitions for /root /swap and /home.
Also made a 3.5gb fat32 'share' drive for (as recommended in the wiki)
for sharing files btwx Windows and Ubuntu.

With this little bit of education and planning, now I know where it all goes.

My new installation went smoothly, updated everything, sound, printer, network, ati card, etc and its all good. (windows is never that easy)

Ubuntu is a real pleasure to work with and seems like a very polished OS.

Thanks again for the great response, patience and I hopefully can return the help to someone else in the greater Ubuntu community soon!!

THANKS! 
Ciao,
Charlie Cacioppo
:cool:

---

