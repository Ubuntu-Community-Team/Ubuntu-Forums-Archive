---
title: "Disk Space Usage"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-17
I'm curious about how my disk space is being used.  I have dual boot with Windows, Ubunto on the second drive.  The first partition is /, 4 gig, the second is my old data storage, about 47 gig, the third is Swap, 1 gig, and the fourth is /home, 22.4 gig.  The Disk Manager shows only 15.5 gig free on the fourth partition.  I only recently installed Ubuntu and there is only a very small space used by the folders/files in /home.  I can't think of a way to have a look at the 7 gig that is being used--would appreciate some guidance.

Also, is any new package that I install placed in the root partition?  What can I do if and when that gets filled up?

Thanks,
Buck

---

### Post by JayTee on 2006-11-17
If you click on System | Administration | Disks it will run Disks Manager. You can view the information for each partition. It will show you the availabe plus used space on each partition. For a better view of how much space folders are using on a given partition you can download an application called Baobab. It will show you a tree view of a partition with the space used for each folder. To install it just click on Applications | Add/Remove and then click on Accessories in the left pane. Scroll down in the upper right pane until you see Baobab and click the checkbox there and then click apply and it will install.

---

### Post by Buck2348 on 2006-11-17
Thanks a lot, JayTee.  I thought there was something on the disk outside the Ubuntu file system.  "Properties" for a folder don't always show the size of everything that's in there.  It didn't take long to find the trouble with Baobab--I had some huge files in the trash.

Can you tell me how well I'm set up with my present partitions--almost 4 gig for root and 22.4 gig for /home?  I set it up this way because of a big partition in the middle that I didn't want to move.  Is all new software installed in the root directory, or will it move into /home when root gets full?  Right now I'm using 2.3 gig in root, and only a little less than 2 gig in /home.

Thanks again for your help.

Buck

---

### Post by Marsolin on 2006-11-18
4G should be plenty for /. All software gets installed there, but you would have to install quite a bit to use all of the space. If you do find yourself running low try executing "sudo apt-get clean" from the command line. It will clear out the cache of all the deb files that get saved with every upgrade and new installation. The directory that gets cleared is "/var/cache/apt/archives".

---

### Post by David Corrales on 2006-11-18
Software won't get moved from / to /home when it's full but / fills up very slowly, so unless you're having space issues on /, you'll be fine.
If the time comes, you can use the new GParted LiveCD which allows for moving partitions and resizing them. That way you can take some Gb's off home and move them to root.

---

### Post by computx on 2006-11-18
Two other good tools to use. from the console type df -h gives you available/used/free space on all mounted partitions.

Also try filelight. Displays disk useage in a pie chart broken down by folder and subfolder.

---

### Post by Buck2348 on 2006-11-18
Thank you all very much.  Just what I needed to know.

Buck

---

