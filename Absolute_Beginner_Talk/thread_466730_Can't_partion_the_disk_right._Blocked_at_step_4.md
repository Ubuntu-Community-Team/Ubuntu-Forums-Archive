---
title: "Can't partion the disk right. Blocked at step 4"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by afropete14 on 2007-06-07
I want to give Ubuntu a try because I want to see what all the hype is about so I got the CD and ran it.  I get past the keyboard choosing thing and then I get to step 4 where it wants me to partition my drive.  Now I want to dual boot my computer so I set up another partition to install Ubuntu on.  I made this partition with a piece of software called Paragon Hard Disk Manager if that matters because I did it out of the install disk.  Anyway when I choose it it says that something about not having a file system.  the partition has the little \ like it says and I have the swap partition.  It just won't let me get past and it is driving me crazy.  I tried just clicking on the use whole hard disk thing and it worked fine but I want to dual boot.  

Am I just overlooking something simple?

Do I have to partition the drive in the installation?

Also I tried Wubi and that didn't even work so maybe my Windows just hates Ubuntu, maybe it never learned how to share.  

Any help would be nice

---

### Post by Inxsible on 2007-06-07
since you created the new space thru a 3rd party app. It must be unallocated and therefore without any file system on it.

Select the unallocated part and then click New Partition and create the partitions for root- denoted by / --   /home and swap drive and you should be good to go

---

### Post by floke on 2007-06-07
Make sure the mount point for the partition is set to root '/' (not \) - and ext3 - use right click to edit the partition. Make sure you check the 'format' box too. You could use the gparted utility on the livecd to set the partitions first.

---

### Post by afropete14 on 2007-06-07
the menu looks something like this:

hda
    hda1  /media(I don't remember what was here)1    ntfs   unknown    ( this of course is my windows partition)
    hda2 /media(again I don't remember)2    ext-32     (checked format box)   26550   (this is where I hope to                        install to
    (I really don't remember this at all)    (checked format box )  swap  512   (this of course is the swap)



I don't know if that helps but it might.

---

### Post by floke on 2007-06-07
Right click hda2 and change it from /media to just '/' - i.e. the root filesystem

That should do it

---

### Post by afropete14 on 2007-06-08
Ok thank you everyone because it actually worked.  Now that I have it installed I try to boot it and it gets most of the way but oh my goodness is it slow.  You may think I am over reacting but around half an hour to get to the login screen drives me crazy.  I then login in and then it shows me this warning about can't run something about GNOME and just sits there.  Also the mouse response is really crazy because moving the mouse move it a ton and it happens after a couple seconds.  Any ideas?

---

### Post by eentonig on 2007-06-08
What are you're specs?

---

### Post by afropete14 on 2007-06-08
1.9 Ghz single core. 512 mb RAM.  What I am comparing it to is my bloated Windows system and I actually part of reason to get is a light OS that doesn't have all the crazy crap in the backround.  My windows system takes about 2 and a half minutes to completely boot.  So far Ubuntu is at half and hour and doesn't even completely boot.  the live disk worked.  I ran it with the safe graphics option but I did that just so it would work faster, I didn't even try the normal mode on the live disk.

---

