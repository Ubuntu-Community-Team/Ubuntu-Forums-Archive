---
title: "replace hard disk"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by tompie on 2007-09-22
Hi everybody,

the HD in my PC needs to be replaced. 
I would like to avoid having to reconfigure the new hard disk into the same partitions and the Reiserfs. 
But more important, is there a way to avoid that i have to download again all the software I added after the installation of Ubuntu7.04 from the live CD.
Of course I know how to put in the new had on the IDE bus as a slave next to the old HD.


thanks for the help,
tom.

---

### Post by JNowka on 2007-09-22
> But more important, is there a way to avoid that i have to download again all the software I added after the installation of Ubuntu7.04 from the live CD.

The most simple way would be to burn everything in the /var/cache/apt/archives folder onto a cd or dvd and afterwards just copy them back after you fix your repositories.

You could go as far as going to the cd and typing in sudo dpkg -i *.deb and that would install all the packages at once.

Just remember if doing the dpkg method, to do a sudo apt-get autoclean before you burn the files to a cd or dvd

---

### Post by wieman01 on 2007-09-22
You could back up your entire HD, then partition then new one, and copy the old files back to the new drive. I have done that once, it is relatively simple if you use "Partimage". This way you don't have to reinstall at all.

---

### Post by hessiess on 2007-09-22
just put both hd,s in, and copy evrything onto the new one:)

---

