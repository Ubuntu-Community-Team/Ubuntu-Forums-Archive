---
title: "samba and 3d-desctops-ntfs writing"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by tonimahoni on 2007-08-15
hi everybody,

i have installed Ubuntu Ultimate 1.4 and its amazing... it looks great.. i love it and i want to use as often i can..
but i have some questions...

1. i cant find the confgurationlink for samba - to get an acess from my windows mashines to the ultimate.. nothing found in help.. can anyone give me a tip??

2. i have acess to my ntfs partitions .. but not writable.. when i try to aktivate it.. i got the message:
------------------------------------------------------------------------------
Fehler beim Mounten von /media/sda1.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/01C7B9895B7E2400': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/disk/by-uuid/01C7B9895B7E2400 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/disk/by-uuid/01C7B9895B7E2400 /media/sda1 ntfs-3g defaults,force 0 0
------------------------------------------------------------------------------
whats this???

and 3.

whats up with this phenomenall 3d destop -  switching between 4 desctops in 3d.. what point on the menu i can administrade activate tihis???


ok.. hope somebody give me an answer.. im new on ultimate and in this forum.. perhaps there are some answers in other threads... sorry for that

cheers and thanx

---

### Post by overdrank on 2007-08-17
HI for number 1 I cannot answer.
2 if you go to synaptic package manager and search for ntfs you will find the two packages you need, ntfs-config and ntfs-3g
3. Desktop effects is located under system, preference, desktop effects, you can also try and install cop-fusion via this link
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
But beware if your graphics are not setup properly it can cause bad things to your system. Good luck! :popcorn:

---

