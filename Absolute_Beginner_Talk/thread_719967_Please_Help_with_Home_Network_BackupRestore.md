---
title: "Please Help with Home Network Backup/Restore"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by DamonChyld on 2008-03-09
I am looking for a good backup solution for my home small home network. I have a desktop and a laptop (both running Gibbon) and a 1tb NAS drive. I want to be able to create scheduled backups to the NAS and have the ability to easily restore my complete system to a prior state (with all packages and programs installed and configured). I am about 2 weeks into linux from windows so a lot the more code/script intensive stuff is still intimidating.

I have been working at this for the last few days and am really no closer to a solution than I was in the beginning! 

I have tried:
QuickStart 6.0
Looks like a great program that has worked for a lot of people but I had pretty sever issues with it. When I would attempt to restore my /home directory the program would quit and then my system would not load Ubuntu on a restart (instead would boot into BusyBox after hanging on the boot screen for awhile).

Sbackup
It does not give status updates when it's completed a backup/restore so you end up needing to keep an eye on the network traffic through your system monitor (if doing over a NAS, if your doing it local you can watch the CPU history on the backup but your out of luck as far as I can tell on the restore). There is no option to restore a complete backup so you are left restoring X # of backups individually. Quite time intensive.

TimeVault/Flyback
Both of these programs have issues writing to or reading from my NAS drive. (It's formatted XFS and mounted locally but they still don't like it)

PartImage
Cumbersome to use as you need to backup from a different partition and most people recommend using the live rescue CD for restoring.

Restore-Backup
Seem way too large and complicated for my setup. I tried Restore-Backup and it looks like a great solution for anyone with a backup server (it can not backup/restore the system it is installed on). The other large system solutions (MondoRescue, Amanda, Baccula) also seem like overkill


I have not tried:
Rsync/Grsync
I ran into a lot of people looking for help problem solving these and most seemed unsure if they would support full system restores.

From terminal 
```
something like this... tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /
```
I am looking for something with a GUI that can do scheduled backups, incremental backups (of changed data), etc.

Backuppc
The documentation page is intimidating... other than that I have no real issues with giving it a shot. I am just getting frustrated configuring/reconfiguring stuff for a program only to find that it comes up short in some way or another.

Think you could help me out a little? :lolflag:

---

### Post by dj1120 on 2008-03-09
Have you tried Synkron , granted it not a true backup program so much as it syncs folders but I have used it and it seems to work

---

### Post by DamonChyld on 2008-03-09
Thanks for getting back to me but what I am looking for is something that can capture my system and application settings, packages, installed apps, etc. and restore it when I mess something up. I like to try out a lot of new packages/apps and want a way to restore my complete system when something goes awry.

---

### Post by reeseslover531 on 2008-03-09
i know partimage is pretty good ([http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page))  You can try that out.  It takes a partition and creates an image file for it, that sounds to be what you are looking for.

---

### Post by DamonChyld on 2008-03-10
The general consensus on the Howto ([http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)) seems to be that it is best to create your backups to a local partition and restore from the recovery cd. I am desiring to set scheduled backups to my NAS drive and would like to be able to run a recovery from an active system. When I tried partimage, I did so using the recovery cd and it required a lot more active participation (going into bios to boot from cd, navigation menus...) than I think should be necessary. 

If there is a well documented procedure for backing up to/recovering from a NAS drive, I can see how Partimage would be a great solution. I have just been unable to locate one :(

---

### Post by DamonChyld on 2008-03-10
It looks like the only way to use Partimageover a network is to run it off a server ([http://www.partimage.org/Partimage-manual_Network-support](http://www.partimage.org/Partimage-manual_Network-support)). I want a solution that will work for both of my home computers and do not have a spare box to run as a server so it looks like this solution will not work.

Edit:After reeseslover531's response I did install the standalone version (had tried the recover CD the first time) and tried to get it to write to the NAS through the 'connect to server' option but it was unable to do so.

---

### Post by mgranet on 2008-03-10
I've found CloneZilla to work quite nicely for network backups. It runs off a LiveCD, and you can multicast backups to the whole network, if you so desire.

---

### Post by DamonChyld on 2008-03-12
I have tried just about every gui backup program but been unable to get them to work (seems like every one requires you to have a server if you are backing up to a NAS drive...?) so am going with the tar option. It's not a perfect fit by any means but it'll do the job until I hear of something that has the functionality I am looking for without requiring a server. Here is the tar command I am using, note that the --exclude=/BigDisk is my NAS drive, I mounted it to / so that I don't have to have a desktop icon for it all the time.

```
sudo tar cvpzf BACKUP.tgz --exclude=/proc --exclude=/lost+found --exclude=/home/USER/Desktop/BACKUP.tgz --exclude=/BigDisk --exclude=/mnt --exclude=/sys --exclude=/home/USER/.Trash --exclude=/tmp --exclude=/media exclude=/boot / 
```

---

