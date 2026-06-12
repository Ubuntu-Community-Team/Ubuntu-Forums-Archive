---
title: "dualboot/grub/no internet problems"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by jamienos on 2007-05-13
Hi

Installed ubuntu and windows xp dual boot on this computer ( 28 gb hard drive only ) went smooth and it all worked fine

Then my sister wanted it done, that computer has around a 75 gb hd and a 18 gb one the dual boot both being on the 18 gb one, the installation went fine but when it came to adding windows xp to the grub this is where the problem started, the menu.lst i needed to edit was blank totally empty and not a word in sight thus meaning i cannot add windows xp 

And had already done the flag's set it to ubuntu and took it off xp etc just like i did on my own computer so i know it's right

The 2nd problem, which isent exactly ubuntu related but since i'ts kind off about it

Windows xp has no internet whatsoever, i dont know much about network connections or the likes and when i did my own dual boot it detected everything fine and internet worked pretty much after i installed

The only thing in network connections is 1394 connection (which a search seems to say it's nothing to do with a network) so i just gave up trying, also found to install the drivers that came with the network card - dont think we have this so stuck again!

Thank's if you managed to read all that and for any help :).

---

### Post by mikewhatever on 2007-05-13
Are you sure that GRUB menu is empty? Do you see grub menu at boot? Can you post the output of the following from the terminal
> cat /boot/grub/menu.lst
The other issue, 1394 adapter is your Firewire port and not your network card.
[http://en.wikipedia.org/wiki/Firewire](http://en.wikipedia.org/wiki/Firewire)

---

### Post by jamienos on 2007-05-14
The grub menu show's upon bootup, but the menu.lst is empty so i cannot add windows xp, so as it is now only windows will load

i tryied that command by loading up the ubuntu livecd since i cant currently acess the real ubuntu install

Doing cat /boot/grub/menu.lst outputs the menu.lst just like the one that i have working so it is there :) 

doing a sudo gedit /boot/grub/menu.lst outputs it as blank so cant edit it to addthe windows xp part

thanks

---

### Post by dstew on 2007-05-14
You have to mount the hard disk installation on your live CD filesystem before you can see and edit the real menu.lst file. After booting the live Cd, open a terminal window and enter:```
sudo mkdir /media/ubuntu
sudo mount /dev/hda2 /media/ubuntu
cat /media/ubuntu/boot/grub/menu.lst
```
If sudo asks for a password, just hit enter.
Also, I do not know if your 18 GB disk is really /dev/hda2. The output of the command **sudo fdisk -l** should tell us that.

---

### Post by jamienos on 2007-05-14
> **dstew said:**
> You have to mount the hard disk installation on your live CD filesystem before you can see and edit the real menu.lst file. After booting the live Cd, open a terminal window and enter:```
sudo mkdir /media/ubuntu
sudo mount /dev/hda2 /media/ubuntu
cat /media/ubuntu/boot/grub/menu.lst
```
If sudo asks for a password, just hit enter.
Also, I do not know if your 18 GB disk is really /dev/hda2. The output of the command **sudo fdisk -l** should tell us that.

At first it worked then the grub menu upon startup disappeared, but i redid it all and it is fine now and will now load up either xp or ubuntu

thanks for the help! :)

---

### Post by mikewhatever on 2007-05-15
> **jamienos said:**
> The grub menu show's upon bootup, but the menu.lst is empty so i cannot add windows xp, so as it is now only windows will load

i tryied that command by loading up the ubuntu livecd since i cant currently acess the real ubuntu install

Doing cat /boot/grub/menu.lst outputs the menu.lst just like the one that i have working so it is there :) 

doing a sudo gedit /boot/grub/menu.lst outputs it as blank so cant edit it to addthe windows xp part

thanks

So, how do you boot Ubuntu then? That menu includes both Ubuntu and Windows options. If it does not exist, then Ubuntu should not boot.

---

