---
title: "Partitioning For Multiple Linux Distributions"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Ek0nomik on 2007-09-26
I am looking at installing Ubuntu Gutsy, Fedora 7, and perhaps OpenSUSE or Linux Mint.  I want to start experimenting with other distributions along with using Ubuntu.  I also will have Windows XP installed so I can start playing Quake Wars.  :)

I am wondering if I will need to create a separate partition for a directory?  Will I need a /boot partition so Grub can work properly during boot?

Also, would you suggest creating a shared /home partition?  I would think a separate /home partition wouldn't be the best idea since not all distributions use the same versions of programs, and thus program files could get borked.

My plan is to turn the majority of my hard drive into a shared ext3 partition, where I can throw all my pictures, movies, music, etc so that all my linux distro's can share the data.  (I'm not worried about Windows having access to those files.)

Any advice, websites, etc would be appreciated.  Thanks!

---

### Post by Kobalt on 2007-09-26
You actually have many options before you, but first things first: a /boot partition isn't necessary in order to have Grub working properly (you can have one for other reasons such as increased mount time). Then, I would suggest having a shared /home partition for all your distros (though maybe not with a single user, I would for instance use different user for Debian systems and OpenSUSE). And a shared partitions for any other data can be considered as well... This would lead to a scheme such as this one:

/ >Ubuntu root file system
/ >OpenSUSE
/ >Fedora
swap
/home
/data

Have fun :)

---

### Post by kellemes on 2007-09-26
There are a million ways to do this..
This is mine..

2 distro's (ArchLinux and Debian)
Each there own bootpartition, I setup Grub from Arch and point to /boot/grub/menu.lst of Debian with this kernelline..
```
# Debian
title Debian
configfile   (hd2,8)/grub/menu.lst

```
It's pointing to the **boot**partition of Debian.

It's like a nested bootmenu.. so when I select Debian from the ArchLinux-bootmenu I get to see Debian's bootmenu and can boot Debian obviously.. can you follow?

Each there own /home and / and /var partitions (or whatever partitions you may wish), I like to keep it separate.
The only partition I let them share is swap!

Now when you install tux-2 (Debain in my case) simply let Grub install itself to the MBR, you bootmenu from tux-1 (Arch in my case) will be gone but can be restored using [SuperGrubDisk]("http://supergrub.forjamari.linex.org/") (the easiest way to do this)

Edit: The technique I use is explained in detail [here]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile").

---

### Post by Shazaam on 2007-09-26
How big and how many hard drives? Interested in virtualization? (vmware, virtualbox, etc) Except for 3d I have had good success running multiple os's using Vmware Player. No need to worry about borking your system and takes up a lot less space on the drive. If you are going to go that route I would recommend Vmware Server so you can add Vmware Tools (not available to Player).

---

### Post by rsambuca on 2007-09-26
I created a bunch of logical partitions for my linux distros.  They all share the same swap.  I also just use my ubuntu grub menu.lst to chainload to the other distros' grub menus so I don't have to edit the menu.lst's with any kernel updates, as that is all done automatically.

---

### Post by Ek0nomik on 2007-09-26
> **Kobalt said:**
> You actually have many options before you, but first things first: a /boot partition isn't necessary in order to have Grub working properly (you can have one for other reasons such as increased mount time). Then, I would suggest having a shared /home partition for all your distros (though maybe not with a single user, I would for instance use different user for Debian systems and OpenSUSE). And a shared partitions for any other data can be considered as well... This would lead to a scheme such as this one:

/ >Ubuntu root file system
/ >OpenSUSE
/ >Fedora
swap
/home
/data

Have fun :)

Could you elaborate on the increased mount time?

I also am wondering what I would do with the /home partition.  Inside /home would be UbuntuUser, SuseUser, FedoraUser?  Three seperate folders?  After a fresh install of Ubuntu, Fedora, and Suse (I have only used Ubuntu, but I imagine Fedora and Suse will be the same) they will have their own /home directory.  So, how do I turn the /home directory after a fresh Ubuntu/Fedora/Suse install into the directory on the /home partition?  Do I link the folders to point to the partition?

Thanks!

---

### Post by Pumalite on 2007-09-26
One /swap is enough for all of them. You can have as many partitions as you want depending on your space. Install Grub to the MBR.I keep separate /homes

---

### Post by Ek0nomik on 2007-09-26
I just want to point out that I added this question:

I also am wondering what I would do with the /home partition.  Inside /home would be UbuntuUser, SuseUser, FedoraUser?  Three seperate folders?  After a fresh install of Ubuntu, Fedora, and Suse (I have only used Ubuntu, but I imagine Fedora and Suse will be the same) they will have their own /home directory.  So, how do I turn the /home directory after a fresh Ubuntu/Fedora/Suse install into the directory on the /home partition?  Do I link the folders to point to the partition?

> **Pumalite said:**
> One /swap is enough for all of them. You can have as many partitions as you want depending on your space. Install Grub to the MBR.I keep separate /homes

Ok, I figured a single swap would be just fine.  You have multiple /home partitions?  So as an example, you have two root partitions for Ubuntu and Fedora, as well as two home partitions for the user on Ubuntu and Fedora?

How does one install Grub to the MBR?  I know it's done automatically with Ubuntu, but just for reference's sake I'd like to know how to manually do it (make sure it gets done).

Thanks for all the replies.  :)

---

### Post by Pumalite on 2007-09-26
Grub is installed to MBR by default. In my set up each OS has it's own partition where there are additional partitions for '/' and /home.

---

### Post by Ek0nomik on 2007-09-26
> **Pumalite said:**
> Grub is installed to MBR by default. In my set up each OS has it's own partition where there are additional partitions for '/' and /home.

How does that installation to the MBR work though?  After installing Ubuntu, Ubuntu is listed in Grub.  What if I then install Fedora?  Will only Fedora be on my MBR?  Will it automatically add itself to the list in addition to Ubuntu?

I know I can edit the /boot/grub/menu.lst file in Ubuntu, but which file do I edit with multiple linux distros?

---

### Post by rsambuca on 2007-09-26
I prefer to use one distro as my 'main' distro.  I then install that distro first, and have grub install to the mbr.

When you load the next distro (to partition number 2 for example), I load the 2nd distro's grub to partition #2.  You then add a chainloader entry to your 'main' distro's grub, which is on the mbr.

Same thing for distro 3, with grub to partition 3, etc.

The benefit to doing it this way is that if distro2 updates its kernel and grub, you don't have to manually update your grub(s).  You just add it the first time and you are done.  The downside is that you hop from grub to grub before you boot up, but I don't find that to be too much of an inconvenience. 

You can have one partition to share a /home, but it is strongly recommended that you use different user names with each distro so they don't bork all the settings.

---

### Post by Pumalite on 2007-09-26
There are some distros that recognize other distros and others don't. I install Ubuntu at the end because I like it's boot loader. If I install something else later, I install grub or Lilo to its own partition and then edit Ubuntu's menu.lst

---

### Post by DeanT on 2007-10-22
> **rsambuca said:**
> I prefer to use one distro as my 'main' distro.  I then install that distro first, and have grub install to the mbr.

I'm a relative Linux noob so go easy on me.  I have 2 hard drives, one has Ubuntu and the other one has XP.  My Ubuntu hard drive is setup as follows:

/dev/sda1 ext3 (flags:boot)
/dev/sda2 extended
/dev/sda5 linux-swap

I want to do the following.  The first question is slightly off-topic but hope someone can help.

1.  My existing Ubuntu install is borked.  I want to overwrite it with a clean install from the live CD.  When I get to the installation section on partitioning what options do I need to take?

2.  To install additional Linux distros afterwards I presume I just split the existing ext3 partition to accommodate the other distros.  How do I tell the installer to use the existing swap and extended partitions?

---

### Post by rsambuca on 2007-10-22
> **DeanT said:**
> I'm a relative Linux noob so go easy on me.  I have 2 hard drives, one has Ubuntu and the other one has XP.  My Ubuntu hard drive is setup as follows:

/dev/sda1 ext3 (flags:boot)
/dev/sda2 extended
/dev/sda5 linux-swap

I want to do the following.  The first question is slightly off-topic but hope someone can help.

1.  My existing Ubuntu install is borked.  I want to overwrite it with a clean install from the live CD.  When I get to the installation section on partitioning what options do I need to take?

2.  To install additional Linux distros afterwards I presume I just split the existing ext3 partition to accommodate the other distros.  How do I tell the installer to use the existing swap and extended partitions?

1.  Have you tried to fix it?  Anyways, you can just re-install and select use the whole drive.

2.  If you are going to re-install ubuntu, and think you may install other distros as well, I would definitely pre-partition your drive using gParted.  Then install Ubuntu and the other distros into the existing partitions.

---

### Post by DeanT on 2007-10-23
I'll go ahead and split my Ubuntu drive into two partitions.  I'll then do a clean install of Ubuntu into one partition and I'll use the other partition for experimenting with other distros.  I saw another post from you about chainloading grub so I will try that out too.

I'll post back if I run into any problems.

Thanks.

---

### Post by indytim on 2007-10-23
Thought I'd add to the fray :).  I'm currently supporting the following ops:
Kubuntu 6.10
Kubuntu 7.10
Ubuntu 7.10
Windows 2000

I add and remove ops frequently as I want at least 1 ops that is purely experimental.  I went the route of having a permament partition for my Grub boot loader.  Adding and removing ops is a breeze and my Grub menu doesn't go bonkers everytime we do a kernel upgrade.

IndyTim

---

### Post by sajro on 2007-10-29
Do you realize that Mint is based on Ubuntu and uses the same repositories? No need to install both. It's like installing Ubuntu and Xubuntu instead of just downloading the xubuntu-desktop package.

---

