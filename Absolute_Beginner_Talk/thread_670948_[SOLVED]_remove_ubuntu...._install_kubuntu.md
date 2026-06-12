---
title: "[SOLVED] remove ubuntu.... install kubuntu"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2008-01-18
Hello,

I have a 40 GB HDD, I gave 20 GB to fat32 for windows and the other 20 GB partition is the ext2 format where ubuntu is installed.

I have been having problems with ubuntu recently and want to try out kubuntu.


so how do i install kubuntu,  should i format the ext2 partition? will that work? will that also destroy the GRUB menu at startup?

---

### Post by wolfen69 on 2008-01-18
```
sudo apt-get install kubuntu-desktop
```
then at login, you can choose which one to boot.

---

### Post by r4ik on 2008-01-18
Also read,

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Good luck !

---

### Post by aysiu on 2008-01-18
If you just want to *try* Kubuntu, consider running the Kubuntu live CD before installing it.

Otherwise, you can install it using [this tutorial](http://www.psychocats.net/ubuntu/kde), and if you like it so much that you actually want to get rid of Gnome, then you can follow [this tutorial](http://www.psychocats.net/ubuntu/purekde).

I don't see why you would need to remove Gnome, though.

---

### Post by faraz_k86 on 2008-01-18
I mean completely remove the ubuntu installation and do a fresh install.

---

### Post by r4ik on 2008-01-18
Just install Kubuntu on the partition (from disk) it wil be formatted auto and should replace grub.

---

### Post by faraz_k86 on 2008-01-18
so i dont have to remove ubuntu first, just install kubuntu?

cause I install y this method:

I usually leave 20 GB of the HDD unpartitioned and when installing I tell the installer to use the largest free space available.

so in this case how do i install kubuntu?


and will this affect my windows installation in any way?

---

### Post by r4ik on 2008-01-18
1. No.

2. Sounds good to me

3.No. (but alway's backup important data first to be sure)

---

### Post by faraz_k86 on 2008-02-09
sorry for digging out this old thread guys, but i  kinda got busy after asking this and plan on doing this now.


so lemme recap, I have 1 HDD, it has both windows and ubuntu installed on it.

I want to remove ubuntu and install kubuntu...

please note that i do not want the kde desktop, I want a fresh install of kubuntu.

so what i will do is to boot my laptop using a partioning tool and delete the linux partition...

hence I will ave free space available that is completely unpartitioned.

after this I will load up the kubuntu live cd... **Will windows even work after the partiton cahsnge will the grub loader or start up options be affected this way??**
[b]
I have a lot of important data on my windows partition and would hate to lose it, i cant back it up as it is a lot of data[/b]


and then i will install kubuntu.


Is this right??

i just want some one to give me the green signal on this method, so that I can proceed ..

---

### Post by overdrank on 2008-02-09
> **faraz_k86 said:**
> sorry for digging out this old thread guys, but i  kinda got busy after asking this and plan on doing this now.


so lemme recap, I have 1 HDD, it has both windows and ubuntu installed on it.

I want to remove ubuntu and install kubuntu...

please note that i do not want the kde desktop, I want a fresh install of kubuntu.

so what i will do is to boot my laptop using a partioning tool and delete the linux partition...

hence I will ave free space available that is completely unpartitioned.

after this I will load up the kubuntu live cd... **Will windows even work after the partiton cahsnge will the grub loader or start up options be affected this way??**
[b]
I have a lot of important data on my windows partition and would hate to lose it, i cant back it up as it is a lot of data[/b]


and then i will install kubuntu.


Is this right??

i just want some one to give me the green signal on this method, so that I can proceed ..

HI and as always **_BACK UP_** your data. You can just use the Kubuntu live cd and install on the same partition that contains Ubuntu. There is no need to delete the Ubuntu partition first.

---

### Post by Incense on 2008-02-09
> **faraz_k86 said:**
> 
I have a lot of important data on my windows partition and would hate to lose it, i cant back it up as it is a lot of data


You really **NEED** to find a way to back up that data. You're going to hit the wrong button someday and lose everything. You may want to get an external hard drive, or a DVD burner and just get all that important data backed up **today**. Once it's gone it's gone, and I would hate to see you lose all that just because you clicked the wrong radio button during an install. 

Plus you mentioned that you don't want the KDE desktop, you want Kubuntu. You do understand that Kubuntu is KDE right? It is slightly modified, but it's KDE nonetheless.

---

### Post by aysiu on 2008-02-09
I agree with Incense.

How important is that data to you? If it's important at all to you, then you should invest in some kind of backup medium (DVDs, external hard drive).

---

### Post by faraz_k86 on 2008-02-09
k thanks guys.

yes i know kde is kubuntu, and kubuntu is kde :)

i just bought meself a 4GB Flash, add that to my old 2GB flash and I have 6GB. Yay! I can backup my data now. :)


but none of you guys told me to go ahead your method is ok.

now that i have backed up my data, should i proceed as according to the method i posted earlier.

i just want to be sure this does not mess up my windows, as I have a lot of softwares and plugins installed and it will be a pain to install em again :)

me wait now :)

---

### Post by forrestcupp on 2008-02-09
Ok, if you really want to get rid of what you have, you can do that without problem.  You don't need to run a partitioner first because that is part of the Kubuntu installation.  When you get to the partitioning part, you just need to choose to do it manually.  Then you will highlight the ext3 partition and delete it. **Make sure you don't delete your NTFS partition that has your files and Windows.**  Then you will make a new partition with the free space setting it as ext3 file system with a mount point of '/' which is root.  Since it's a new partition, it should automatically be checked where it says format.  If you mess something up at this stage, it can be canceled, but if you mess it up and get to the point that it actually writes the partitions, you're screwed.

I can understand why you would want to get rid of your current install since you only have 20 GB dedicated to Ubuntu.  But like others said, make sure you back up any files on the Linux partition that you want to keep.  And it's always a good idea to back up very important files from your Windows partition just in case you screw up.

Edit:
And if you do this, you don't have to try to remove anything first.  It will just be deleted and formatted in the process.

---

### Post by Ghuloomo on 2008-02-09
I understand your need of making a fresh clean installation for ur kubuntu. You think it's like Windows you should format first, and put it all again, instead of upgrading.

First of all, you should define why u want Kubuntu? is it bcoz of its desktop environment (KDE)? or u want it's applications too? if only the desktop environment, just run sudo apt-get install kubuntu-desktop
If not, just put the Kubuntu installation disc, and when it reaches to partitioning, choose manual, and hit enter on the ubuntu partition, then choose delete, and then hit again on it and mount it for kubuntu. Don't worry it will automatically format it, and put kubuntu for you.

Come on, I'm giving you the green light :p ..

---

### Post by overdrank on 2008-02-09
> **faraz_k86 said:**
> k thanks guys.

yes i know kde is kubuntu, and kubuntu is kde :)

i just bought meself a 4GB Flash, add that to my old 2GB flash and I have 6GB. Yay! I can backup my data now. :)


but none of you guys told me to go ahead your method is ok.

now that i have backed up my data, should i proceed as according to the method i posted earlier.

i just want to be sure this does not mess up my windows, as I have a lot of softwares and plugins installed and it will be a pain to install em again :)

me wait now :)

HI and either way you choose to install, by installing the kubuntu desktop or a clean install of kubuntu will work just now you have your data backup and you can proceed. :)

---

### Post by faraz_k86 on 2008-02-10
thx a lot guys.

kubuntu is installed and working :D

---

### Post by Incense on 2008-02-10
Good job mate! Be sure to use the thread tools and mark this as solved. Have fun in KDE!

---

