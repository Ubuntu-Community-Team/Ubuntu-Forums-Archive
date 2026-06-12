---
title: "Mount queries"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by niteblind on 2007-04-15
Hi All,

Wonder if anyone can answer my query? I am currently using Kubuntu Dapper and I also have a Synology DS-106 NAS. I have set up one of the folder as a mount point on my linux as advised by a friend so as to be able to play music files from my backup drive through Kaffeine.

I notice though now as soon as linux boots up it kicks the NAS out of hibernation mode and starts up the hard drive regardless of whether i actually use it or not. I would rather this does not happen, what i want is the following

1. to have the DS-106 listed a remote location/place in Nautilus
2. To be able to play files from the NAS
3. To only kick it into life when i actually go onto the drive.

below is the output of my fstab file:

ile system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.2.66/music	/media/Archangel smbfs	credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

the above entry regarding the remote store was verbatim from my colleague so I do not actually understand the extra options at the end and these may be the cause, any help would be appreciated.

Also from the above I now have an icon on the desktop which i would rather not have just simply want an entry in the places section of nautilus I like a clear desktop can this be done by altering the above?

Finally there is one other thing i would like to be able to do but i do not think it is possible but by all means prove me wrong. I would like to bale to mount the root folder of the nas which would be //192.168.2.66/

Cheers in advance for any help offered

---

### Post by freebird54 on 2007-04-15
With the drive automounted in /etc/fstab, it will be started up and wil show on the desktop.  It shows on the desktop because the mountpoint was in the /media directory  - which exists for that purpose!

I THINK you can add noauto to the fstab entry, and mount by command at your whim, but if not you can transfer the info OUT of fstab to a script file that you run when you want to access it.

Hopefully this is clear enough! ie:

```
sudo mkdir /mnt/Archangel
```

and edit the entry to be /mnt/Archangel instead of /media/Archangel

would get it off your desktop.  OK?

---

### Post by niteblind on 2007-04-15
thanks for the response, if i set the mount point to be as you suggest /mnt/.... will this still be picked up by Nautilus and listed as one of my places?

if so can i set the script up to run when i click on that place in nautilus only is that possible at all does anyone know?

Alternatively does anyone know of a player OTHER THAN VLC that can play files over a smv network share? It liooks like Kaffeine should but when I brouwse through open file dialog box to the share and double clock a file it says it cannot do it beciase it is not a local file.

cheers

---

### Post by freebird54 on 2007-04-15
It certainly *should* default to being there!  As for the script, I gather you don't want things on your desktop - so I would create a launcher on one of your panels (top or bottom) - just <alt><F2> to open a 'Run' and run it.  Of course, you can also put the 'Run' on a panel too - lots of configuration possibilities on these things!

---

### Post by niteblind on 2007-04-17
Hi all,

fraid it did not work. I have created a directory called /mnt/share and then edited to the fstab entry above so that it reads as follows:

//192.168.2.66/music	/mnt/Archangel smbfs	credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0


but now the share no longer appears in the Nautilus "places" list which i want it to.

Anyone know what i have done wrong here?

cheers

---

### Post by freebird54 on 2007-04-17
Not sure if you did anything wrong!  I suspect that the Places menu is built at boot time automagically - as I can't find any way to edit it (as yet, anyway).  So - if it isn't going to be visible at boot up, I guess it won't get in there.  The only workarounds I can think of are more trouble than they're worth (eg - restart X after dive is in) - so you may be stuck without perfection.  Anyone else out there with brilliant thoughts on this subject?

---

