---
title: "Hdd gone for good?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-01-11
I was having problems with my hdd first not partitioning correctly from within in Gparted so I de-fragmented it multiple times. Then it kept saying I had a bad sector which would make me unable to use Gparted. Partition Magic would also fail if i tried to partition it. So i used ntfsresize from terminal and got it resized. Still when i boot the Ubuntu live cd it shows that my windows partition takes up the whole drive. From within Windows it also shows that the partition takes up the whole drive even though it said it was successful. Now in windows supposedly my data takes up 20 gigs more than it did before. (the exact size of the partition i made) So I'm at a lost as I don't know where to go from here.

I'm thinkin my hdd is just crapping out but it's kind of odd since I've only had this laptop since august of last year.

Just for the hell of it, it is a PATA drive.


Please tell me this isn't the case :( (that my drive is crappin out).



I did attach a picture of what shows up in partition magic so you guys can see that it's odd. Says only 45 gigs are used, but the bar shows up about 65 gigs

---

### Post by dalejefferson on 2007-01-11
Re Sizing NTFS is always a dangerous job, and can corrupt the file system.

I would recommend:

[LIST=1]
[*]Back up any remaining data
[*]use fdisk to delete all partitions
[*]reboot
[*]try installing Ubuntu again
[/LIST]

It would seem unlikely that your drive died at the same time as you are installing Ubuntu.

Modern Hard Disks last for years.

---

### Post by codejunkie on 2007-01-11
> **rj686 said:**
> I was having problems with my hdd first not partitioning correctly from within in Gparted so I de-fragmented it multiple times. Then it kept saying I had a bad sector which would make me unable to use Gparted. Partition Magic would also fail if i tried to partition it. So i used ntfsresize from terminal and got it resized. Still when i boot the Ubuntu live cd it shows that my windows partition takes up the whole drive. From within Windows it also shows that the partition takes up the whole drive even though it said it was successful. Now in windows supposedly my data takes up 20 gigs more than it did before. (the exact size of the partition i made) So I'm at a lost as I don't know where to go from here.

I'm thinkin my hdd is just crapping out but it's kind of odd since I've only had this laptop since august of last year.

Just for the hell of it, it is a PATA drive.


Please tell me this isn't the case :( (that my drive is crappin out).



I did attach a picture of what shows up in partition magic so you guys can see that it's odd. Says only 45 gigs are used, but the bar shows up about 65 gigs

I've had problems like this when using partition magic it gave me errors and reported space incorrectly and i also noticed for some reason that if i use partition magic on a drive sometimes gparted will not work afterwards. in my cases though the drives were not bad the partition tables were just really messed up, theres not much you can do when that happens except repartition and reformat the drives and reload your OS here's some things you could try but they involve reloading your os though.

**first [COLOR="Red"]BACKUP All DATA[/COLOR] just in case your drive is failing.**

if by chance you have to repartition and reformat make sure you have your windows/windows-restore cds, some laptop/desktop manufactures don't include one but offer a utility to create one. if you haven't done that already make sure to create them before you repartition and format your harddrive if you don't have your windows cd or the utility to create them contact the manufacture and have them send you a restore cd.

find the drive manufacture and model, go to there website and download there utilities for the drive model and run diagnostics on it in most cases if it is a bad drive there utilities will detect it and let you know if it does detect a bad drive hit up the manufacture for a replacement if it's under warranty.

if there utilities don't detect anything wrong with the drive use fdisk to delete all partitions or you could use a tool like dban, autoclave or the drive manufactures utilities to zero out the drive to make sure all partitions and data is gone.

do not use partition magic again to partition the drive, just insert the windows cd and reboot the computer with the cd in the drive to reinstall windows either let it use the whole drive or set the amount of space during the install you want to use for windows, if you use the whole disk you can use gparted on the ubuntu disk to resize the drive with no problems later and install ubuntu.

i know it's probably not what you wanted to here but partition magic does some funky things to partitions sometimes and wiping it all out and reloading is pretty much the only thing you can do.

---

### Post by jvc26 on 2007-01-11
Another thing which may be causing problems - did you defrag the ntfs partition before you started? Otherwise a fragmented partition can cause you all kinds of problems,
Il

---

### Post by rj686 on 2007-01-11
Thanks for the info, I'm downloading the manufacturer's utility now and testing it ;). You are correct I have used partition magic in the past and that's probably what screwed it up.

---

### Post by rj686 on 2007-01-11
Boo the manufacturer's utility doesn't work at all :(

---

