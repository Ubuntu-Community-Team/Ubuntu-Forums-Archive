---
title: "/home partion questions"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by mntamimi on 2008-03-13
Hi, I am rather new to ubuntu and linux and had a couple questions regarding the /home. I've been reading (here and elsewhere) about advantages of separating out the /home on to its own partition, but to be honest they kind of go over my head. 

Could someone explain to me what the purpose of a /home partition is? What goes in the home partition and what goes in the other partition (root?)? And what are the advantages and disadvantages of partioning it out?

Also, if I had a multiboot system, with a couple of different distros would they share a single home partition or would they each need there own? If it could be either way, are there problems with or issues with either choice?

Thanks for any help, explanations, or answers!

---

### Post by billgoldberg on 2008-03-13
> **mntamimi said:**
> Hi, I am rather new to ubuntu and linux and had a couple questions regarding the /home. I've been reading (here and elsewhere) about advantages of separating out the /home on to its own partition, but to be honest they kind of go over my head. 

Could someone explain to me what the purpose of a /home partition is? What goes in the home partition and what goes in the other partition (root?)? And what are the advantages and disadvantages of partioning it out?

Also, if I had a multiboot system, with a couple of different distros would they share a single home partition or would they each need there own? If it could be either way, are there problems with or issues with either choice?

Thanks for any help, explanations, or answers!

The home folder is where you keep all your files. (documents, videos, audio) and some other user settings.

If you put the home folder on a different partition you can install a new ubuntu version without losing all your files.

---

### Post by wednesday allfather on 2008-03-13
> **mntamimi said:**
> Hi, I am rather new to ubuntu and linux and had a couple questions regarding the /home. I've been reading (here and elsewhere) about advantages of separating out the /home on to its own partition, but to be honest they kind of go over my head. 

Could someone explain to me what the purpose of a /home partition is? What goes in the home partition and what goes in the other partition (root?)? And what are the advantages and disadvantages of partioning it out?

Also, if I had a multiboot system, with a couple of different distros would they share a single home partition or would they each need there own? If it could be either way, are there problems with or issues with either choice?

Thanks for any help, explanations, or answers!

I'm pretty new too, but welcome to the community.  

A /home PARTITION is your home folder (all your files, images, personal data, etc.) mounted to a separate partition.  I do it, and my reason keep personal data away from OS data.  Suppose something happens to my OS, or if I want to change OSes, and go with an inferior OS (mac or windows).  My OS can be reinstalled, but anything that has not been backed up yet is gone.  Plenty of other reasons, too.

Down side is that you are allocating space.  If you need more OS room or personal data room, you have to repartition your drive.  There are other reasons, i'm sure, but that's what bothers me about it.  

You can multiboot, specifying the one home directory/partition for any distro that can use the filesystem you are using.  You just have to worry about installation afaik.  Never know what will happen during installation.  You might get your partition wiped adn replaced with default folders.  

Depending on what you are going to do, you could create a partition separate from /home adn use it across all OS installs.  Remember that there are many choices for the type of filesystem format.  You have to have something compatible (or make it compatible).

Maybe that helps you.  Good luck!

---

### Post by kellemes on 2008-03-13
> **mntamimi said:**
> Hi, I am rather new to ubuntu and linux and had a couple questions regarding the /home. I've been reading (here and elsewhere) about advantages of separating out the /home on to its own partition, but to be honest they kind of go over my head. 

Could someone explain to me what the purpose of a /home partition is? What goes in the home partition and what goes in the other partition (root?)? And what are the advantages and disadvantages of partioning it out?

Also, if I had a multiboot system, with a couple of different distros would they share a single home partition or would they each need there own? If it could be either way, are there problems with or issues with either choice?

Thanks for any help, explanations, or answers!

The purpose of the /home-partition isn't much different from "My Documents" with Windows, it holds your personal setting for individual software. So basically everything that's bound to a specific user.

The /(root) partition is simply the top of the file-tree, this holds everything.. including your /home-directory when you haven't created a separate partition for /home. It basically holds every package needed by the base-system to function, this includes individual software-packages that store there files in all the different directories beneath /(root). /home isn't really needed for the base-system to function at all..
I personally don't recommend sharing /home-partitions between distributions of Linux, there is really nothing to gain and at best won't give crap. Just don't do it. ;-)

---

### Post by handydan918 on 2008-03-13
> **mntamimi said:**
> Hi, I am rather new to ubuntu and linux and had a couple questions regarding the /home. I've been reading (here and elsewhere) about advantages of separating out the /home on to its own partition, but to be honest they kind of go over my head. 

Could someone explain to me what the purpose of a /home partition is? What goes in the home partition and what goes in the other partition (root?)? And what are the advantages and disadvantages of partioning it out?
 /home is a directory. You can put it on it's own section of disk space, called a partition. The home directory contains all user files, i.e., data, personal configurations, etc. 
The biggest advantages to having a separate /home partition are:
1) Easier to reinstall without hosing all your data.
2) Easier to do upgrades and backups, too, you can even put /home on a separate physical drive. This is handy if you fsck around with older hardware and you have an OLD sub-ten GB drive (for the root partition) and put home on that shiny new bargain-basement 40GB drive you picked up cheap.
> 
Also, if I had a multiboot system, with a couple of different distros would they share a single home partition or would they each need there own? If it could be either way, are there problems with or issues with either choice?
 Generally speaking, a lot of what gets put in /home is desktop-environment specific, so if you had one distro running KDE and another running Gnome, You couldn't (easily) share /home.

---

### Post by Daveth on 2008-03-13
this is worth a browse as well

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Duck2006 on 2008-03-13
> Also, if I had a multiboot system, with a couple of different distros would they share a single home partition or would they each need there own? If it could be either way, are there problems with or issues with either choice?

You can use the same home partition for each distro just make sure you have different user names for each distro you use.

---

### Post by aysiu on 2008-03-13
Think of it as separating user settings and files from system settings and files.

/home is where your user stuff lives.

Outside of /home is where the system stuff lives.

If you understand anything about how Windows is structured, it'd be like having C:\ in general as its own partition and then C:\Documents and Settings as another partition.

A separate /home basically allows you to easily reinstall Ubuntu without having to copy all your user settings and files back from a backup medium.

---

### Post by drubin on 2008-03-13
> Quote:
Also, if I had a multiboot system, with a couple of different distros would they share a single home partition or would they each need there own? If it could be either way, are there problems with or issues with either choice?
You can use the same home partition for each distro just make sure you have different user names for each distro you use.

Why is that? Thought his theory was sounded quite cool, Same data/ same configs for the applications?

Or would this break things?

---

### Post by forrestcupp on 2008-03-13
> **Duck2006 said:**
> You can use the same home partition for each distro just make sure you have different user names for each distro you use.

You probably don't even need different user names if you don't mind them all looking the same.

---

### Post by drubin on 2008-03-13
Looking the same :) 

Great point didn't even thing about it like that. What would be the point in changing if you kept every thing the same :)

---

### Post by kellemes on 2008-03-13
> **forrestcupp said:**
> You probably don't even need different user names if you don't mind them all looking the same.

Well, what's the point in running multiple distro's that are exactly the same?
You most likely run different distro's, even if from the same brand, sharing settings will likely give problems since not every package on these systems will be the same version and therefor not be compatible.
I really don't see the benefit here..

---

### Post by Duck2006 on 2008-03-13
> **forrestcupp said:**
> You probably don't even need different user names if you don't mind them all looking the same.

Each distro in it's / partition sets things up different so you may end up with configure prob's.

---

### Post by darkworld on 2008-03-13
Havent read all the thread but heres my pennies worth. When I first started out on Linux over 8 years ago I read a book written by a hacker and he said. Partitioning up your disk into several partitions was good security policy.

I always partition up /, /home, /usr,/var,/tmp and /opt old habits die hard!

---

### Post by drubin on 2008-03-13
> I always partition up /, /home, /usr,/var,/tmp and /opt old habits die hard!

How do you know how much of your hard drive in proportion to use for each section?

Now assuming you have been using it for so long, you would know but the newbies?

---

### Post by aysiu on 2008-03-13
I've never created separate partitions for /usr, /var, /tmp, /boot, or /opt, and I've never regretted it.

A separate partition for /home is a good idea, though.

---

### Post by darkworld on 2008-03-14
> **rubinboy said:**
> How do you know how much of your hard drive in proportion to use for each section?

Now assuming you have been using it for so long, you would know but the newbies?


Maybe there is a deeper question on this? Does extra partitioning increase security? Or has Linux improved so much that exploits to get root are far and few? I remember reading that keeping your Var\ logs on a separate partition was good policy.

Its not that hard to gain knowledge of an installations requirements. I think its harder for a newbie working out in the installation wizard how to do manual partitioning??? :lolflag: 

In fact you are right because im sure most newbies wont know the structure even. However after a few reinstalls they may.

---

### Post by Mustard on 2008-03-14
> **Duck2006 said:**
> You can use the same home partition for each distro just make sure you have different user names for each distro you use.

Wow..I hadnt thought about doing it that way.  Thanks.  Each user would have their own config files then, unique to the distribution they relate to..

---

### Post by mntamimi on 2008-03-14
Thanks everyone for the clear responses. 

I think I'll put the /home on a separate partition for the primary distro (ubuntu of course) and then maybe just be lazy for the other distros and leave them as a standard install, as they are mainly for fooling around with anyways, so they probably won't have much to save in cases of re-installs, etc..

Plus I do most of my heavy file lifting on a second HD that has my music and other important files. 

Thanks again

---

### Post by aysiu on 2008-03-14
If your other distros are just for fooling around, how about installing them as virtual machines using VirtualBox? Then you don't have to mess around with partitioning.

---

### Post by mntamimi on 2008-03-14
> **aysiu said:**
> If your other distros are just for fooling around, how about installing them as virtual machines using VirtualBox? Then you don't have to mess around with partitioning.

This may be an ignorant response, but I'm not conceptually a big fan of VM's. Truth is I don't know a lot about them. But I just can't imagine that running an OS inside an application residing on another OS is a very efficient way to run things. 

Also, one of the other distros may be used for a little more than fooling around but wouldn't really have much in the way of personal data. I'm thinking about running an openSuse partition since it can natively install rpm's, and I'll need a functioning version of Citrix for work.

Plus, I was unimpressed the last time I tried to run something on a VM (or was it some other sort of emulating software thing), but of course this was trying to get windows apps to run on a Mac back in the early 90's. So that might not be a fair experience to judge on. :)

**What's the adavantage of using VirtualBox?**

For me at least, HD space isn't really an issue. I have a second drive with 500GB for music and file storage and the primary drive is big enough (can't remember the size) to hold at least a few installations without any issue (I think!).

---

### Post by aysiu on 2008-03-14
Yes, it's not efficient, but if you have enough RAM, it makes it very easy to switch back and forth between the OS you're fooling with and the OS you're working on. It also makes it easy to delete OSes without having to worry about selecting the right partition to overwrite or ever having to reboot.

Much has changed in the virtualization world since the early 90s.

---

### Post by wednesday allfather on 2008-03-14
I use VMWare and I think it is great.  It's good because you can effectively have several machines running on your computer.  They run with different OSes and files and space and you never have to close your tabs, save your work, shut down the pc, restart the pc, choose a different OS, login, and check to see if a web page works in IE.  I know, I know... Wine, right?  I have that too, but I also use some win stuff, every once in a while, but not enough to want to NOT use my Ubuntu stuff.  

I also don't want to partition up my drive needlessly.  I don't want to have to use gparted every time I see an interesting distro I want to try.  

You need to have the system resources to run 2 operating systems.  You can set the amount of disk space and memory you allow VMWare to use.  I've run MSW and Ubuntu pretty hard at the same time, and didn't see much of a problem.  

It's worth a try.  I mostly think it's cool, booting into a different OS from Ubuntu.  Mostly.

OOPS:  beat me to the punch

---

### Post by handydan918 on 2008-03-14
> **rubinboy said:**
> How do you know how much of your hard drive in proportion to use for each section?

Now assuming you have been using it for so long, you would know but the newbies?
separate /usr, /var , et cetera is a good policy for some server uses. For example, if your server starts throwing copious errors that all get logged to /var (on your / partition) it won't take long to become the victim of a self-inflicted denial of service because your root directory is full!

---

### Post by drubin on 2008-03-15
> 
Quote:
Originally Posted by rubinboy View Post
How do you know how much of your hard drive in proportion to use for each section?

Now assuming you have been using it for so long, you would know but the newbies?
separate /usr, /var , et cetera is a good policy for some server uses. For example, if your server starts throwing copious errors that all get logged to /var (on your / partition) it won't take long to become the victim of a self-inflicted denial of service because your root directory is full!

Every one seems to miss understand the question I was getting at. So I will try and explain what i was getting at.

It was not the reason for doing it, that is pretty clear and has always been. My question what size related.

How much/size do you know to allocate to each drive/partition...

---

### Post by aysiu on 2008-03-15
> **rubinboy said:**
> Every one seems to miss understand the question I was getting at. So I will try and explain what i was getting at.

It was not the reason for doing it, that is pretty clear and has always been. My question what size related.

How much/size do you know to allocate to each drive/partition...
I'd recommend between 8 and 12 GB for the / partition, between 256 MB and 1 GB for the swap partition, and the rst for home.

Unless you're running a server, there's no need for other separate partitions.

---

### Post by drubin on 2008-03-15
I only really wanted to start separating  my home partition now  so that it is easier to upgrade to Hardy.. 

But I more like your idea about using another folder like stuff/media. that way  you get the full version. 

It would not be a problem to symlink my Documents/Desktop/... to that folder then would it :)

---

### Post by spyder0080 on 2008-03-20
If I'm creating the /home partition while installing ubuntu, does it need to be primary or logical? Also, how would it look like when I run ubuntu? Will it be mounted as a separate drive or will the /home folder point to the partition?

---

### Post by erginemr on 2008-03-20
You should follow **aysiu**'s excellent howto on how to separate your /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

With the imminent advent of Hardy, I am also just half-way in the process of separating my /home folder to a new partition. This way, you can both do a clean install and still keep your personal settings.

Regarding your questions, I am not sure yet (have made it primary in Gparted, but not yet transferred the files), yet I believe primary should do. 

Your new /home folder will be acting just like it did before. Actually, it will stay on a completely separate partition, but unlike the awkward drive letters of Windows, this will be handled elegantly by Linux and provided that you make the necessary changes in your /etc/fstab file as instructed by the howto above, the inner-workings of the file system will be completely invisible to you. This is the beauty of Linux, isn't it?

---

### Post by louieb on 2008-03-20
> **spyder0080 said:**
> .../home partition ... primary or logical? 

Doesn't matter Linux doesn't care. 
> **spyder0080 said:**
> ... Also, how would it look like when I run ubuntu??
When your using a running Linux system you will not be able to tell if its installed on a single partition or spread across several partitions. Even if the partitions are on different hard drives. 

There is a file called /etc/fstab that  describes what partition is used for what part of the file system.

To look at the physical layout of a Linux install you run the **mount** command.

---

