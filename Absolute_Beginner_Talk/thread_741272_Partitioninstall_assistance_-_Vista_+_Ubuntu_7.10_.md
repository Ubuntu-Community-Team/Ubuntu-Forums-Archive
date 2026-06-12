---
title: "Partition\install assistance - Vista + Ubuntu 7.10 on same harddrive"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Bellicus on 2008-03-31
I got a cd with ubuntu 7.10 today. I already got windows vista home premium installed on the harddrive, and the harddrive is divided in 3 partitions. Running the cd works fine, got internet connection and sound without having done anything myself, so i'm thinking of trying to install ubuntu, but i want to keep vista too. **So what im trying to figure out is how to install ubuntu on my harddrive without overwriting any data or specially not to overwrite windows** (i dont got a cd for it). I'm adding a picture with what i imagine to be a list of the harddrive partitions. Witch of them is c, d and e: ?

---

### Post by Michael.Godawski on 2008-03-31
> Witch of them is c, d and e: ?
Well only you know what size is the c, d and e partition in Windows. Just compare the sizes.

When you click on the install icon on the desktop the installation of Ubuntu will start. There are when I remember correctly seven questions you have to answer. One of them is the partitioning part.

Select the "Manual" option and choose the partition on which Ubuntu should be installed.

Also before attempting to install Ubuntu make a back up of your important data and read through this guide.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Bellicus on 2008-03-31
Thanks for answering :)

The guide you linked to looks good, but i have one more question and this is a pretty important one. I cleared out my E: partition to use this for ubuntu. But unfortunatly the E: is almost the same size as the vista partition (C:). And even if i cleared the E: i cant find a partition on the ubuntu partition screen list with nothing on. The install screen shows a list of 4 partitions and i only got 3. So i am a bit confused. But i wrote down the sizes of the drives when checking from vista:

C: VISTA DRIVE 246 025 285 632 Byte 229GB -  43.9GB Used
D: GAMES 465GB
E: FREE PARTITION FOR UBUNTU 245 699 178 496 Byte 228GB - And this should have 0bytes used space, freshly formatted.

So the million dollar question is: When looking on my screenshot, witch is the E: partition?

---

### Post by Michael.Godawski on 2008-03-31
I guess it is sda3.Why? Please think with me, perhaps I have done some error.

C: VISTA DRIVE 246 025 285 632 Byte 229GB - 43.9GB Used is sda2 because there is also 47 GB used.

E: FREE PARTITION FOR UBUNTU 245 699 178 496 Byte 228GB should be sda3 
It is not free because perhaps Windows created some hidden files on it or I don't know what.

But let's wait for someone other to answer. This is a tricky question and the wrong answer may be painful.

---

### Post by Bellicus on 2008-03-31
I'm thinking sda3 too, It is slightly smaller, as it should be, and it got less used space as it should have. I just restarted vista, and made sure the trashcan was empty, i used ccleaner to wipe out all the trash, and i formatted again, but still, when checking the partition properties, there is 146mb used space. I have no idea what vista is using all this space for and why vista and ubuntu is telling me different stories about the partition, Maybe its a kind of system restore backup or something. But since we both agree sda3 should be the correct choice i'm just gonna go for it, and maybe someone can reveal the hidden mysteries of vista later. ;)

Thanks alot for your time Michael.Godawski

---

### Post by Duck2006 on 2008-03-31
As posted sd0,3 is your free space you made. this is a guide that may to install. The guide that "Michael.Godawski" gave you is a good one, this one is for ubuntu it help you a bit better..

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Bellicus on 2008-03-31
I tried to figure it out, and it turned out well. I guess something have changed since the ubuntu version in the first guide, cause the same stuff as in the guide didn't happen, but i figured it out with some help from the installer about making a root partition and a swap partition. After restarting i almost got a stroke cause when entering windows i got a weird error and some system backup tool started up, but when restarting one more time it was back to normal. I also got a neat start-up menu now where i can choose either vista or ubuntu. Downloading updates for ubuntu now, and gonna start working to find drivers and get some use of my hardware. Thanks for the guide Duck2006, maybe if someone else read this thread they find the info they need. :)

---

