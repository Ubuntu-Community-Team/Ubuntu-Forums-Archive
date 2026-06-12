---
title: "getting onto my drives in ubuntu"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by watchinthewhels on 2007-10-23
Ok im a total newbie to linux but I have a decent ammout of experience with computers unfortunatly it shows. I am stuck trying to access my drives. I have my machine setup with 2 physical HDD's both were previously formatted with NTFS for an XP install. 

I have installed kubuntu (I know its not ubuntu but its the same backend isnt it?) Unfortunatly I cant make head nor tail of what its done to my system. I can get into the OS and access the file system settings, but once there I am stummped

Its showing up as my primary drive formatted with EFS3 but only on a small partition, about the size of the OS itself. There are also about 4 other partitions showing up between 1-3Gb. I dont know what these are. There is also a disabled one thats the remaining 50 odd Gb of my primary drive. This is what im desperatly trying to get into.

I have tried changing its settings to NTFS and trying to mount it to a folder nut It wont let me anable it. It gives me errors about not being able to mount, it says something about it being an extended partition. This may be right but I never set the options for this and im not sure how to check what the partition is under linux. If it is an extended how would I access it anyway? I am happy to re-format the drive with efs or whatever the os wants but I cant find an option for that either.

any help is greatly appreciated, thanks.

---

### Post by quinnten83 on 2007-10-23
I use Ubuntu, so maybe I won't be of much help, but here goes:
- how did you install? did you do it manually or did you let kubuntu create the partitions for you?
- Which version of Kubuntu did you install, only 7.10 has native read/ write support for NTFS drives, the other version require you to install ntfs-3g.
- could you please copy paste the errors you are getting when you try to access the drives.
- and what happens when you click on the 50GB partition?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-23
```
sudo apt-get install gparted
```
then run gparted 
I find it is really good way to see whats going on with your drives
an extended partition is were you would put logical partions
a hard drive can only have 4 partitions unless you make some of em extended partittions then you can get 2 in each one of those so 

sorry not more help could you post more info

---

### Post by watchinthewhels on 2007-10-23
Thanks for the quick replies. I understand the theory behind the partitions etc but I just dont klnow how to manage them under linux. Do you need to mount a partition to be able to access it? is it not possible to simply get onto a partition? 

I dont know what type of partition the large one is, under windows I could find out by my main problem is simply not knowing where to look in linux (again total newbie to this). If I need to install a seperate app to manage it I will do that and see what I can do, im assuming I just put that code into the run dialogue?

Im not sure how I installed it tbh, i was in a bit of a rush. It gave me an option with a slider to select what I though was partition size. I selected the maximum size, thinking that would create an 80Gb partition including all free space and the OS. That was the first option on the screen and I assumed the default. I definatly didnt setup multiple partitions, or at least I didnt get the option of it.

---

