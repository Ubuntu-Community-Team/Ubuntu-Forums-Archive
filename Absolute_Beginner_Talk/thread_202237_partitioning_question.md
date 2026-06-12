---
title: "partitioning question"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by stone80 on 2006-06-23
i have ubunutu installed and love it, but my wife who has little computer knowledge wants xp back. when i installed ubuntu i was trying to make it a dual boot and keep xp on there along with adding ubuntu, but i messed up and just reformatted my hard drive and now only have ubuntu on there. 

i was thinking about uninstalling ubuntu, then installing xp, then installing ubuntu. but what i want to know is how should i setup my hard drive when i get to installing ubuntu? i have an 80 gb hard drive and want to have about 25 gb for xp and 25 for linux and leave the other space open, but i don't know how exactly to set it up this way, can someone tell me what i need to do to set it up this way? i understand i also need a swap partition and maybe one other??

thanks

---

### Post by x64Jimbo on 2006-06-23
There's an app in the LiveDVD installer that will partition for you. Just run the installer up through the part where it asks about partitioning, then go manual. You'll be able to set the size and order of all your partitions before you install anything. You have made the correct decision to install Windows first then Linux though, because WIndows doesn't play nice with other operating systems when it sees them on the hard disk before it gets there.

---

### Post by Apple 101 on 2006-06-23
25 GB for XP
25 GB for Ubuntu / partition
10 GB for Ubuntu /home partition (can be less if you want)
3 GB or 4 GB for Linux swap partition - if you have 1GB RAM installed, it should about 3 times the capacity of your computer's RAM.

Install XP first giving 25 GB when asked for the partition size.  Then install Ubuntu.  You need to select Manual Partitioning in the Ubuntu installer.  Make sure that you select to create partitions in the free space.  The swap space should be at the end of the drive.

---

### Post by Apple 101 on 2006-06-23
[QUOTE=x64Jimbo]You have made the correct decision to install Windows first then Linux though, because WIndows doesn't play nice with other operating systems when it sees them on the hard disk before it gets there.[/QUOTE]It doesn't really matter, but it is much easier to install Windows first.  I use the XP boot loader to boot GRUB because I don't like the GRUB theme.

---

### Post by johnkennethhughes on 2006-06-23
When I was setting up my dual boot computer, Windows XP was installed first and took up the entire disk. I found it easiest to use the GParted live CD from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) to resize the Windows partition (hda1) to a bit less than half the disk. Then I used GParted to insert a small FAT32 partition (hda2), so I could share files between Windows and Ubuntu and left the rest of the disk blank.

I then booted the Ubuntu Dapper live CD and ran the installer. Now that there was some free space on the disk, I chose 'Install into the largest free space' and Ubuntu's installer set up the / and swap partitions automatically. It might not be the most direct method, but I found it the most straightforward and simple while I was still learning about partitioning. Obviously, the sizes of all the partitions depend on how much you intend to put in them.

---

### Post by stone80 on 2006-06-23
ok, so the only partition that should be on my hard drive when i get to the partitioning part is the windows partition, which will be taking up the entire 80 gb right? how do i go about resizing it to make room for the ubuntu and swap partitions?

---

### Post by Apple 101 on 2006-06-23
That depends on what you want to do.  In your first post you said you would uninstall Ubuntu and then install Windows.  In that case, just let Windows format the drive, but select a partition of 25 GB.

---

### Post by stone80 on 2006-06-23
when i am installing windows will it come up and let me select the size of the partition? or will i have to do that another way?

---

### Post by SkyNet2029 on 2006-06-23
You can resize the partition during the install process (by way of the disk partitioning options). As it was pointed out earlier though, its alot easier and less of a hassle to get your XP setup working LAST, since XP (windows in general, actually) does not like to have its MBR messed with or changed). 
The post by Apple101 is an excellent way to head for what you are doing.

---

### Post by ajifans on 2006-06-23
[QUOTE=Apple 101]25 GB for XP
25 GB for Ubuntu / partition
10 GB for Ubuntu /home partition (can be less if you want)
3 GB or 4 GB for Linux swap partition - if you have 1GB RAM installed, it should about 3 times the capacity of your computer's RAM.

Install XP first giving 25 GB when asked for the partition size.  Then install Ubuntu.  You need to select Manual Partitioning in the Ubuntu installer.  Make sure that you select to create partitions in the free space.  The swap space should be at the end of the drive.[/QUOTE]

I'd reduce the root / partition to about 10/15 Gb, and increase the Home partition.  That's because I don't have millions of apps, but do have lots of media.  You'd probably struggle to fill 25 Gb.

The old rule of thumb for Swap was 2x your RAM, but this is a bit outdated now, and any more than 2GB is a bit of a waste.  I have 2GB RAM and 2GB Swap.

---

### Post by stone80 on 2006-06-23
whats the difference between the ubuntu root partition and the ubuntu home partition?

---

### Post by ajifans on 2006-06-23
[QUOTE=stone80]whats the difference between the ubuntu root partition and the ubuntu home partition?[/QUOTE]

Essentially the root partition '/' is where the OS and apps will be installed.  Your Home partition '/Home' will hold all your (& other users) personal files and personal settings.

You don't need separate partitions, but it's best practice so you don't lose your files when you reinstall your OS.

---

