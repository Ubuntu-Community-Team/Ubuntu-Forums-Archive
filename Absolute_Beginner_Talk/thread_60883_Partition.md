---
title: "Partition"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-29
Hi 

I wondered if people generally install the default or manually set up partitions.

this is my partition:

1.  /                  1.2Gb
2. /home                   i dedicated most of my 80 gb to home
3. /swap              1gb
4. /urs                  2.5gb
5. /var                   1.gb

or close to something like that. Can some one tell me which would be set as logical and the name of the others?

I'm looking at doing a reinstall. In [https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

what does, "From this point, you can select guided partitioning and the installer will calculate everything else for you." mean??

Basically i want to divide my 80 gig into two and create a dual boot. 40 gig should still be healthy for general desktop stuff.?

--
sophtpaw

---

### Post by c0rderr0y on 2005-08-29
i think 5 gigs total is plenty for /,var,usr as for the 1 gig swap really depends on how much ram you have on the system.  I have 1 gig ddr2 ram and havent used my swap yet (which is 512mb BTW).  hope this helps you out.

---

### Post by sophtpaw on 2005-08-29
[QUOTE=c0rderr0y]i think 5 gigs total is plenty for /,var,usr as for the 1 gig swap really depends on how much ram you have on the system.  I have 1 gig ddr2 ram and havent used my swap yet (which is 512mb BTW).  hope this helps you out.[/QUOTE]


First time i installed Ubuntu i did the default install. I now hear it is better to assign / ; /home ; /var ;  //usr ; and swap .

Can i have opinions advice and comments on the merits of only having one ext3 / and swap which is essentially the default install or manually configuring as said. 

In [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)  we are shown how he shaves some off the primary partition to add to and create a second larger partition for Ubuntu.

Does it work the other way too,  If i already have Ubuntu on my 80 gig can i shave some off to create enough to create another secondary partition to boot Mepis in my case. or, would anyone here know  :)  whether the mepis partitioner can shave someoff my primary (current ubuntu) as the ubuntu partitioner did to the xp. If you follow my drift  :-? 

--
sophtpaw


In theory couldn't i follow the instructions on  [http://www3.telus.net/linux4u/ubuntu2.html](http://www3.telus.net/linux4u/ubuntu2.html)

to shave some of my 80gb ubuntu install and create a dual boot ubuntu / ubuntu install. then i could just write over one of 'em?

Would love to hear from anyone who has wanted to creat a dual boot without having to destroy his primary install to have to start all over again. 

any advice, comments, pointers? welcome,

thank you,

sophtpaw

---

### Post by az on 2005-08-29
> **sophtpaw]First time i installed Ubuntu i did the default install. I now hear it is better to assign /  said:**
> http://www3.telus.net/linux4u/ubuntu.html[/url]  we are shown how he shaves some off the primary partition to add to and create a second larger partition for Ubuntu.

Does it work the other way too,  If i already have Ubuntu on my 80 gig can i shave some off to create enough to create another secondary partition to boot Mepis in my case. or, would anyone here know  :)  whether the mepis partitioner can shave someoff my primary (current ubuntu) as the ubuntu partitioner did to the xp. If you follow my drift  :-? 

--
sophtpaw


You can grow and shrink partitions and move the data around.  Just as long as you have enough space to do it.  Do not do it just for fun because there is always the change that you lose some data.  Not a big change, just do not go crazy.

There is no advantage to not having everything on a single partition.

If you have special needs, like if you are an internet service provider or if you are running a webserver, you do not want your root partition to get full if someone spams you, then there is a reason to create different partitions.  Otherwise, there is absolutely no need to create anythig more than just one root and one swap partition.

Is 40 gigs enough?  That depends on what you do with it.  Out-of-the-box, Ubuntu takes up less than 2 Gigs of space.  Unless you are saving thousands of photos of your newborn, you will not need much more than five or ten gigs of space for typical office or desktop use.  It depends on your needs.

---

### Post by az on 2005-08-29
[QUOTE=sophtpaw]what does, "From this point, you can select guided partitioning and the installer will calculate everything else for you." mean??[/QUOTE]


It means that you can boot the installer, free up some space and then let the installer decide what to do with that space.   It will make one root and one swap partition.  It will calculate your available space and how much memory you have and decide how big a swap partition you should use.

---

### Post by sophtpaw on 2005-08-29
[QUOTE=azz]You can grow and shrink partitions and move the data around.  Just as long as you have enough space to do it.  Do not do it just for fun because there is always the change that you lose some data.  Not a big change, just do not go crazy.

There is no advantage to not having everything on a single partition.

If you have special needs, like if you are an internet service provider or if you are running a webserver, you do not want your root partition to get full if someone spams you, then there is a reason to create different partitions.  Otherwise, there is absolutely no need to create anythig more than just one root and one swap partition.

Is 40 gigs enough?  That depends on what you do with it.  Out-of-the-box, Ubuntu takes up less than 2 Gigs of space.  Unless you are saving thousands of photos of your newborn, you will not need much more than five or ten gigs of space for typical office or desktop use.  It depends on your needs.[/QUOTE]

Thank you Azz,

So, i can load my Ubuntu disc in the tray and shrink my partition? If you were me how would you now basically divide my 80 gigs in two so that i can have a dual boot?

thx again,

--
sophtpaw

---

### Post by aysiu on 2005-08-29
[QUOTE=azz]Otherwise, there is absolutely no need to create anythig more than just one root and one swap partition.[/QUOTE] I generally agree. In fact, that's what I have, and it's fine. However, there are some people who create a separate /home partition, and there's an advantage to that. If you reinstall a fresh distro (either a newer version of the same distro or another distro entirely), you can keep all your settings and preferences intact without having to back them up.

I know some people like to just *sudo apt-get dist-upgrade*, but others like to do a clean install.

---

### Post by az on 2005-08-29
I do not know you.

If I had a 40 gig drive(I do), I would not run windows on it.  I would quadruple boot Hoary, Breezy, Debian Sid and Debian Woody(Don't ask).  

It depends on what you do.  What are your needs from either operating system you want to dual boot?

---

### Post by aysiu on 2005-08-29
Yes, describe more your needs.
For example, I need a small Windows partition, a partition to share files between OSes, and I like Mepis and Ubuntu... and I like to try out other new distros on whim.
So I have a small Windows XP (NTFS) partition, a large FAT32 partition for my files, a small swap, and three Linux partitions, with Ubuntu's Grub on the MBR quadruple-booting all four OSes.

But that's me.

What are your needs?

---

### Post by sophtpaw on 2005-08-30
What are your needs?[/QUOTE]


I thought i was clear. I would like to share my 80gb between two distributions. Ubuntu and Mepis right now. Basically i want one stable installation, and the other partition to try other things, learn and mess about and be able to make mistakes without fear, knowing i have my other os to fall back on.

Since, i had dedicated all 80gb to Ubuntu i want to know whether i can shave someoff /home to create this partition for a dual boot.

Do please read the threads properly before asking what it is i want, and thank you for wanting to help again


--
sophtpaw

---

### Post by poofyhairguy on 2005-08-30
[QUOTE=sophtpaw]
I thought i was clear. I would like to share my 80gb between two distributions. Ubuntu and Mepis right now. Basically i want one stable installation, and the other partition to try other things, learn and mess about and be able to make mistakes without fear, knowing i have my other os to fall back on.
[/QUOTE]

Smart!

---

### Post by az on 2005-08-30
[QUOTE=sophtpaw]

Do please read the threads properly before asking what it is i want, and thank you for wanting to help again


--
sophtpaw[/QUOTE]


Here is what I said about it yesterday:
"
Is 40 gigs enough? That depends on what you do with it. Out-of-the-box, Ubuntu takes up less than 2 Gigs of space. Unless you are saving thousands of photos of your newborn, you will not need much more than five or ten gigs of space for typical office or desktop use. It depends on your needs."


Now, I re-read the thread eight times, now.  I still do not know if you spend your days swapping DVD images over the net, or edit home movies and store large amounts of data from the Genome project on your hard drive or if you just have modest needs such as casually browsing the internet and reading your email from yahoo and bidding on lawn chairs from Ebay..

You cannot expect me to assume what your needs are out of an operating system.  I am sure that it is perfectly clear to you, but it is not obvious to any one else.

You would be able to use a partition as small as three Gigs in size all the way to needing a few additional 120 gig-hard drves on a raid array.

Please assume that people are *not* stupid before answering.  Thanks.

---

### Post by sophtpaw on 2005-08-30
[QUOTE=azz]Here is what I said about it yesterday:
"
Is 40 gigs enough? That depends on what you do with it. Out-of-the-box, Ubuntu takes up less than 2 Gigs of space. Unless you are saving thousands of photos of your newborn, you will not need much more than five or ten gigs of space for typical office or desktop use. It depends on your needs."


Now, I re-read the thread eight times, now.  I still do not know if you spend your days swapping DVD images over the net, or edit home movies and store large amounts of data from the Genome project on your hard drive or if you just have modest needs such as casually browsing the internet and reading your email from yahoo and bidding on lawn chairs from Ebay..

You cannot expect me to assume what your needs are out of an operating system.  I am sure that it is perfectly clear to you, but it is not obvious to any one else.

You would be able to use a partition as small as three Gigs in size all the way to needing a few additional 120 gig-hard drves on a raid array.

Please assume that people are *not* stupid before answering.  Thanks.[/QUOTE]


What i want to do with my dual-boot is not relevant. I gave a list of my partitions and said i had 80 gb and that i wanted to create a dual boot. 
Specifically i wanted to create a dual boot without destroying the already existing os (Ubuntu). What inspired me was finding a  link i found and which i  copied to the thread, the example of which, uses  xp on an ntfs and 'shaving' (his/her word) as much as one wants without destroying the existing os. But because ntfs is one whole file as it were i wondered if i could follow the same instructions and apply it to my Ubuntu. As i had Ubuntu setup with  many files or partitions i wondered if it would still be possible. Therefore i asked a) if it is possible and b) specifically how you would have me 'shave' some (as much as i would want) off my existing /home  to enable me to create safely another parittion for creating a dual boot. How much i would want to would indeed depend on my need and usage, i agree, but that was not ever my question.

I'm sorry if i didn't make my question clear enough or if there was otherwise a misunderstanding. 

I went ahead anyways as best i could, only now coming to the point, and it seems i now have a dual boot.
I loaded my Ubuntu cd into the cdrom tray and went ahead as if i was doing an install and at partitioning i edited my /home file (50/50) after which Ubuntu carried on its install. The net result being that i have an Ubuntu / Ubuntu computer. 

the idea now is to Install Mepis over the new install, and then i will have achieved the Mepis/Ubuntu dual boot as set out without destroying either the original install. 

In CLI i typed:
sudo fdisk /dev/hda 


The number of cylinders for this disk is set to 9964.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         697     5598621   83  Linux
/dev/hda2             698         843     1172745   82  Linux swap / Solaris
/dev/hda3             844        6096    42194722+   5  Extended
/dev/hda4   *        6190        9964    30322687+  83  Linux
/dev/hda5             844        1876     8297541   83  Linux
/dev/hda6            1877        2229     2835441   83  Linux
/dev/hda7            2230        6096    31061646   83  Linux

My question now is have i really got a dual boot? Effectively i do because i i can choose in Grub whether i want to go into one or the other. But on here something doesnt look right.  
Especially when matched up with
df -h

conrad@x1-6-00-0b-6a-16-78-f0baraka:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4              29G  1.5G   26G   6% /
tmpfs                 126M     0  126M   0% /dev/shm
/dev                   29G  1.5G   26G   6% /.dev
none                  5.0M  2.8M  2.3M  56% /dev

Do things match up? I'm not clear that my new install is its own partition and not part of the original makeup. Sorry i don't know how to articulate intelligently or clearly my question here. 

Really appreciate somebody's expertise and input on this. 


cordially,


sophtpaw

---

### Post by az on 2005-08-31
[QUOTE=aysiu] who create a separate /home partition, and there's an advantage to that. If you reinstall a fresh distro (either a newer version of the same distro or another distro entirely), you can keep all your settings and preferences intact without having to back them up.[/QUOTE]


I did that and got bitten in the ass.  I maintained a debian Sid box remotely for my brother's desktop.  Somewhere between KDE3.0 and KDE3.2 the KDE settings were completely wrong and the desktop slowly stopped working.

I would periodically install sid and check KDE's stability and could not find any problems.  When I finally told him to create a new user and try that, everytying was fixed.  It would seem that saving settings in that manner is not always successful.

---

### Post by savage on 2005-09-02
I may be wrong but I would guess that whatever installation you are currently booting into when running 'df -h' (probably your initial install) doesn't know about the new partition you just "shaved" off. It doesn't need to know about the other install unless you want to move files between the two. In which case you can use the mount command on /dev/hda7 and versa-vice for your new install. For something more permanent you will need to edit your fstab file in each installation so they can be nice lil buddies.

---

