---
title: "Pre-Installation Questions"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-15
Hello,
A couple of weeks ago, I installed Kubuntu on my Laptop and I was dual-booting with Windows XP. Although everything seemed to work properly, I was tired of booting back and fourth and decided that I needed a separate machine for Linux if I am really going to learn to use it everyday. So, I found a nice deal on EBay and am now in possesion of a nice Toshibha Satellite Laptop with the following configuaration:

Intel Pentium M Centrino 1.5GHz, 512MB RAM, 120 GB hard disk and all the other normal goodies that come with a laptop.

Now before I begin installation I would like to know a few things:

1) With this configuaration, is Kubuntu ok? or should I turn to Xubuntu as its more lighter on system resources?
2) Irrespective of the distribution I choose, I would like to know whether the following partition set is alright:

SWAP - 1GB
/ - 9Gb
/home - 80GB
/usr - 30GB

Should I modify this partition set? Or should I just use the guided install (which uses the entire hard disk) option on the installation menu?

3) I am under the impression that /usr is kind like program files in windows where all the user programs get installed. And /home is where the user files are kept. Is this correct? I will be installing a lot of programs like Matlab and stuff, so I want to make sure that, space for these programs are ample.

4) Is it possible to have all three flavors of Ubuntu for a single user? ie if I am bored using Kubuntu, I could just log out and using the same username log back into Ubuntu?

Thats all for now, but I am sure I will plenty of questions in the time to come. It would be really helpfull if answers are provided in the order of the questions.

Thanks!

---

### Post by ggaaron on 2007-06-15
Kubuntu and Ubuntu is the same system, just different desktop environment is used. You can log out, choose different desktop environment and log in.

With partitions, I don't use /usr as separate and I don't know any profits of doing so. Maybe use 39GB / partition... But I think that 39GB is quite a lot... I have all packages form kubuntu,xubuntu,ubuntu,edubuntu (kubuntu-desktop,xubuntu-desktop,ubuntu-desktop,edubuntu-desktop packages) plus some other packages and it is less than 10GB.

And as for xubuntu, it isn't really light... It can't match fluxbox/blackbox as desktop environment, but on your computer everything will go, it's pretty strong.

---

### Post by John.Michael.Kane on 2007-06-15
Kubuntu will run fine on the specs posted. Theres really no need to sperate the partitions in to so many

Most users run their partitions like this
/ - 9GB
/home - 110GB
swap - 1GB 

You can install ubuntu-desktop xubuntu-desktop environments, and log in to each one using your same user/pass. you can install them using adept package manager.

---

### Post by Keshyden on 2007-06-15
1. That machine will handle Kubuntu just fine.

2. If you use the guided partitioning, it will use 1g for swap and the rest will be /. This usually works fine.

3.  If you fill the whole drive with / it won't matter.

4. You can install kubuntu and then install ubuntu-desktop and xubuntu-desktop, and just switch desktops from the login screen.

EDIT: Redundant :-)

---

### Post by ts51 on 2007-06-15
The only thing you might need to worry about is networking....

---

### Post by ggaaron on 2007-06-15
But having separate /home is good, you have two partitions, so you can backup files on the other partition and then use gparted to change the first one, actually I've changed whole partitioning since install using gparted and it still works=)

---

### Post by linuxnovice on 2007-06-15
Thank you for all your help.

I didnt understand 2 of the replies. I have heard that having a separate /home partition is good. Suppose I have only a / partition and swap and the next version of Ubuntu comes along and I decide to upgrade. Now if I only have a / partition will all my personal files be intact? In this scenario, would it not be safer to have a separate /home partition for my stuff?

> ts51:The only thing you might need to worry about is networking.
Could you pleaes elaborate on that?

> But having separate /home is good, you have two partitions, so you can backup files on the other partition and then use gparted to change the first one, actually I've changed whole partitioning since install using gparted and it still works=)
Could you explain that in more layman terms :)?

Where do the user programs get installed? Like suppose I install skype, where would the files that it uses be stored in?

Thanks!

---

### Post by linuxnovice on 2007-06-17
Hi,
I am just about to install Kubuntu on the laptop that I purchased. I just want to know one thing. As I mentioned earlier, I would like to use / 10GB, Swap 1GB and rest for /home. But now I have noticed that there is a guided install using the entire disk during installation. Is it better to use that option since I am giong to install Kubuntu on the entire disk anyway? Could someone please tell me how guided install partitions the hard disk?

Thanks.

---

### Post by John.Michael.Kane on 2007-06-17
The standard live cd install will only give you / and swap no seprate home.

You can however use the live cd to use gparted to set up partition sizes as you want.

Click system---->administration---->gparted, and set up the drive how you like.

Another option is to use the alternate text mode cd which may be a little more easier for you to use to set up your drive.

---

