---
title: "Dual Boot Ubuntu with ... Ubuntu"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-02-10
Hi there. This might sound like a bit of an odd question, but bear with me and Ill explain.

I want to dual boot Ubuntu with a second installation of Ubuntu.

The Reason:
I'm a long time ex-Windows user (Since WIn3.1) who has just made the move to Linux. I currently have a dual boot with Windows 2000 and Ubuntu. Since installing Ubuntu a few months ago Iv not been in Windows more than once or twice and I now see no reason to keep it on my system at all, as it is only wasted space.

However, years of Windows use has left me paranoid, and I would like a second, much smaller, Ubuntu installation, that I could use for recovery purposes should my main Ubuntu installation have a problem.

The Question(s)
I would like to set up something like this:

hda1 - Ubuntu Main + Swap
hda2 - Home
hdb1 - Smaller Ubuntu Recovery + Swap
hdb2 - Smaller Ubuntu Recovery Home

1) 
Is it possible to share the Swap partition between installations?

2) Will Ubuntu Main be able to see Ubuntu Recovery and auto mount the drives in the same way as it does with my current Windows installation (And vice-versa of course), and if it does, would it be possible to share my bookmarks and email settings across the two, as I currently do with Windows?

3) Perhaps this should have been first, but should Ubuntu Main fall over would I be able to use Ubuntu Recovery in the same way as I would use the live cd? (I currently use *Quickstart* as a backup, as supplied by a helpful person on these very forums, and my backups go to an external hard disk, so total recovery should only be a case of restoring from the backups)

4) Am I barking up the wrong tree entirely and has my years of Windows subservience left me addled and unable to grasp some simple concepts?

Thanks for any light you may be able to shed on this.

Cheers

Max

---

### Post by mikkenzi on 2008-02-10
I see no need for you to do that... you could just make a backup of your ubuntu as it is now, save it to another disk and the restore it later... just as you used to do with Windows 
see here
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by LaRoza on 2008-02-10
Swap can be shared. You can share a home directory, or if you want to just transfer all your settings to the other installation, you can copy the configuration files. (They will be in your home directory, press Ctrl + h, copy the ones you want to the other installation's home)

You might want to just create an image of your Ubuntu partition, and store that for backup purposes. Clonezilla can image an entire disk or a partition and restore it from the image.

See the link in my sig.

---

### Post by Paqman on 2008-02-10
I'm not sure that setting up a second install of Ubuntu would have much value though. LiveCDs such as the Ubuntu CD, Knoppix or the System Rescue CD all work really well to recover broken systems.

Still, there's no reason why you can't have multiple _different_ distros on one machine. It's a good way to learn about other versions of Linux. You can share swap and /home partitions, you just need to create seperate / partitions and seperate user accounts.

---

### Post by R@inm@n on 2008-02-10
I just made a new partition when I wanted to try out Mint recently. 

It's an easy way to try the other Linux distro's. The Live CD can save your OS from most disasters.


  R.

---

### Post by geo909 on 2008-02-10
I had a similar question, too (for personal reasons I wanted to have Ubuntu-studio as a different installation-no alternative suggestions, please!).

 SO, when you want dual/triple/quadruple boot between Ubuntus, you just throw in the live CD and install Ubuntu on a different partition? 
What about grub? 
Will that work fine or one should have to fix things manually?

---

### Post by LaRoza on 2008-02-10
> **geo909 said:**
> I had a similar question, too (for personal reasons I wanted to have Ubuntu-studio as a different installation-no alternative suggestions, please!).

 SO, when you want dual/triple/quadruple boot between Ubuntus, you just throw in the live CD and install Ubuntu on a different partition? 
What about grub? 
Will that work fine or one should have to fix thing manually?

When you reinstall grub, it adds other Linux installations to it.

Ubuntu is very good at getting them all.

---

### Post by MaxVK on 2008-02-10
Thanks for your replies and links.

LaRoza: That link to Clonezilla is great, thanks, Ill look into that as a backup medium, but it doesn't address my main concern:

I get a lot of emails on an regular basis (Hourly sometimes) and many of them are mails that I want to keep for a while at the very least. However, I backup once a week on a Monday, so if I managed to trash the system on Saturday Id lose a weeks worth of mail (And quite possibly money into the bargain!), hence my desire to be able to share email settings across another installation.

Wow! Quick responses here! Iv just noticed LaRoza's other answer to geo909's question, and that answers another of my own, however, I have another:

Should I go ahead with this, and GRUB picks up my new installation, is there some way to Name the installations in GRUB, or will they both simply show as Ubuntu?

---

### Post by LaRoza on 2008-02-10
> **MaxVK said:**
> 
Should I go ahead with this, and GRUB picks up my new installation, is there some way to Name the installations in GRUB, or will they both simply show as Ubuntu?

You can name them, by default, the last Ubuntu installed will be first.

You can edit the entries:

```

gksudo gedit /boot/grub/menu.lst

```

You can change the "title" lines to whatever you want. (The actual entries will be about halfway down)

If you are going to change more, you can switch them around more, but I'd back it up first (copy it so you can restore it if it is changed beyond recognition)

---

### Post by Paqman on 2008-02-10
> **MaxVK said:**
> 
I get a lot of emails on an regular basis (Hourly sometimes) and many of them are mails that I want to keep for a while at the very least. However, I backup once a week on a Monday, so if I managed to trash the system on Saturday Id lose a weeks worth of mail (And quite possibly money into the bargain!), hence my desire to be able to share email settings across another installation.


How are you backing up? sbackup is a good utility that automates backups. You can specify when and where you want to back up, and where to put the backups. In your case you could simply to tell it to back up your emails (to wherever you tell it to) as often as you like. It's in the repos.

> 
Should I go ahead with this, and GRUB picks up my new installation, is there some way to Name the installations in GRUB, or will they both simply show as Ubuntu?

You can call them anything you like. Just edit the "title" field in /boot/grub/menu.lst

---

### Post by erfahren on 2008-02-10
I've done the same thing - installed Xubuntu 7.10 beside my Ubuntu 7.04 (my "stable" one) - so I don't think it's crazy! - lol

anyway - I share a swap, but have seperate /home partitions (I've been known to mess them up) 

I mounted my /homes in each of the fstab(s) with (for example):
```

# /dev/sda9      
UUID=c9d266e5-3cba-496f-ab7a-7355d604b783 /mnt/xubuntu_home      ext3     defaults     0       0

```
since I use the same username for both I don't think the permissions are a problem - just need to change owner on the mount point to me so I could access it: "sudo chown efarhren:erfahren /mnt/xubuntu_home" - (I guess I could have just mounted it in my /home directory and wouldn't have had to do that)

Anyway - about GRUB - I installed Xubuntu second and *didn't* install GRUB along with it. I just added entries for Xubuntu in my existing Ubuntu's menu.lst  - most Linux distros provide an simple way to do that by default - see [this thread](http://ubuntuforums.org/showthread.php?p=4003454)

---

### Post by gn2 on 2008-02-10
> **MaxVK said:**
> I get a lot of emails on an regular basis (Hourly sometimes) and many of them are mails that I want to keep for a while at the very least. 

Set your e-mail software to leave a copy on the server and you'll be able to access them from any PC at any time.

---

### Post by MaxVK on 2008-02-10
Paqman: I currently backup using Quickstart, which is an excellent script created by someone on these forums. It works very well for me and seems to be very fast. I *might* consider looking into Clonezilla as suggested by LaRoza, but if its like most other drive clone software, it will backup everything, including the empty space, which is of no use to me.

Anyway, thanks for all your comments. I'm going to mull over them for a while and consider what I want and what I actually need (Usually two different things entirely!).

Thanks

Max

---

### Post by LaRoza on 2008-02-10
> **MaxVK said:**
> Paqman: I currently backup using Quickstart, which is an excellent script created by someone on these forums. It works very well for me and seems to be very fast. I *might* consider looking into Clonezilla as suggested by LaRoza, but if its like most other drive clone software, it will backup everything, including the empty space, which is of no use to me.


It won't clone empty space :)

You can save the image in a variety of formats, and compression.

---

### Post by Paqman on 2008-02-10
> **MaxVK said:**
> Paqman: I currently backup using Quickstart, which is an excellent script created by someone on these forums. It works very well for me and seems to be very fast. I *might* consider looking into Clonezilla as suggested by LaRoza, but if its like most other drive clone software, it will backup everything, including the empty space, which is of no use to me.


Sbackup backs up individual folders. You can either specify which ones or let it grab a default set. It'll also restore them for you.

Clonezilla is a good option for taking a 100% backup though. Like LaRoza said, you can squeeze them down pretty small.

---

### Post by MaxVK on 2008-02-10
> **LaRoza said:**
> It won't clone empty space :)

You can save the image in a variety of formats, and compression.

Now I'm interested! Most of the clone applications Iv come across (I'm talking Windows now) would clone the empty space, which means (As far as I can tell) that you cant restore the image to a drive that is not exactly the same size as the cloned image.

This has always been an issue, and especially so now, since I'm at the point where I want to remove windows and use some of that space for my current Ubuntu installation. As I understand it Quickstart will simply put the files onto any disk you point at (I have asked about this in the Quickstart thread, although Iv yet to get around to trying it)

Is this an issue with Clonezilla?

Whichever way I go with my current plans my current Ubuntu installation is likely to grow, and while I don't mind re-installing the system once the drives have been resized (And possibly repartitioned entirely) Id like to be able to restore my current system to the new, larger one.

Thanks again for your help

Max

---

