---
title: "Uninstall Ubuntu Powerbook G4"
date: 2007-12-02
forum: Apple PPC Users
---

### Post by miikkee on 2007-12-02
Hello all, 

-> There have been similar posts about this in the past, but I am still confused... 

I have a powerbook G4 with a dualboot (MacOSX [60GB] and ubuntu [20GB]). 
I would like to remove ubuntu and get my full hard drive space available in OSX [80GB]. 
If possible I would also like to keep all my MacOSX data when I remove the ubuntu partition and resize my harddrive to its original size. 

I heard that a solution is to use parted. The problem is I am not sure how to use it and where to use it (LIVE CD?). 

I would much much appreciate any help on this... 

Miikkee

---

### Post by frog_pilot on 2007-12-03
It is quite simple to remove ubuntu from your mac.

You have to disable your Journal of the OS X partition from within OSX by executing ```
sudo diskutil disableJournal /
``` to prevent data loss during resizing the partition.

Then you have to start from a ubuntu desktop cd. On my iBook edgy is running out of the box. There you have to start **gparted** (a gui for parted). There you can delete the ubuntu-related partitions e.g. newWorld-bootblock, root and swap. After this you can resize your OSX partition.

During restart you have to hold the ALT-Button to choose your OSX-Systemvolume for startup in OF. Enable your Journal by executing ```
sudo diskutil enableJournal /
```.

Thats it! It could be helpful to start your OS X Diskutility with the repair-option after the whole procedure.

---

### Post by miikkee on 2007-12-05
Thanks Frog_Pilot, 

Here is what I did. 

I booted my G4 with the ubuntu LIVE CD version 6.06. 

I opened the terminal, then typed "sudo gparted"

Here is what I saw: 

```
Partition          filesystem         size                flag
-------------------------------------------------------------
/dev/hda1        unknown           0.03    MB        --
unallocated     unallocated      128      MB        --
/dev/hda3        hfs+                 55.75   MB        --
/dev/hda2        hfs                    0.95     MB        boot
/dev/hda4        ext3                  17.86   MB        --
/dev/hda5        linux-swap        811.93 MB        swap
```

There was a small warning sign near /dev/hda1
and there was a small "lock" sign near linux-swap

I am thinking about deleting: 
/dev/hda2 boot 
/dev/hda4 The Ubuntu Space
/dev/hda5 swap 

Am I correct? I am not quite sure...
It seems that I cannot delete the swap because of the small "lock sign"


Well this is for the deleting... What about resizing? I am not quite sure how to do that properly. 
Again I'll appreciate any help on this... Thanks a lot. 


Michael

---

### Post by frog_pilot on 2007-12-05
I would agree with you about the partitions to delete.

hda2 seems to be the NewWorld bootblock
hda4 is root
hda5 SWAP. maybe the lock-sign is there because your live CD is using it.

hda1 is the apple bootblock and hda3 is the OS X system volume.

Did you fill in the MB? For hda3 and hda4 its obvious that the size is shown in GB.

I'm wondering that no parted-GUI was started by the command. You will find the GUI for the program under System -> Administration -> GNOME Partition Editior. Or Try the 6.10 live CD.

There you can delete/ resize your partitions with buttons and the mouse. Leave 128 MB of free space (unallocated) at the end of the hd like in front of hda3. It seems, this freespace is a kind of seperator between the apple partitions.

---

### Post by miikkee on 2007-12-05
Thanks Frog, 

Yes hda3 and hda4 are in GB (I just typed the thing)

I did start the GUI-parted from a command line within the terminal (sudo parted). 

Ok I will try to delete the partitions as you mentioned, and see what I can do about resizing. I'll get back to you after that, and hopefully it'll be good news. Thanks for your time on this. 

Mike

---

