---
title: "Im On Ubuntu baby!!! - Problems Problems! Help!"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-05-31
Hey all,
Finally I'm on Ubuntu...and its AMAZING!!! the installation was a piece of cake, except the partitioning, which took the hell out of me. Well, to be honest, it didn't work out as planned. I put on my dads hard disk to try ubuntu (which btw was totally empty!)
First I had problems with partitioning in the ubuntu live, it wouldnt let me access my drives or anything. Anyway i went back to windows deleted my created swap drive and everything else. And create one partition of 50 gb NTFS and left 30 gb as unformatted space.

So all went well, i loaded ubuntu live and created me partitions. But later on when i tried to install, it would ask me unmount my hda5, which i had no idea about. So to solve all problems, i deleted my NTFS partition and installed. It worked fine hence forth. Anyway my question is when i install ubuntu on my primary HDD, i have a major 200 gb NTFS partition. Which I cannot lose at ANY cost. So if anybody could tell me where i went wrong and what i could do next time to avoid these complications would be of great help!
thanks in advance
sibot!

---

### Post by LaRoza on 2007-05-31
The scenerio: Install Ubuntu next to a preexisting NTFS partiton.

Howto: 
First use windows to defrag the NTFS partition,

Second, backup the info, just in case

Third, start the install, but choose, either manual or resize and install to new space (uses a slider)
                     
 note: when you move the slider, the "free space" is where you are going to install Ubuntu, and the  
                                bar represents the existing partition.

-edit You said you cannot lose the 200 gig partition at ANY cost. If that is the case, I wouldn't do anything to the drive, like installing Ubuntu without having a full backup. If you have extremely important data, it is best to keep it on a seperate drive from your os, and idealy, as a RAID 5 configuration.

---

### Post by Inxsible on 2007-05-31
I would suggest to go with the manual partitioning. That way you know exactly where you want to create partitions.

---

### Post by sibot on 2007-05-31
yeah well, i got another problem now, everytime i start gaim, my ubuntu crashes...! hmmm gonna be rough ride

---

### Post by sibot on 2007-05-31
btw these restricted drivers i download from the net, where do they go? can i save the installer for further usage, when i format again?

---

### Post by candtalan on 2007-05-31
> **sibot said:**
> 
[...]
can i save the installer for further usage, when i format again?

A convenient way to examine partitons and edit them may be to make use of a GUI based partition editor such as Gparted which conveniently is available as a small live CD. I have always used it, and, for me, it makes things simple. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I confirm another comment here - that if you have priceless data then do not attempt to change partitons, errors and failures will instantly and brutally loose a great deal of data mostly irretrievably!

good luck!

---

### Post by lamalex on 2007-05-31
if you have uber important data than you should be backing it up anyway, drive failure is inevitable!!

---

