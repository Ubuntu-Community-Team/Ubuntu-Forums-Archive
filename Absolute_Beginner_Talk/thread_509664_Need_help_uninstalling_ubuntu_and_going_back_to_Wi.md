---
title: "Need help uninstalling ubuntu and going back to Windows."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Bensky on 2007-07-25
I enjoyed using Ubuntu, but right now I am running out of space and need to remove it. I used it basically to learn and test stuff, and if I buy a new computer I'll probably load ubuntu only, but for now I need to go back to Windows until I either get a new hd or get a new computer. :)

Here is my setup:
[img]http://img165.imageshack.us/img165/8558/partitionshg6.png[/img]

Can anyone tell me how I can just remove Ubuntu and make my "Disk1" go back to how it was without the Ubuntu partitions there? I know how to restore the MBR, I just basically need to get rid of Ubuntu and then im all good.

To clarify...when I installed ubuntu I told it to take up 50% of the drive, so it took half of the full ~37.5 GB on my HD and left the other 50% for windows. I need to get rid of the ubuntu partitions that took up the 50% or uninstall ubuntu, and restore that taken up space back to my C: drive so I will have a full ~37.5 GB hard drive again with just windows on it.

Thanks,
Bensky :confused:


P.S. I also have a ghost backup as you can see in that screenshot - if I click on "Disk 1" it highlights all 3 entries, even the ubuntu partitions. Would this remove the ubuntu partitions and leave the windows one? If so, this might be easier, im just not clear on that part...

---

### Post by doomster on 2007-07-25
just use Partition magic from windows, to delete all Linux partitions, and maby resize your windows one to fill up unallocated space:) this should work

---

### Post by Bensky on 2007-07-25
> **doomster said:**
> just use Partition magic from windows, to delete all Linux partitions, and maby resize your windows one to fill up unallocated space:) this should work

Hmm, that one costs money. :P Guess i'll have to go "find" a copy, unless someone has a free alternative? ;)

---

### Post by Blutack on 2007-07-25
Boot your ubuntu live cd
Go System - Admin - Gparted
Delete your two linux partitions, keep the ntfs one.  Then hopefully gparted will let you grow the ntfs partition back up again.  (I'm not sure but I think it can grow ntfs...)

---

### Post by Bensky on 2007-07-25
> **Blutack said:**
> Boot your ubuntu live cd
Go System - Admin - Gparted
Delete your two linux partitions, keep the ntfs one.  Then hopefully gparted will let you grow the ntfs partition back up again.  (I'm not sure but I think it can grow ntfs...)

Alright, that would remove ubuntu i'm assuming since the whole partition would be gone. After that, I would have to fix my MBR right? :P

I looked on the gparted website and it can resize NTFS fully, so I think that would work.

---

### Post by doomster on 2007-07-25
bensky   check your PM's. ;)

---

### Post by bodhi.zazen on 2007-07-25
You can use the Ubuntu desktop cd (gparted) as above ...

To fix the Windows boot loader :

To restore windows MBR:  Boot the Windows XP CD.

Windows will come with some screens and look at "repair an existing XP" or something like that.

NOT THE AUTOMATIC REPAIR it will bring you nowhere.

You get three options,install windows,repair an existing XP or quit.

Choose "repair" ; You get a black screen where the existing install [a number] is displayed.

Choose that number and then it asks for your administrator password.

Type in ADMINISTRATOR if you don't know otherwise and pray it's the right one.

Then you get a prompt.

Type fixboot and see what it tells you.

If this doesn't work type fixmbr and you get a warning about messing up things,but ignore,and proceed.

This should make your windows bootable again.

See also: [http://ubuntuforums.org/showthread.php?&t=303765](http://ubuntuforums.org/showthread.php?&t=303765)

---

### Post by annda on 2007-07-25
you really don't need *wink* software (by the way: nice euphemism, i like it). you can modify your partitions either using ubuntu live cd and gparted or the gparted live cd from sourceforge.net

you will still have to use a windows INSTALL cd to overwrite GRUb in the mbr.

---

### Post by Bensky on 2007-07-25
Alright, I am in the LiveCD now and loaded up gparted, everything appears to be fine except for one thing - the linux swap and extended partitions seem to be locked, and it doesn't look like I can remove them, but the other linux one I can.

Here's a screenshot:
[img]http://img129.imageshack.us/img129/7742/screenshotta2.png[/img]

^What should I do with the locked ones? :confused:

---

### Post by doomster on 2007-07-25
these seem to be locked cause theyre mounted atm. right click on them and select Unmount drive, and they will get unlocked

---

### Post by bodhi.zazen on 2007-07-25
You should start gparted as root :

Open a terminal and enter :

```
gksudo gparted
```

---

### Post by Bensky on 2007-07-25
> **doomster said:**
> these seem to be locked cause theyre mounted atm. right click on them and select Unmount drive, and they will get unlocked

When I right click, unmount is grayed out. Could they be my livecd? :\

---

### Post by doomster on 2007-07-25
do this and you should be fine :) sorry for that ommision :P

---

### Post by Bensky on 2007-07-25
Umm, when I run that command now all the partitions are locked. :\

in terminal it reads:
libparted: 1.7.1
Automounting disabled

---

### Post by doomster on 2007-07-25
> **bodhi.zazen said:**
> You should start gparted as root :

Open a terminal and enter :

```
gksudo gparted
```

do this and you will be fine.. sorry for that ommision :P

---

### Post by Bensky on 2007-07-25
> **doomster said:**
> do this and you will be fine.. sorry for that ommision :P

Yeah, I did...lol. read my post above

---

### Post by doomster on 2007-07-25
did you now as root tried to umount the locked drives?

---

### Post by Bensky on 2007-07-25
> **doomster said:**
> did you now as root tried to umount the locked drives?

Ugh okay, this is weird. When I try to unmount the ext3 or ntfs partition, it works, but then the other one becomes locked again...

Also, the other partitions at the bottom still have the grayed out unmount button...the one that's inside the other one has a "swapoff" button. Not sure what that does.

---

### Post by bodhi.zazen on 2007-07-25
Odd, it is not supposed to work that way ...

OK, close all instances of gparted ...

Then Go to System > Preferences > Removable Drives and Media and uncheck the box about automatically mounting drives.

Then re-start gparted, as root (gksudo gparted)

Unmount all partitions

swapoff unmounts your swap partiton ...

Off topic : I think Ubuntu is trying to tell you something ...

If you are still having problems, use the gparted live CD (it is a small download)

[gparted live cd](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by Bensky on 2007-07-25
> **bodhi.zazen said:**
> Odd, it is not supposed to work that way ...

OK, close all instances of gparted ...

Then Go to System > Preferences > Removable Drives and Media and uncheck the box about automatically mounting drives.

Then re-start gparted, as root (gksudo gparted)

Unmount all partitions

swapoff unmounts your swap partiton ...

Off topic : I think Ubuntu is trying to tell you something ...

If you are still having problems, use the gparted live CD (it is a small download)

[gparted live cd](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)
Okay well now I can unmount both the ntfs and ext3 partitions, but the bottom 2 still won't let me unmount. Should I click the "swapoff" button?

EDIT: Oh, and when I go to the information on the extended one, it says: "Busy (at least one logical partition is mounted)" if that's any help.

---

### Post by doomster on 2007-07-25
yes presss it to umount the swap too

---

### Post by bodhi.zazen on 2007-07-25
> **Bensky said:**
> Okay well now I can unmount both the ntfs and ext3 partitions, but the bottom 2 still won't let me unmount. Should I click the "swapoff" button?

EDIT: Oh, and when I go to the information on the extended one, it says: "Busy (at least one logical partition is mounted)" if that's any help.

EDIT: yea, that is your swap. It is busy because it is mounted via swapon. use swapoff ;)

Bodhi hopes you have enough RAM to run the Ubuntu Desktop CD (= gparted) without swap .... he he he

---

### Post by Bensky on 2007-07-25
> **doomster said:**
> yes presss it to umount the swap too

Okay, now everything is unlocked. It appears that i can delete the linux swap, but I cannot delete the "extended" partition thing. Would the option to delete it enable itself after I delete the swap? I'm thinking yes because of that information I got about how it's busy.

EDIT: Yeah, it re enabled itself. I should delete the extended one too, right? ;)
EDIT2: Yeah, I have 1gb of ram, should be fine.

---

### Post by doomster on 2007-07-25
just delete both swap and extended, and apply changes to make some unallocated space
after changes are applied try to enlarge-resize your windows partition, or make one new partition formated with NTFS format

---

### Post by Bensky on 2007-07-25
Okay, deleted all of those and everything seems to be working fine now. I'm going to go attempt to restore the MBR and ill post here if I have any trouble. :p

EDIT: Yeah, I gave all the space back to my ntfs partition (windows) and it said it worked fine so im good i think. ;D

---

### Post by doomster on 2007-07-25
may the god of computers(not sure if there is one:P ) be with you :)

---

### Post by bigken on 2007-07-25
[SIZE=6][COLOR=Red]**Fool **[SIZE=2][COLOR=Black]but each to there own[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by anewguy on 2007-07-25
For others reading this post who want to delete Ubuntu and go back to just Windows, please see my prior post on an easy way to do this at:

[[COLOR="Red"]remove Ubuntu on dual boot systems[/COLOR]]("http://ubuntuforums.org/showthread.php?t=508927")

:)

---

