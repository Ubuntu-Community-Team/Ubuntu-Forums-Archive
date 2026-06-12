---
title: "uhhh where is it...? and is it possible"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by tadada on 2007-07-27
when I installed Ubuntu I took the 52.4 gig and split it up
10 gig for the install partition for Ubuntu
2 gig swap yes I know it is massive
and 40.4 gig for my DATA (pics installed stuff that I dictate don't go in the install partition (if possible) etc)

but now I can't find the different partions

and also when I installed I on accident didn't make it possible for it to display at the full 1280 x 1024. Is it possible to fix this without redoing it all? (I am using Virtual PC till I decide it is worth dual-booting. (just got the mouse to work too. :( ))

---

### Post by Rocket2DMn on 2007-07-27
Please post the output of the command
```
sudo fdisk -l
```

For your monitor resolution, you can reconfigure the xserver by running
```
sudo dpkg-reconfigure xserver-xorg
```
When you get to the resolution page, use TAB to move between options and SPACEBAR to select.  Choose the max resolution your monitor can support and anything less than that.

---

### Post by tadada on 2007-07-27
for some reason when I go to type in my password for the sudo it won't take it it won't type any thing there

---

### Post by Rocket2DMn on 2007-07-27
That is normal, it is a security precaution.  It is receiving input, it just doesn't display on the screen.  Type your password normally and hit enter.

---

### Post by Majorix on 2007-07-27
Or if you want to make sure to see you are typing, use gksudo wherever you see sudo. That will launch a graphical environment where you can type your password. But its usually recommended only for graphical programs.

---

### Post by tadada on 2007-07-27
Disk /dev/hda: 52.4 GB, 52428718080 bytes
255 heads, 63 sectors/track, 6374 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        1459     1951897+  82  Linux swap / Solaris
/dev/hda3            1460        6374    39479737+  83  Linux

thanks for the password help and I'm gunna reboot it to make sure everything worked but threabove is what you asked for

---

### Post by Rocket2DMn on 2007-07-27
[EDITED]
I see
/dev/hda1 as your boot sector and file system
/dev/hda2 as your SWAP
/dev/hda3 as your data partition
You might need to make sure they are declared in /etc/fstab
Here is some good reading to help you out with that: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Sbarton on 2007-07-27
If you get into the screen you can try SYSTEM/PREFERENCES/SCREEN RESOLUTION and then select the one you require.
regards

---

### Post by tadada on 2007-07-27
is it possible to instead use a program or something that will do the same thing to kill the data ppartition and add it too the first partition?

---

### Post by Rocket2DMn on 2007-07-27
Hold on, I confused myself earlier when I went back and edited my entry.
/dev/hda1: boot sector and file system - your 10 gigs
/dev/hda2: SWAP space - 2 gigs
/dev/hda3: data storage - your 40.4 gigs
You can use gparted to combine the partitions, but you have to use the LiveCD since the drives can't be mounted when you make the changes.

I will edit my previous entry for posterity

---

### Post by tadada on 2007-07-27
ok when i loaded the disk i went to Gparted and killed the data partition but before i was alouded to grow the first one but now it won't let me... it says it is locked but before only the swap was
nvm i just temporairly unmounted it but now it says it can't go any bigger... that 9.5 gig is the max when about 40 gig is open

---

