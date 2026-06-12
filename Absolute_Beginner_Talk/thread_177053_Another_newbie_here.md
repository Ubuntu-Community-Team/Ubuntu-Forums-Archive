---
title: "Another newbie here"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by ki2 on 2006-05-15
Hi All,
This is my first post here.
Thanks to all the experienced users posting replies for us newbies, making Ubuntu a stronger community.
I just installed Ubuntu, on my Dell Latitude C840 and got everyting to work on a Win Xp Pro Dual Boot -after having to wipe off my entire HDD, still worth it.

I have 2 Simple questions
I can see my windows Partition- I want to be able to pull data from that partition and write to it- _How can I do that -it says That do not have permissions to access that area
I wanted to use LILO and a have a splash image at startup, how do I enable that

Thanks for all your help.
Have a Good Day!
Ki2

---

### Post by aysiu on 2006-05-15
[QUOTE=ki2]I can see my windows Partition- I want to be able to pull data from that partition and write to it- _How can I do that -it says That do not have permissions to access that area[/QUOTE] If your Windows parition is NTFS, you won't be able to write to it. You'll be able to read from it, though.

If it's FAT32, you can read from it or write to it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ki2 on 2006-05-15
Thanks aysiu, I was reading your essay on "http://www.psychocats.net/essays/linuxswitchstory.php" My Switch to Linux, Interesting read, I have had a similar experience.
If I am not able to write on the NTFS partition, a better way to go would be to have a common HDD for both Ubuntu and Windows- Can Both the OS write to a SCSI HDD on NTFS or Fat32?
How do I download and Install Thunderbird? It is Not listed in the Synaptic
Thanks Again for your help- and off course anynone helping me out here.

---

### Post by aysiu on 2006-05-15
[QUOTE=ki2]If I am not able to write on the NTFS partition, a better way to go would be to have a common HDD for both Ubuntu and Windows- Can Both the OS write to a SCSI HDD on NTFS or Fat32?[/quote] You can access Ext3 (Linux) partitions from Windows using [http://www.fs-driver.org/](http://www.fs-driver.org/)  > How do I download and Install Thunderbird? It is Not listed in the Synaptic It should be in Synaptic. If you want the absolute latest version (1.5.0.2), use [this script](http://www.ubuntuforums.org/showpost.php?p=1014486&postcount=50)--just ignore the third and fourth line about the *undo* script.

---

