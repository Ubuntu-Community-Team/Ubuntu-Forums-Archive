---
title: "Installation stage 4 problem."
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by T4K3Z0U on 2007-09-05
Hi all, 
I have searched the forums quite a bit and cannot seem to find the info that I am looking for.

When I get to stage 4 of the installation "prepare disk space" I am presented with the following options.

Guided-use entire disk SCI1 (0,0,0) partition #5 & use free space. (not sure what to make of that because my drive only has 3 partitions)

Guided-use entire disk SCS! (0,0,0) (SDA) 100GB ATA ST9100824A

Guided-use the largest continuous free space

Manual.


So at first I tried the manual option but, I got a message saying "root menu not defined" or something to that effect.
I went backward and tried the first option and was presented with this message. "before you can select a new partition size, previous changes must be written to disk. You cannot undo this operation."
I went ahead and clicked ok and waited and waited, but nothing happened, so I went back and well long story I tried all 4 of the options but got nowhere, I am at a total loss and even the person who recommended it to me, is unable to help.


Now I was to understand that I can have both Windows XP and Ubuntu on my PC so in effect I don't need to nuke my hard drive for installation, is this correct? The only reason I want to keep Windows is because I have too many files to back up, so I'd rather not lose them, if you know what I mean.
Are you able to give me some pointers and help me get past stage 4 of the installation process?

Thanks everyone.

---

### Post by por100pre1 on 2007-09-05
The easiest way would be to use the **Guided-use the largest continuous free space** option but first you need to shrink your xp partition with Gparted (included in the LiveCD) or a 3rd party tool like Partition Magic.

EDIT: Be sure to backup your Windows files first, to attempt to shrink any partition can be risky!

---

### Post by T4K3Z0U on 2007-09-05
> **por100pre1 said:**
> The easiest way would be to use the **Guided-use the largest continuous free space** option but first you need to shrink your xp partition with Gparted (included in the LiveCD) or a 3rd party tool like Partition Magic.

So when I D/Ld Ubuntu that would have been a live CD after I burned it yea?
Um how do I access Gparted? I guess I tried to install wrong? I restarted pc and put cd in and went from there.

Sorry but I do know nothing apart from basics, send an email, surf the net and play some games. :redface:

---

### Post by por100pre1 on 2007-09-05
> **T4K3Z0U said:**
> So when I D/Ld Ubuntu that would have been a live CD after I burned it yea?

If it looks like [this]("http://www.cs.cornell.edu/~djm/ubuntu/screenshots/feisty/01.png"), yes, it is the LiveCD.

> **T4K3Z0U said:**
> Um how do I access Gparted? I guess I tried to install wrong? I restarted pc and put cd in and went from there.

Sorry but I do know nothing apart from basics, send an email, surf the net and play some games. :redface:

No problem, we are glad to help. New users are always welcome. Look for GParted or Gnome Partition Editor, once opened it should look like [this]("http://www.elart.it/kubuntu/GParted.png").

You may need to defragment your Windows files and do some Disk Cleanup before shrinking it's partition so take your time, and don't forget to backup your files. :)

---

### Post by T4K3Z0U on 2007-09-05
> **por100pre1 said:**
> If it looks like [this]("http://www.cs.cornell.edu/~djm/ubuntu/screenshots/feisty/01.png"), yes, it is the LiveCD.

Yes it looks exactly like that.

> **por100pre1 said:**
> 
No problem, we are glad to help. New users are always welcome. Look for GParted or Gnome Partition Editor, once opened it should look like [this]("http://www.elart.it/kubuntu/GParted.png").

You may need to defragment your Windows files and do some Disk Cleanup before shrinking it's partition so take your time, and don't forget to backup your files. :)

Ok just confirming I'm on the right page as you. I need to look for Gnome Partition or GParted before I click the install button, is this correct?

---

### Post by T4K3Z0U on 2007-09-06
OK I have tried to shrink the partition using GParted but it keeps giving me an error message saying it cant shrink it for me. The size of the Partition is 48GB with 22GB free, is this not enough space?

The specs as best I can give you are:

2GB RAM
100GB HDD
Its an Compaq V2020AP notebook with centrino. 
1.7ghz if I recall correctly.

I am pretty much a beginner and I am starting to lose faith in Ubuntu as this is now day 4 of trying to install.

---

### Post by por100pre1 on 2007-09-06
> **T4K3Z0U said:**
> OK I have tried to shrink the partition using GParted but it keeps giving me an error message saying it cant shrink it for me. The size of the Partition is 48GB with 22GB free, is this not enough space?

The specs as best I can give you are:

2GB RAM
100GB HDD
Its an Compaq V2020AP notebook with centrino. 
1.7ghz if I recall correctly.

I am pretty much a beginner and I am starting to lose faith in Ubuntu as this is now day 4 of trying to install.

22G will do for a small installation. Sorry for the delay, I was in bed. it is 6:00 AM here.

---

### Post by T4K3Z0U on 2007-09-06
> **por100pre1 said:**
> 22G will do for a small installation. Sorry for the delay, I was in bed. it is 6:00 AM here.

No probs, its 8pm here. only 8pm here.

So if 22GB is technically enough then why does GParted not seem able to shrink it?
I have a 2nd partition which is 24GB would that be better? although I'm to understand both OS need to be on the c:/ to dual boot, is that right?
Oh I don't know how, but if I could, there is no problem for me to merge the 24GB partition in with the main one if that will make things better.

---

### Post by antoz on 2007-09-06
If you have nothing on that other 24 GIG partition you could just delete it, leave it as unlalocated, and install Ubuntu there.
Ubuntu will create it's own partition **not** use your C drive which obviously is Windows if you are going to dual boot

---

### Post by T4K3Z0U on 2007-09-06
Ok so I just did that this minute. (deleted the 24GB partition) Now the main partition and my smaller 19GB ones have padlocks beside them, Is this anything to be worried about?

Now that its unallocated can I go ahead with the install or is there something else I need to know?

---

### Post by por100pre1 on 2007-09-06
Those are mounted (in use by the operating system) right-click them and click unmount to unmount them and leave them alone...

EDIT: If you feel ready now install with the Guided-use the largest continuous free space option.

---

### Post by T4K3Z0U on 2007-09-06
> **por100pre1 said:**
> Those are mounted (in use by the operating system) right-click them and click unmount to unmount them and leave them alone...

EDIT: If you feel ready now install with the Guided-use the largest continuous free space option.

So they normally mount like that after deleting a partition? I need to unmount them? or I can just install like that?

Just trying to make sure I'm not going to screw it up. :)

---

### Post by por100pre1 on 2007-09-06
> **T4K3Z0U said:**
> So they normally mount like that after deleting a partition? I need to unmount them? or I can just install like that?

Just trying to make sure I'm not going to screw it up. :)

Gparted mounts the partitions to look at them. Not sure if it is necessary, but go ahead and right click any disks you see on the desktop in click unmount. Then click the Install icon to start setting up your installation and go ahead with the install.

---

### Post by T4K3Z0U on 2007-09-06
> **por100pre1 said:**
> Gparted mounts the partitions to look at them. Not sure if it is necessary, but go ahead and right click any disks you see on the desktop in click unmount. Then click the Install icon to start setting up your installation and go ahead with the install.

Doing that now. Thanks for your help. I will update you soon.

When doing new things, I have a motto. "It's better to go slow and get it right the first time, than to go fast fudge it up and have to start again"

*note: Replace fudge with appropriate word.

---

### Post by por100pre1 on 2007-09-06
> **T4K3Z0U said:**
> Doing that now. Thanks for your help. I will update you soon.

When doing new things, I have a motto. "It's better to go slow and get it right the first time, than to go fast fudge it up and have to start again"

*note: Replace fudge with appropriate word.

Agree with you. Glad to help. Lets us know how everything works when finished.

---

### Post by T4K3Z0U on 2007-09-06
> **por100pre1 said:**
> Agree with you. Glad to help. Lets us know how everything works when finished.

It seems to have worked. I rebooted into Ubuntu without the cd so thats good. Haven't tried booting into XP just yet, might do that in the morning.

Now I'm going to research Beryl coz that looks very Gucci. Then off to tell my mayes to get with the program. (pun intended)

Thank you again por100prel and antoz.

---

### Post by T4K3Z0U on 2007-09-06
Excellent, Windows booted fine as well this morning.

---

