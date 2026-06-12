---
title: "Multiple distros on the same hard drive"
date: 2011-09-16
forum: Any Other OS
---

### Post by tech291083 on 2011-09-16
Hi Friends,

So far I have tried Ubuntu alone (single boot), Ubuntu with Windows ie dual boot and Ubuntu with Windows and Fedora ie triple boot and it has been a great learning experience for me. I have been able to do so with the kind and timely help of members of this very forum and I am grateful to all of you. 

Now I am thinking of installing multiple distros on the same hard drive and the list includes Ubuntu, Fedora, Suse, Debian, Gentoo etc. No Windows this time. What do you suggest is the best way to do so. I want to do this in order to learn something new and as of now I do not want to do any sharing of files among these distros (or any other complex settings) once they are installed successfully. I guess that one swap partition will be common to all. Each distro will create its own boot and root partition automatically as I understand. Correct me if I am wrong here. So please help me chalk out a plan and yes, my hard drive is SATA 80 GB. I have read on some forums that muliple distros can be installed on the same drive. 

Thanks a lot.

---

### Post by SteveDee on 2011-09-16
> **tech291083 said:**
> ...I only want to learn so I do not want to share a home folder or any other partition in particular....

You just want to learn, so I'd suggest installing VirtualBox and creating virtual machines for any OS you want to explore. When your done playing with an OS...just blow it away!

---

### Post by tech291083 on 2011-09-16
> **SteveDee said:**
> You just want to learn, so I'd suggest installing VirtualBox and creating virtual machines for any OS you want to explore. 

Thanks SteveDee, but I would love to install them manually and learn the right way to do so. VirtualBox is not an option for me right now, but yes it is a good suggestion though and I may try it in near future, thanks again.

---

### Post by tech291083 on 2011-09-19
Dear Friends,

Please share your experience of installing multiple distros on a single hard drive if any with all of us here, please do send me suggestions on the exact planning one requires for this whole exercise, thanks.

---

### Post by Alwimo on 2011-09-19
I hear of some people having problems when they have more than four partitions.

---

### Post by oscarivera9 on 2011-09-20
> **SteveDee said:**
> You just want to learn, so I'd suggest installing VirtualBox and creating virtual machines for any OS you want to explore. When your done playing with an OS...just blow it away!

I completely agree!  That's what I'm doing these days.  I used to have a Pentium 4 and now I have a triple core CPU which allows me to better run Virtual Box.  Before I couldn't do so.  If that is the case with you, then I understand.  Otherwise, if you just want to learn then virtual is a good way to go.  It is just like the real thing except that it isn't, the installation process, Grub, and everything else is pretty much the real things, but like SteveDee says, when you're done experimenting with a system just blow it away!

---

### Post by oscarivera9 on 2011-09-20
> **Alwimo said:**
> I hear of some people having problems when they have more than four partitions.

I've heard of people having problems with ONE partition, so that doesn't really say anything.  I have one PC right now with 8 (9) partitions and everything runs just fine.  I've got a 320 GB HDD with:
1.  DELL Recovery Partition (hidden)
2.  Windows XP
3.  a separate home partition (formatted to FAT32 so that Windows as well as Linux can read & write to it),
4.  Extended Partition with the following:
5.  Ubuntu 10.10,
6.   Debian 6, 
7.  Linux Mint 10 Debian Edition,
8.  Mandriva Linux 2010.2
9.  Empty unformatted partition to play around with

I have had problems in the past with other setups but they've all been due to user error, that is to say that ***I caused the problems,*** not the hardware nor the software.  Eventually I fixed the problems but much like in your case, it was definitely a fun learning experience.

For a while, I used to use separate partitions for /boot /home /dev /mnt /etc etc, but now I just use one /root partition for each OS and I make them share the Swap and if I can also the /home partition, if that sounds too complicated then I'll summarize as follows:  Use only one / partition for each OS but let them share the Swap.

---

### Post by Alwimo on 2011-09-20
Apparently, I was thinking of it not being possible to have more than four primary partitions.
[http://www.linuxquestions.org/questions/linux-general-1/creating-more-than-4-primary-partitions-376698/](http://www.linuxquestions.org/questions/linux-general-1/creating-more-than-4-primary-partitions-376698/)

---

### Post by malspa on 2011-09-20
There are different ways you can go with this. 

I use separate / and /home partitions for each of my distros, with a data partition that is accessible by each distro. But it isn't necessary to separate / and /home.

The first three partitions are primary partitions. The fourth partition is an extended partition, containing all the other partitions. One swap partition, which is one of the primary partitions.

Of course the first distro has grub installed to the MBR; the other distros have their grub installed to their /root.

I use Mepis with grub-legacy to boot all the other distros. Easier for me than using grub2.

You'll get a lot of replies with different approaches on how to do this (including replies about using VirtualBox instead), but whatever works for you is cool. Since you've already done some dual-boots that included Windows, multi-booting all Linux should be kind of a breeze. It was a lot easier for me once I took Windows out of the equation and went with all Linux here.

---

### Post by tech291083 on 2012-01-09
Hi,

I have a drive with only 80 GB of space and I am thinking of installing the following distros, please feel free to add the distro I should try based on your experience.

Ubuntu
Fedora
Debian

I am thinking of creating only one swap partition for all the distros, is it a good idea? Do I need to have a dedicated swap partition for each of the distros I want to install? I am thinking of installing a max of 8 distros with space of 10 GB each, please guide me, thanks.

---

### Post by tech291083 on 2012-01-09
Based on the 5 main types of Linux distros, this is what I understand, correct me if I am wrong (namely Debian based, Gentoo based, Pacman based, RPM based, Slackware based) as mentioned in this Wiki page on the net. I would love to have atleast one distro recommended by you from each of these 5 types. 

[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

Once I have downloaded them, I will try to install them on the same SATA hard drive with a total space of 80 GB. Thanks.

Please note that I want to install each distro on the hard drive to see how it works. I have used live CDs in the past and I am not happy with that idea. Installing each distro (one each from the 5 main types) will only give me an exact idea of how they look and behave. Hope you will reply accordingly. Thanks.

---

### Post by Double.J on 2012-01-09
^^^ Admins care to split this ^^^

---

### Post by Double.J on 2012-01-09
> **tech291083 said:**
> Based on the 5 main types of Linux distros, this is what I understand, correct me if I am wrong (namely Debian based, Gentoo based, Pacman based, RPM based, Slackware based) as mentioned in this Wiki page on the net. I would love to have atleast one distro recommended by you from each of these 5 types. 

[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

Once I have downloaded them, I will try to install them on the same SATA hard drive with a total space of 80 GB. Thanks.

Hi there! what you're going to notice most about these different types is the package managers. 
My personal favourites are 
apt - Ubuntu (or mint)
rpm - Open SUSE
pacman - well.. ARCH!
ports - gentoo, but sabalyon is MUCH more noob friendly
slackware - well I like zenwalk, but it has its own pakagemanagement system no pktools

I'd say download a bunch of live cds and try them out! Bare in mind that the Gentoo 12 live cd is actually a display of what you could do - there is no graphical installer and you build the system completely from source and binaries yourself - very configurable very stressful, very noob hating; Sabayon is probably a better place to start to see if you like the ports system. 

Slackware is a very strong distribution, though I've never got on with it which is why I recommend zenwalk - much easier transition from Ubuntu but ofcourse YMMV so give it a go (you can ofcourse live USB them all with unetbootin)

I'd say arch is a must - love the philosophy, love pacman.. heck I even love typing pacman - like Sorcerer 

At the end of the day, try everything, find something that works for you, but most of all give them a chance - Ubuntu is tailored for the new user after all - most of these will seem less user friendly at first.

in terms of number of swaps - one will be fine unless you plan on using another whilst one is hybernating

enjoy :)

---

### Post by leclerc65 on 2012-01-09
Whatever you do, avoid configuring NTFS as Logical Partition.
I have XP, Lubuntu as dual boot on my old desktop, later I add Puppy in the crowd because wireless was extremely unstable with the former two. Then I boot into Lubuntu and run 'sudo update-grub'. In addition I installed grub-customizer to get a better looking Boot menu. With Puppy you have the choice  not to install Grub, but in case you loose it for whatever reason you can recover it using the live Lubuntu CD. It's less pain for me than learning to edit grub (I will forget everything after after a week anyway).

---

### Post by tech291083 on 2012-01-09
> **leclerc65 said:**
> Whatever you do, avoid configuring NTFS as Logical Partition.

Ok, sure I will keep this in mind.


> With Puppy you have the choice  not to install Grub, but in case you loose it for whatever reason you can recover it using the live Lubuntu CD.

Great this is really useful. Thanks for the tips.

---

### Post by tech291083 on 2012-01-09
> **gnu/mirow said:**
> Hi there! what you're going to notice most about these different types is the package managers. 

That is why I am trying one each from the above mentioned main types (my personal understanding), it will help me get familiar with different ways of installing/upgrading packages. Great learning experience for me.


>  My personal favourites are 
apt - Ubuntu (or mint)
rpm - Open SUSE
pacman - well.. ARCH!
ports - gentoo, but sabalyon is MUCH more noob friendly
slackware - well I like zenwalk, but it has its own pakagemanagement system no pktools

Thanks I will add them to my list of install.

>  I'd say download a bunch of live cds and try them out! 

I have done it in the past, but to be honest I never enjoyed it. I love to install each distro to the hdd if possible.

 > Sabayon is probably a better place to start to see if you like the ports system. 

I will keep this in mind.

>  Slackware is a very strong distribution, though I've never got on with it which is why I recommend zenwalk 

Ok.

> I'd say arch is a must 
Agreed.

> 
At the end of the day, try everything, find something that works for you, but most of all give them a chance - 

I want to try and learn everything atleast once in my life, although I am not going to master each distro, but trying out new things is a fun itself. 
> 
in terms of number of swaps - one will be fine unless you plan on using another whilst one is hybernating
I want to know this badly. 

Thanks a lot. Great piece of advice.

---

