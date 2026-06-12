---
title: "Install to Second Hard Drive"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by blueskye on 2006-01-20
I want to try to install Ubuntu 5.10 Breezy today. I have read many of the help files and have gathered hardware docs in case I need to answer questions during install.

I have two hard drives. XP is loaded on hda (first controller, Master.)
I want to load Ubuntu on hdb (first controller, currently set as Slave.)

I saw in the docs that something will be written to the MBR so GRUB will ask for which OS to load. Since I want to install on a second hard drive, where does this get installed? On the first hard drive (the Master)? If so, should I temporarily disable my anti-virus, anti-trojan, anti-spy software in my XP installation so that MBR can be written?

Do I need to move my second hard drive to the second controller? That one currently has a CD/DVD writer as Master (no Slave.)

Also, my second hard drive has never had an OS loaded on it and I don't know if the BIOS will recognize it as a bootable drive. It is currently formatted as NTFS. Do I need to do anything in the BIOS to make it a bootable drive or will this be set during install of Ubuntu? Can Ubuntu install to a drive formatted as NTFS and will it be able to convert to ext3? (I have not been able to figure that part out reading the docs.)

Thanks very much for any help ... Blueskye

---

### Post by Kapre on 2006-01-20
[QUOTE=blueskye]I have two hard drives. XP is loaded on hda (first controller, Master.)I want to load Ubuntu on hdb (first controller, currently set as Slave.) [/quote]

blueskye - During the setup process, the screen will show all the drives on your pc (master and slave). If you properly installed your second hd, the setup process will tag this and it will ask you where do you want to install Ubuntu (which I think you will choose the 2nd hd).

> I saw in the docs that something will be written to the MBR so GRUB will ask for which OS to load. Since I want to install on a second hard drive, where does this get installed? On the first hard drive (the Master)? If so, should I temporarily disable my anti-virus, anti-trojan, anti-spy software in my XP installation so that MBR can be written?

As I stated above, setup process will ask you where you will install, just select the second hd. You dont need to turn off your anti whatever because you won't load windoes during the install (CD will boot  not your XP).

> Do I need to move my second hard drive to the second controller? That one currently has a CD/DVD writer as Master (no Slave.)

Use the second section of the ribbon cable of your hd.

> Also, my second hard drive has never had an OS loaded on it and I don't know if the BIOS will recognize it as a bootable drive. It is currently formatted as NTFS. Do I need to do anything in the BIOS to make it a bootable drive or will this be set during install of Ubuntu? Can Ubuntu install to a drive formatted as NTFS and will it be able to convert to ext3? (I have not been able to figure that part out reading the docs.)

Read the instruction carefully during the set-up process and it will you all the options.


K

---

### Post by blueskye on 2006-01-20
OK ... thanks, Kapre ... I feel like I am about to step off a cliff (g) ...

blueskye ...

---

### Post by Kapre on 2006-01-20
[QUOTE=blueskye]OK ... thanks, Kapre ... I feel like I am about to step off a cliff (g) ...

blueskye ...[/QUOTE]

Nah...dont think like that...with this community helping (us), it would be a walk in the park for you... Anyways, welcome to the linux (real) world.

K

---

### Post by lha on 2006-01-20
Hi blueskye,

If you haven't started installation yet, you should take a look on [this thread]("http://ubuntuforums.org/showthread.php?t=119232"). If you follow those instruction, you don't need to modify your which has Windows. IMHO it is easier and safer way to go.

---

### Post by blueskye on 2006-01-21
Kapre ... I don't believe it ... the install ran perfectly ... I did have to enable my second hard drive in the BIOS as bootable and set to boot to CD. I just told it which drive to install to ... it set up the partitions ... and away it went. Took 50 minutes, including 44 update packages. Then I found Synaptic and downloaded some doc files.

Now I have to find out if there is anything else I need to install or configure to make this a standalone one-user client-type config.

I am really amazed at how easy it was to install. Thanks! ... blueskye

---

### Post by blueskye on 2006-01-21
Hi, lha ... sorry I didn't see your post until after install, which went really well... far better than I expected. The cliff was only 3 feet tall (g) ... thanks for the reply ...
..... blueskye ....

---

### Post by lha on 2006-01-21
[QUOTE=blueskye]Hi, lha ... sorry I didn't see your post until after install, which went really well... far better than I expected. The cliff was only 3 feet tall (g) ... thanks for the reply ...
..... blueskye ....[/QUOTE]

I don't mind. :) Nice to hear your installation was painless.

---

