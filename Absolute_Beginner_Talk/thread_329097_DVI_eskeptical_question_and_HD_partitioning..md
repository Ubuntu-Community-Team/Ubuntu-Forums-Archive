---
title: "DVI eskeptical question and HD partitioning."
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by HighD on 2006-12-31
Ok, so here's the deal..I just bought a new PC, it's a Dell Dimension E520, 1GB DDR2 533MHz Ram, Core 2 Duo E6300, SATA II 250GB HD, nVidia GeForce 7300LE 256Mb GPU(has a DVI port), Dell 19" 1907FP Digital Monitor(has a DVI port)..and so on...now here's my question : I WANT TO INSTALL UBUNTU(to Dual-Boot), the thing is **I read a post a long time ago saying that someone burned his or hers DVI port by installing Ubuntu or running it from a Live CD**, I know it's kinda dumb, but i just wanted to know if anyone or anybody knows anything about this, OR if they have similar PC components so they can give an opinion on whether to install Ubuntu or not.

Also i just partitioned my hard drive the following way : (233GB Total) (Assuming Linux is a choice)

53GB - Windows
20GB - Linux
80GB - NTFS
80GB - FAT32

Any suggestions on how could I improve this decision? I can repartition, there's no problem. 

If any of you has any advice or answer on the DVI question, please let me know!

Thanks in advance for any answer or advice :mrgreen:

---

### Post by Sigudian on 2006-12-31
i would suggest you do

233gb - linux

but since it looks like you dont want to let go of windows i would suggest
20gb - Windows
20gb - linux
153gb - FAT32 (since both linux and windows know that partition), or EXT3 and install support for EXT3 on windows.

if you want to install a loot of programs on windows, you might highten the space for windows 10gb or 20gb, and remove it from the partition that would be shared betweein the operating systems

---

### Post by tagra123 on 2006-12-31
> **HighD said:**
> Ok, so here's the deal..I just bought a new PC, it's a Dell Dimension E520, 1GB DDR2 533MHz Ram, Core 2 Duo E6300, SATA II 250GB HD, nVidia GeForce 7300LE 256Mb GPU(has a DVI port), Dell 19" 1907FP Digital Monitor(has a DVI port)..and so on...now here's my question : I WANT TO INSTALL UBUNTU(to Dual-Boot), the thing is I read a post a long time ago saying that someone burned his or hers DVI port by installing Ubuntu or running it from a Live CD, I know it's kinda dumb, but i just wanted to know if anyone or anybody knows anything about this, OR if they have similar PC components so they can give an opinion on whether to install Ubuntu or not.

Also i just partitioned my hard drive the following way : (233GB Total) (Assuming Linux is a choice)

53GB - Windows
20GB - Linux
80GB - NTFS
80GB - FAT32

Any suggestions on how could I improve this decision? I can repartition, there's no problem. 

If any of you has any advice or answer on the DVI question, please let me know!

Thanks in advance for any answer or advice :mrgreen:

I have Nvidea with DVI -- no problems something else must have fried their card. 

Partitioning

30GB - to 50GB - Windows
15GB - Ubuntu - Root / (ext3)
40GB - Ubuntu home (ext3)
20GB - 30GB  - BackupPartition (ext3 or Fat32)  This comes in handy using partimage I call mine tempdrive and use it any time I need extra space.
Balance - FAT32 or ext3  (Place windows and linux data here to share.)

I might even consider reserving 20GB or so for a partition to store virtual machine file (at least that what I have done).

As far as FAT goes. If I were starting from scratch. I would consider having ext3 and no FAT. There are drivers/libraries that allow ext3 file system to be used from windows. One less drive to defragment.

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by HighD on 2007-01-01
First of all thanks to sigudian and tagra123 for their answers-

to Sigudian : i tend to have large files on my hd, so I'd rather have those 153gb  divided in NTFS and FAT32 (as FAT does now allow files > 4gb). Do you think 20gb is enough for an  "medium" Ubuntu user?:confused:  How much does a fresh install of ubuntu take? I can't let go of windows cuz I need the .NET platform and I want linux mainly for experimenting, do some work and I just want to feel I could switch completely to linux whenever I wanted (though I currently can't :( ).

to tagra123 : do you consider 55GB is good for an "medium"  linux user? Also thanks for the DVI advice:) . I just don't want to install ext3 support YET.

Also does anyone has a 1907FP monitor with DVI on it?

---

### Post by tagra123 on 2007-01-01
Take a look at this site -- mainly items 7-9.

I write windows software and never boot the computer as windows. I simply start vmware and do my work. Windows is isolated and contained in a nice little window.  I keep my working files on an ext3 partition -- also name linwinshare. I have uninstalled windows and just use the virtual machine when I need to work on windows.  VmServer is great for setting up but once youget it working i prefer the vmplayer .

You can always resize latter - I always wish I'd made this partition or that bigger.  Take whatever size you need and add another 5 to 10GB just to be sure.  

I have a mythtv server and process the files on a 2nd computer - most of the time the files I work with for video are between 700MB to 4GB so having enough space becomes important.

FAT32 is not that bad. Try the virtual machine -- It takes forever to get the OS installed but once installed it works just great.  Make a backup of the virtual disk files and you always have a clean install to go back to without reinstalling. The real bonus with this setup is that I can load up the VM on another machine such as my laptop.  

The tough part of the VM part had nothing to do with the VM at all. It took me a little work to get VM Windows and samba to communicate, but once that was working its almost like dual booting wothout having to reboot.

[http://users.piuha.net/martti/comp/ubuntu/install.html](http://users.piuha.net/martti/comp/ubuntu/install.html)

---

