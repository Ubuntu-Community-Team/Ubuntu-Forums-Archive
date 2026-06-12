---
title: "Going to install and have a duel boot system"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by aggscott on 2007-01-20
Good Morning all,

I woke up bright and early this morning so that I could install Ubuntu on my laptop-alone. Three children can sure make you miss a few steps!:KS 

Last night I put the live CD in and went half way there-I wanted to see what happened when I pressed the install button and how it would partition the drive. It did everything that it was suppose to.

So anyone else out there have a duel boot system with Windows XP? Anything I should know before I jump? 

I have the live CD which is a great thing. I like the idea that they let me look at it and play with it before I install. I think that is what caught my eye yesterday when I bought the magazine. I can look through it and play with it before I install? Cool!


One thing I want to ask is that when I did put the CD in and was on the desktop I could not go on the internet. Is that normal or not?  I have a wireless network set up. I guess you would have to set up Firefox with it? That's wht I'm guessing but, I could be wrong...

O.K. I'm going to go and get started-

Aggie

---

### Post by housam on 2007-01-20
My advice is to back-up every thing before installing . " just in case"

---

### Post by xpod on 2007-01-20
And possibly defragment your windows a couple of times before any resizing:D 

You certainly got the right idea with regards to the little distractions though.I cant think when my 5 are running riot?](*,) 

Good luck

---

### Post by aggscott on 2007-01-20
I was just looking through everything to see if anything needs to be backed up but, two days ago I cleaned it and re-installed Windows XP. I actually have nothing left. All my personal things are on the desktop, which is the main computer in the house. The laptop is my husbands' and mine-no kids allowed!



But, I will run the defrag before I do it-good idea. It shouldn't take to long-that's for sure!

Aggie

---

### Post by Canis familiaris on 2007-01-20
Along with the C: in Windows (probably formatted NTFS), set up a shared FAT32 drive(size<32GB) and install Ubuntu in a logical drive in extended partition.
For more info on setting up your partition refer to this thread:
[http://ubuntuforums.org/showthread.php?t=338258]("http://http://ubuntuforums.org/showthread.php?t=338258")

> **aggscott said:**
> 
One thing I want to ask is that when I did put the CD in and was on the desktop I could not go on the internet. Is that normal or not?  I have a wireless network set up. I guess you would have to set up Firefox with it? That's wht I'm guessing but, I could be wrong...

If your network in via DHCP then, it' is the problem may be due to the wireless network. Please search support in the forums about setting up your wireless network (or you may try to sort it out yourself :wink: )

---

### Post by Zaffe on 2007-01-20
U dont really need a fat32 shared partition, linux can read/write ntfs now, read this:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

If u have a broadcom wireless card u will need to do some configs.

---

### Post by aggscott on 2007-01-20
How do you find what type of wireless card you have? I have only the one that was installed when we purchased it. We never added anything extra. It's a Compaq Presario if that means anything...

Aggie

---

### Post by housam on 2007-01-20
Check the device manager.

---

### Post by shareMenaPeace on 2007-01-20
Or open a terminal and type

> lspci

---

### Post by housam on 2007-01-20
Or you can go for all programs >> accessories >> system tools >> system information >> components

---

### Post by mikewhatever on 2007-01-20
Wireless doesn't always work with LiveCD. In System->Administration->Networking, you should have a wireless option. Properties is the place to enter your network information. There is no network manager on LiveCD, so you can't see the networks around, but there are several to get from Ubuntu repositories after installation. Good luck.

---

### Post by aggscott on 2007-01-20
O.K. first problem-when I get to the part where it asks about partioning it does not have the option to duel boot? 
the first choice is erase the entire hard drive
the second is use largest free space and the third is manual edit...what happened to the first option? Where you can do the duel boot? 

Aggie

---

### Post by mikewhatever on 2007-01-20
If you have previously freed room for Ubuntu on your HD, use 'the largest free space option'. If not, you need to edit partition manually.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

read these guides first!!!

At the end of the installation, you'll be prompted to install GRUB to your MBR. GRUB is a boot manager that gives you the choice of loading Windows or Ubuntu.

---

### Post by housam on 2007-01-20
When you choose the 2nd option ,it w'll resize your windows partition and create another 2 partitions for ubuntu to be installed. and also it w'll install the Grub boot loader which w'll allow for the dual boot.

---

### Post by housam on 2007-01-20
I've posted the following before and it may help you.
> I prefer to manage the partitioning manually to put every thing under control. You have to keep windows in a separate partition and create another 3 partitions for ubuntu.
Using the partitioning tool Gparted you can devide the unallocated space to the following partitions as an examples:
- 10 - 15G ext3 ( / ) for root
- 1G swap ( useless if more than 1G , you may not use it ever if you have 1G RAM or more.)
- 10-15 Gb is ext3 for /home
Remember that you can only create 4 primary partitions on your HDD. if you need more partitions you can change the 4th primary partition to be an extended one. and that one can be devided to what ever you want.
After creating the partitions you can go for the installation.

---

### Post by aggscott on 2007-01-20
I didn't make room for anything actually but, I did just redo Windows XP and I have nothing on the computer but the OS and all the drives and things but, that's it. I just reinstalled it about two or three days ago. 

If I decide to go with the largest free space available- will that bump out Windows XP?

 I would feel better if it looked like the screen I see on the installation process that you showed me. The one that shows how it will make room and fit both for a duel boot drive. 

Aggie

---

### Post by housam on 2007-01-20
> **aggscott said:**
> 
If I decide to go with the largest free space available- will that bump out Windows XP?


NO, it won't do any harm to your windows.

---

### Post by mikewhatever on 2007-01-20
If there is no free room to make Ubuntu partitions, one of your existing partitions needs to be resized. LiveCD can do it too, and it is shown in the guides.

---

### Post by aggscott on 2007-01-20
Thank you so much for your help! I didn't think it would hurt Windows but, I wanted to make sure. I pressed the install button and it has begun..I am so happy that I found this OS-I have always loved Linux and the way it looked compare to Windows but, my family can not live with out Windows. I can but, they can't. 

I will let you know how it goes and thanks again for all the help given.

Aggie

---

### Post by mikewhatever on 2007-01-20
The point of dual booting is to have Windows and Ubuntu. In my case, for example, I had Windows installed on 75 GB NTFS partition. In order to install Ubuntu, I shrank that partition to 50 GB, and created new partitions for Ubuntu in the freed space. That's why Ubuntu installer is so great.

---

### Post by housam on 2007-01-20
> **mikewhatever said:**
> The point of dual booting is to have Windows and Ubuntu. In my case, for example, I had Windows installed on 75 GB NTFS partition. In order to install Ubuntu, I shrank that partition to 50 GB, and created new partitions for Ubuntu in the freed space. That's why Ubuntu installer is so great.
You are right, but many people know a little about partitioning and want ubuntu to do the job for them.

---

### Post by aggscott on 2007-01-20
Well I'm done-it was really fast! When the computer reboots it asks what OS you want to boot into-very cool. Now if I could get the internet to work...that's my next thing now. Firefox is not set up for my wireless network. I need to figure that out now..


Aggie

---

### Post by mikewhatever on 2007-01-20
Glad the installation went smoothly. I was holding fingers for you. Start a new thread to get your wireless sorted out.

---

### Post by aggscott on 2007-01-20
Well that went very smooth:D  I mean it I'm on Firefox, on the internet on my laptop! 

I just updated everything, went and changed a few things that were easy to understand and that was it. I'm on and so far so good.


Now to explore everything and play, play, play! 


Aggie

---

### Post by housam on 2007-01-20
> **aggscott said:**
> Well that went very smooth:D  I mean it I'm on Firefox, on the internet on my laptop! 

I just updated everything, went and changed a few things that were easy to understand and that was it. I'm on and so far so good.


Now to explore everything and play, play, play! 


Aggie

Glad to here that you are on-line under ubuntu. Welcome to ubuntu world.
if you have any question, you just ask. this forum is great.

---

