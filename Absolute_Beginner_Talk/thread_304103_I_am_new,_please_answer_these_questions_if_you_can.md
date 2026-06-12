---
title: "I am new, please answer these questions if you can."
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Ayush on 2006-11-21
1. What is the difference between Ubuntu, Linux, Fedora ?

2. After formatting my C:\ (Windows) partition, i resized it to try Ubuntu. 3.20 gb for Ubuntu and rest for Windows XP. I installed Ubuntu and when it asked for the swap partition, i made a partition that has only 8MB (Yes MB) for Swap use. Is it OK ?

3. What is a Swap partition ? How/Why Ubuntu use it ?

4. Can Ubuntu write to Fat32 ?

5. I installed Ubuntu then Windows and now i can't boot to Ubuntu because there is no choice. How can i multi-boot ?

6. I am using Dial-up. After trying a lot, i found [System-Adm.-Networking] but it fails to detect my Modem (PCI SoftV92-Internal) so i cant connect. There is a Linux driver on CD (rpm file) but Ubuntu tries to open it with Archive manager and fails so i cant install the driver. Am i doing something wrong ?

---

### Post by adwait on 2006-11-21
Lots of questions! Anyway welcome to Linux! Ok here goes...

1)Linux is the general name for the class of operating systems based on the linux kernel. Ubuntu and Fedora are two distributions based on linux. Each distribution (or distro) is different in its look and feel etc. but basically based on the same linux kernel

2)Yes, 8 MB swap will do provided you have enough RAM

3)Swap is a partition used by Ubuntu as a swap space. ie: when it runs out of RAM, it uses the swap to store the less frequiently stuff that should actually be in the RAM. Normally, PCs today have ample RAM and so too much swap is not really needed anyway.

4)Yes, ubuntu can write to a fat32 partition, without doing anything special.

5)You should install Windows first and then Ubuntu so that Ubuntu detects windows and cofigures the dual boot for you. Reinstall if possible, if not, then post here and someone will post a solution :)

6)The rpm files work on Redhat based systems, not on Debian based systems (ie: ubuntu).

To use the rpm file, you first need to convert it to deb file by using

```
sudo alien <filename>
```

This will generate a deb file which can then be installed using
```
sudo dpkg -i <deb filename>
```

These commands should be typed in the terminal program. Alien is normally not installed on the Ubuntu system and since you don't have internet access, you will have to download a deb file for alien and then install it using

```
sudo dpkg -i <filename>
```

Then you can use the above commands.

You will find alien here:[http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Falien%2Falien_8.52_all.deb&md5sum=9a26fff8fcf93eb1f77abbfdb3bd8267&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Falien%2Falien_8.52_all.deb&md5sum=9a26fff8fcf93eb1f77abbfdb3bd8267&arch=all&type=main)

---

### Post by wyldstryker on 2006-11-21
someone beat me to the punch.  lol

> **Ayush said:**
> 1. What is the difference between Ubuntu, Linux, Fedora ?

2. After formatting my C:\ (Windows) partition, i resized it to try Ubuntu. 3.20 gb for Ubuntu and rest for Windows XP. I installed Ubuntu and when it asked for the swap partition, i made a partition that has only 8MB (Yes MB) for Swap use. Is it OK ?

3. What is a Swap partition ? How/Why Ubuntu use it ?

4. Can Ubuntu write to Fat32 ?

5. I installed Ubuntu then Windows and now i can't boot to Ubuntu because there is no choice. How can i multi-boot ?

6. I am using Dial-up. After trying a lot, i found [System-Adm.-Networking] but it fails to detect my Modem (PCI SoftV92-Internal) so i cant connect. There is a Linux driver on CD (rpm file) but Ubuntu tries to open it with Archive manager and fails so i cant install the driver. Am i doing something wrong ?

1.   Both are linux distros.  Ubuntu is based off Debian,  while Fedora is Red Hat Based.

2.  you might want at least 128mb - 256mb for your swap

3.  The best way I can describe the swap is -  virtual ram.  It will use the swap partition along with the installed ram so linux can run faster.   (please, correct me if I'm wrong.  This is my understanding of it. )

4. Yes, it will write to fat32.

5. I think windows just ate the boot loader (Grub) for your ubuntu install.  Most people will install windows first and then ubuntu.  

6.  Not sure on that one. might wanna do some forum searching.

---

### Post by tocleora on 2006-11-21
I'm under the impression alien isn't installed by default so you may have to do this:

sudo apt-get install alien

then enter the password you set up for your "root" account.

If I remember correctly (I get the fedora and ubuntu installs mixed up a lot as I've installed fedora several times and only ubuntu once [mark for ubuntu]) they will answer some of these questions along the way in your setup process.  It should set a default configuration for your partitions for example so you don't have to pick the swap size, and it should prompt you that it detected windows and information for installing the multi-boot loader.

---

### Post by Shuja on 2006-11-21
Just to touch on #2 it's a good practice to have your swap at least as big as the amount of ram on your system.  Even if you have a lot of ram there will some swap activity.

---

### Post by adwait on 2006-11-21
Well, I have 512MB or RAM and I rarely if ever see Swap activity..

---

### Post by Ayush on 2006-11-21
> **adwait said:**
> Lots of questions! Anyway welcome to Linux! Ok here goes...

1)Linux is the general name for the class of operating systems based on the linux kernel. Ubuntu and Fedora are two distributions based on linux. Each distribution (or distro) is different in its look and feel etc. but basically based on the same linux kernel

2)Yes, 8 MB swap will do provided you have enough RAM

3)Swap is a partition used by Ubuntu as a swap space. ie: when it runs out of RAM, it uses the swap to store the less frequiently stuff that should actually be in the RAM. Normally, PCs today have ample RAM and so too much swap is not really needed anyway.

4)Yes, ubuntu can write to a fat32 partition, without doing anything special.

5)You should install Windows first and then Ubuntu so that Ubuntu detects windows and cofigures the dual boot for you. Reinstall if possible, if not, then post here and someone will post a solution :)

6)The rpm files work on Redhat based systems, not on Debian based systems (ie: ubuntu).

To use the rpm file, you first need to convert it to deb file by using

```
sudo alien <filename>
```This will generate a deb file which can then be installed using
```
sudo dpkg -i <deb filename>
```These commands should be typed in the terminal program. Alien is normally not installed on the Ubuntu system and since you don't have internet access, you will have to download a deb file for alien and then install it using

```
sudo dpkg -i <filename>
```Then you can use the above commands.

You will find alien here:[http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Falien%2Falien_8.52_all.deb&md5sum=9a26fff8fcf93eb1f77abbfdb3bd8267&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Falien%2Falien_8.52_all.deb&md5sum=9a26fff8fcf93eb1f77abbfdb3bd8267&arch=all&type=main)


Thanks, i will reinstall Ubuntu so i can use that and try installing the deb files but :

1.I have 256 mb and when i open help files, it slows the Operating system for a while. Is it because low swap file size ?
2.I have a Fat32 partition (17.7 gb, 2 gb free) but Ubuntu cant write to it. The commands like Create folder are grayed out.
3.I think i am using a old version of Ubuntu. How i can find the version ?
4. What is a terminal windows and where is it. Is it like Command Prompt in windows?

---

### Post by tocleora on 2006-11-21
1. Yes more than likely.
2. It's probably in read only mode, you need to make it read/write.  I can't remember how to do it but I'm sure someone will post here seconds after me with the response. ;)
3. System > About Ubuntu
4. It's like DOS (command prompt).  Applications > Accessories > Terminal

---

### Post by adwait on 2006-11-21
1) Yes, If you have 256 MB RAM, you should have around 128-256MB of swap.
2)The create folder etc. options are grayed out because by default, only the root (like the administrator in windows) has access to the file system. The users have access only to their home folders. In the terminal window type
```
sudo nautilus
```

In this window, if you select the fat32 partition, it will allow you to create folders etc. Basically, any command prepended with sudo is executed as the root user. When it asks for your password, just enter your normal password. To allow the normal user to write to the fat32 partition, look in the system configuration, not really sure where you will find it in UBuntu because I am Kubuntu..

3)Open firefox, by default it should show you a page telling you about Ubuntu. It should also mention the version (eg: Dapper, Edgy, Breezy etc.)

4)Terminal is like the command prompt in windows. You should find it somewhere under Applications>System I think. AGian not sure since I am on Kubuntu, not on Ubuntu.

PS: How do you like Linux?? Within minutes of posting your questions, you have so many responses! That's what I call product support ;) BTW, u in India?

---

### Post by Dasold on 2006-11-21
are you sure that windows partition is FAT32 and not NTFS? anyways the answer to make it writeable for every user is in /etc/fstab

---

### Post by Ayush on 2006-11-21
> **adwait said:**
> 1) Yes, If you have 256 MB RAM, you should have around 128-256MB of swap.
2)The create folder etc. options are grayed out because by default, only the root (like the administrator in windows) has access to the file system. 

3)Open firefox, by default it should show you a page telling you about Ubuntu. It should also mention the version (eg: Dapper, Edgy, Breezy etc.)

4)Terminal is like the command prompt in windows. You should find it somewhere under Applications>System I think. AGian not sure since I am on Kubuntu, not on Ubuntu.

PS: How do you like Linux?? Within minutes of posting your questions, you have so many responses! That's what I call product support ;) BTW, u in India?

Thanks to all.
Yes i liked Ubuntu, that is why i am asking these question even when i have windows.How you know i am from India ?

 I wil try everything after installing it again but when i installed it before, it never asked me to specify a password for root account. What is the password ?

---

### Post by Ayush on 2006-11-21
New Problem !!! When i went to reinstall Ubuntu, at the Partition Manager step (where you have to select the partition you want to use), there is only one choice that is MY HARD DISK. No partition listed, only choice is [repartition the hard disk] / [remake the hard disk table]. Before windows, everything was ok.  ](*,) ](*,) ](*,)

---

### Post by ron999 on 2006-11-21
Ayush
The root password is the same password that you use to log in when booting.

---

### Post by speeddemon8803 on 2006-11-21
> **wyldstryker said:**
> someone beat me to the punch.  lol



1.   Both are linux distros.  Ubuntu is based off Debian,  while Fedora is Red Hat Based.

2.  you might want at least 128mb - 256mb for your swap

3.  The best way I can describe the swap is -  virtual ram.  It will use the swap partition along with the installed ram so linux can run faster.   (please, correct me if I'm wrong.  This is my understanding of it. )

4. Yes, it will write to fat32.

5. I think windows just ate the boot loader (Grub) for your ubuntu install.  Most people will install windows first and then ubuntu.  

6.  Not sure on that one. might wanna do some forum searching.

pretty smart for a newb! :)

---

### Post by wyldstryker on 2006-11-21
> **speeddemon8803 said:**
> pretty smart for a newb! :)

Thanks :D  I've been "tinkering"  with ubuntu on and off since breezy.  Normally I just lurk the forums.  Figured it was time I gave back to the community. :D

---

### Post by adwait on 2006-11-21
Yes, that's because when nothing was installed, it could just view the entire disk as unpartitioned space, but now Windows is installed on it. Select to automatically partition the disk and it should be fine.

N I know you are in India, coz the name Ayush is Indian..

---

### Post by Ayush on 2006-11-22
Are you sure to choose Automatically partition ? I have data that is not backed up and i cant backup. What if it choose a data partition automatically ? Before windows, the hard disk was like this :
C :\  Formatted as Fat32 and when i installed Linux it converted this to another Format (i cant remember the name).
D:\   DATA, NTFS
E:\   DATA , Fat32
Unpartitioned 8 mb, swap now.

When i choose Manual :
It list my Hard DIsk (Before windows, my partitions were listed)
When i choose the hard disk, it gives me the option of delete all partitions and create a new partition table !!!

---

### Post by Circus-Killer on 2006-11-22
> **Shuja said:**
> Just to touch on #2 it's a good practice to have your swap at least as big as the amount of ram on your system.  Even if you have a lot of ram there will some swap activity.

personally, every guide/howto/doc i've read, it recommends your amount of RAM x 2. one example off the top of my head is the gentoo installation guides.

i dont know, i've always (since 99) used double my ram amount. maybe i've been wrong all this time, but i know i've never had issues with running out of swap space. :p

---

### Post by Ayush on 2006-11-22
Adwait, Are you in India ? If yes, then can you tell me is Ubuntu Free CD really free in India or is there some kind of charge.

---

### Post by adwait on 2006-11-22
Yeah, I am in Mumbai. Yes, the CD is free, there's no charge whatsoever, but it does time for the CD to reach you. I haven't really ordered the CD ever, just downloaded the images from the net. 

As forautomatic partitioning, in the partitioning menu, it should give you an option to use the largest contiguous free space. Don't select the create new partition table option, that will erase your disk.

---

### Post by Ayush on 2006-11-22
> **adwait said:**
> 
As forautomatic partitioning, in the partitioning menu, it should give you an option to use the largest contiguous free space. Don't select the create new partition table option, that will erase your disk.

There is no option (only option is recreate). But i solved it. When i installed Windows, it messed up the partition table. I edited that with BooITNG and by chance my data partition got deleted](*,) but no problem i have the backup:D. Now the next step install Linux> My current setup is :
5.7 gb for Ubuntu (it is Ubuntu 5.10 i386 + i ordered the CD)
1 gb for Swap (I have Lots of space now )

Now, i am thinking if i install Ubuntu then how can i boot in Windows ? I dont think i will be able to connect to internet easily so i want to make sure i know everything before doing anything. Just tell me the precautions and how can i multi boot if i install Ubuntu. Thanks..:KS

---

### Post by CaveRat on 2006-11-23
One thing you will definately need to do is defrag Windows before installing Linux. Windows software spreads itself all over the hard drive.

---

### Post by Ayush on 2006-11-23
> **CaveRat said:**
> One thing you will definately need to do is defrag Windows before installing Linux. Windows software spreads itself all over the hard drive.

[5.7 gb for Ubu and 1 gb for Swap ] both are now Free Space. I will format them when i install Ubuntu so idont think it is necessary to defrag.

---

### Post by adwait on 2006-11-23
As far as I understand, you have windows installed and have unformatted space on the disk to which you want to install Ubuntu, right? Well, in the installation program of Ubuntu, if you can see these partition correctly and create partitions in the unpartitioned space leaving the windows partitions alone, you should be fine. The dual boot will be auto configured without a problem.

Best of luck!

PS: If you are using any kind of PPPoE type of internet, just run
```
sudo pppoeconf
```

in Ubuntu and you should be able to access the net.

---

### Post by Ayush on 2006-11-23
> **adwait said:**
> As far as I understand, you have windows installed and have unformatted space on the disk to which you want to install Ubuntu, right? Well, in the installation program of Ubuntu, if you can see these partition correctly and create partitions in the unpartitioned space leaving the windows partitions alone, you should be fine. The dual boot will be auto configured without a problem.

Best of luck!

PS: If you are using any kind of PPPoE type of internet, just run
```
sudo pppoeconf
```in Ubuntu and you should be able to access the net.


New problems every day :evil:
I tried to install it. Everything was fine but at the package installation step (right after Installing Base system), when it reach 98% on the file xscreensaver (not sure), it reports a error that either the hard disk space is low or CD Drive is bad. Hard disk space cannot be the problem because i installed it on 3.20 gb and now i am installing it on 5.7gb. CD Drive cannot be bad because i have two (CD burner, DVD Burner). Tried in both twice, same pronblem. I think CD is bad. I dont have the iso image now because as i said before i deleted a partition by chance and the iso image was big so i never backed it up. I have formatted my partition 6 times now and i am thinking if i continue doing this, i will have a dead hard disk so i think i will wait for the CD (Shipped). But i installed it by skipping the step after 98% (it offers to skip). But problem is when there should be Welcome screen (after the boot screen "Loading modules" etc..), there is a DOS Prompt type screen with the following text (Ayush-Ubuntu is the computer name)
Ayush-Ubuntu login :
If i login by this way, there is still no gui. These lines appear after successful login (something like the following) :
ayush@ayush-ubuntu: 

I will wait for CD. Now i want to know how can i clear the info from MBR because the setup offered to put boot menu in MBR and i selected that cause i want to dual-boot with Windows.

---

### Post by Bachstelze on 2006-11-23
GRUB should offer the option to boot Windows anyway but to restore your MBR to default Windows' state, boot from a Win XP CD, go to a recovery console and run the command *fixmbr*.

---

### Post by adwait on 2006-11-23
Hmm, well since the CD was bad and you chose skip, some parts might not have been installed. Anyway, try to start the GUI by using
```
sudo /etc/init.d/gdm start
```
If that does not work, try executing
```
sudo dpkg-reconfigure xserver-xorg
```
and then try the first command again.

---

### Post by Ayush on 2006-11-23
> **adwait said:**
> Hmm, well since the CD was bad and you chose skip, some parts might not have been installed. Anyway, try to start the GUI by using
```
sudo /etc/init.d/gdm start
```If that does not work, try executing
```
sudo dpkg-reconfigure xserver-xorg
```and then try the first command again.

I removed it from Hard-disk so i cant try these . Thanks for your great help so far.:KS

---

