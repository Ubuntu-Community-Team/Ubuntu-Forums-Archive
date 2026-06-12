---
title: "ubuntu with winxp a beginer's question"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by arai on 2006-12-03
I have a 80 GB harddisk with 40 GB (ntfs) allocated for winxp and 3 fat32 partitions for storing files. one of the partition is 13 GB and i want to make it Ubuntu now. 

I have a doubt here. I previously had winxp (ntfs) and ubuntu on fat32 dual sometime back. i had to reinstall winxp for some reason and when i reinstalled xp i saw ubuntu missing. i also missed the hard disk space. 

so i formatted harddisk completely and then reinstalled winxp to regain my hard disk space. one reason i hesitate to go linux is when you reinstall windows xp the linux partition gets lost. is there a way to recover it without reinstalling linux again ?

---

### Post by noneofthem on 2006-12-03
Hey there!

If you wanna make sure you don't mess up your Windows partition I would recommend you to download and use the alternate CD for Ubuntu. This version will give you a text based installation with more options.

When you get to the partition manager please make sure you do not touch the windows partition and when you are asked if GRUB should re-write the MBR, select YES.

You should not get any problems when using the alternate CD. However, as always, make a backup of your most precious data before doing such a major thing to your computer.

If you need any more help just ask... :-)

---

### Post by Stew2 on 2006-12-03
Yes, all you have to do is reinstall grub and you will be able to boot into Ubuntu again (not after you reformat the whole drive though, then it is gone). There are quite a few threads on the forums about "reinstalling grub". Hope this helps.:) 
Edit: Here is a [thread about reinstalling grub]("http://www.ubuntuforums.org/showthread.php?t=224351") for you to check out.

Regards,
Stew2

---

### Post by arai on 2006-12-03
good. is 20 gb hard disk partition enough for ubuntu installation? i am going to install ubuntu 5.10 (i have the cd). 

please give a good partition manager so that i combine two 10 gb partitions (fat32) into one partition for ubuntu. thanks.

---

### Post by AirAshby on 2006-12-03
The partition manger used during the installation on the %.10 disc is fine just select Manually edit partition table

---

### Post by arai on 2006-12-03
thanks all. will come again if i get into some trouble.

---

### Post by bulldog on 2006-12-03
I should download the 6.06 Dapper Drake version it has LTS [Long Term Support]

Download the Gparted live cd [25MB] burn it to a disk and boot from it.
Now you can resize your partitions a little easier.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

And when you reinstall windows for some reason,just reinstall GRUB with the Ubuntu live cd and your ubuntu is on track again.

Good luck.

---

### Post by seshomaru samma on 2006-12-03
Linux didnt get lost . Windows cannot see it thats all.
Reinstall Grub and you'll be OK
Please don't install Breezy (5.10), it will be hard for you to find support for it .go for Dapper (forgot the number , starts with 6..), it is much more stable and has a long term support
Dapper comes with a good graphic partitioner that will help you combine two 10GB partitions into one. yes 20GB is enough.
good luck

---

