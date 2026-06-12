---
title: "package uninstalling"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-19
I installed Edubuntu today and it must be *HUGE* because it filled the remainder of my HDD. I began uninstalling but soon noticed that when it was marked to remove a program that it also wanted to take the edubuntu desktop with it. I wanted to keep my edubuntu desktop and lose the program (onscreen keyboard program, for example). Can this be done? Or am I stuck with space filling programs that I really do not need...?

Btw, how do you fuse an empty existing partition with a partition that is already populated? I could use the extra space from another partition I'm not using....:-k

---

### Post by Dr. Nick on 2006-10-20
dont worry about it removing edubuntu-desktop, If you look carefully only a few kb or mb will be freed, it will not erase evertyhing else.

edubuntu-desktop is a metapackage that is made to depend on all the default packages to simplify installation and upgrades.

If you search the forum for "metapackage" you can learn alot about it

You may not be able to fuse the empty to an existing, im not sure
you should be able to format it and mount it though, look around here for gparted instructions

---

### Post by ReaderRat on 2006-10-20
> you should be able to format it and mount it though, look around here for gparted instructions
gparted Live CD site:
[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/download.php)

EDIT: gparted is on your Ubuntu Live CD install disc.

---

### Post by Dr. Nick on 2006-10-20
> **ReaderRat said:**
> gparted Live CD site:
[**Gnome PARTition EDitor = gparted**]("http://gparted.sourceforge.net/download.php")

EDIT: gparted is on your Ubuntu Live CD install disc.


here are some instructions
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Just BE CAREFUL and make sure to have backups, partitions can be a dangerous thing, 

Make sure your not tired ;)

---

### Post by Sef on 2006-10-20
> because it filled the remainder of my HDD

How many gigabytes are you talking about?

---

### Post by saintj0n on 2006-10-20
Ok..
I put the ubuntu cd in the drive..vulcan nerve pinch..select install ubuntu..go to terminal..type gparted and it comes up with /dev/hdc1 has 8 GBytes free(out of 8) and /dev/hdc2 has 300Mbytes free out of 10Gbytes. The rest in used up by 2 swap partitions.  I was hoping to be able to fuse the two into one but I think they are 2 physical drives because I erased the /dev/hdc1 and couldn't resize /dev/hdc2.  Alright, that sux but I can deal. So, maybe there is a way to transition some data over to the other drive. Typically, I would just move data, but there really isn't any data on this computer, I use it for developing apps/writing reports and that is it. So, I need to move some programs over somehow. Is this an option in Synaptic or will I have to do it manually(if so, how?)

---

### Post by Dr. Nick on 2006-10-20
It appears you only have one physical hard drive, if you had a second drive it would refer to it as /hdc and /hdd. The last letter will change for each drive.

Now onto your partitions, You do not need 2 swap partitions, One partition of about 500mb-1gig will suffice depending on how much memory you have.

The easiest solution may be a total reformat and repartition, but if you want you can fix the issue with the swap and make it useable for data storage. Depending on the sizes of the swap partiton you could erase both using the livecd and then make a single new one, or just erase one and use the other as data storeage. 

The best thing to do would be to make the new partiton your /home drive so all you projects will be stored on a different partition then the system. I dont think you can really tell synaptic to install to a different partition, With program installs it really only checks the file space of the "/" partition. A smiley got in the way of one of you hd sizes.

If this is a fresh install you should have more space free then 300mb of 10gig. I would [this guide]("http://www.psychocats.net/ubuntu/separatehome") and make a /home partition from one of the swaps if you want to avoid a reformat.

---

### Post by saintj0n on 2006-10-20
The 2 hdc drives have locks next to them. What is that?

---

### Post by saintj0n on 2006-10-23
I am beginning to think there is a 2nd drive and it has gone bad. Either an hdd is bad or the fan is shot, cuz it sounds like a nest of locusts live inside my laptop. The 2nd partition will not let me enable it. I can format it but nothing else. The drive isn't mounted either. I wonder what is the fastest and most convenient way to trim disk space eating software. Maybe I should take a look in synaptic and see if anything I don't need is there....

---

