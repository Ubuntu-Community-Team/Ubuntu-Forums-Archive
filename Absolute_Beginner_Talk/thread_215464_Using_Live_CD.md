---
title: "Using Live CD"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by favad on 2006-07-14
I'm new to Ubuntu and infact linux, although I have been using Windows for many years.

I tried booting from the Live CD and was able to do so except that my modem drivers were not installed. Plus I could not play a .dat movie file although I could see the graphical display. Moreover is there a way to access my NTFS formatted partitions in Linux.

I would be grateful if someone could tell me whether there was something like an automated online check to check my hardware compatability for linux (Ubuntu). If not where could I get the linux drivers for my listed hardware.
Hard disk   ST380011A
Video Card  VIA/S3G PCI Slot
Fax Modem   Lucent Dual Chipset Hardware modem V.92
Motherboard GENX P4M800-G
LAN Card    VIA Rhine II Fast Ehernet Adapter
Sound Card  Realtek AC'97 Audio for VIA(R) Audio Controller

favad

---

### Post by Dr. Nick on 2006-07-14
To access ntfs look [here]("http://www.psychocats.net/ubuntu/mountwindows.php")

To play movies you probably need codecs, i would get those after installation , search "w32codecs" in the forums

Dont worry about your hard drive, it will work
I believe I have the same ethernet and sound as you, mine a a k8m800 borad i believe so it has alot of the same via stuff, worked out of the box.

sorry not sure on the modem

---

### Post by trent dillman on 2006-07-14
You might luck out with the modem, seeing as how it's a Lucent. The .dat movie files require mpeg decoder plugins, which are available but not included on the live cd due to licensing issues. Yes, you can read your NTFS partition, but you probably shouldn't enable writing.

If you decide to install Ubuntu, we would be glad to help you with all of these things if they do not work out of the box.

---

### Post by favad on 2006-07-14
Thank you Dr Nick, but I feel understanding and implementing those codes isn't really simple for a newbie. 

Secondly as far as installation is concerned, I would love to install Ubuntu, but would definitely not want something wrong to happen to my precious Windows installation and files. So please let me know if I can do it without any risk of fiddling with my Win XP-SP2 installation.

And as far as modem goes, is it only a driver issue as it was recognized by Ubuntu. How can I find the modem details like whether it is a soft modem or DSP modem etc

favad

---

### Post by Dr. Nick on 2006-07-14
Installing the codecs is a pretty simple task, Thier are many step by step guides

Like
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full)

About windows, when installing a differnt OS thier is always the option of messing up the previous, You just have to take percautions in case. I would reccommend using the link above to access your ntfs off of the livecd and backup any important data files to a cd or external harddrive, usb stick etc..
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)


If you are very concerned their are applications you can use to make a image of your hard drive just in case. If you are carefull in the installation that shouldnt matter though, You can install ubuntu without messing up your XP, just **do not** format your ntfs partiton in the installer, If it all works as it should then you will get a screen at bootup asking if you want Windows or Ubuntu. 

If you make some good backups first then I wouldnt worry.

Unfortunately I have no expierence with modems :(

---

### Post by BobSongs on 2006-07-14
This is a general answer as far as modems are concerned.

Many modems built today are called "WinModems". The problem for GNU/Linux systems is that it's more than just a "driver" that's required. These puppies are built to have Windows do half the work (obviously increasing the workload on the system). Getting them to work in Linux means figuring out what **isn't** done by the modem and writing all that from scratch.

I believe there's a list of WinModems where hackers have successfully gotten them to work in Linux. But I don't have that at my fingertips. This is just to let you know that some equipment doesn't work with Linux and why.

If you seriously consider using Linux, then consider the possibility of having to research components in future to ensure they are Linux compatible.

---

### Post by favad on 2006-07-15
Ok thank you everybody. The good part is that I'm in a position to proudly acclaim that I have installed Ubuntu (Registered Linux user #422598) on my computer, and its working barring a few problems. Now the details

I will try installing the codecs and plugins, so I guess they should start working. However even with a 2.4Ghz machine and 
352MB ram it is running extremely slowly. I installed Linux on a separate 4.3GB hard disk, and out of it 2.5GB are free.

Finally is there a simple way to access my NTFS partitions then the one provided by Dr Nick, because I simply don't get it.

favad

---

### Post by Dr. Nick on 2006-07-15
Try looking at System - Administration - Disk and you may be able to get it.Also what video card do you have? If you have a nvidia or ati then you may need to install the 3d drivers to speed it up.

---

### Post by favad on 2006-07-15
Thank you for your advise Dr, but speed isn't the main issue once Ubuntu starts up, over there its pretty ok, but it takes too long to come to the desktop i.e almost 4 big minutes (8 times slower than my XP bootup). My swap partition auto-created by Ubuntu is only 203MB, is it enough or should I increase it to something like 700MB. Even then I'll have 2.0 GB of free disk space in Linux Ext 3.

favad

---

### Post by Dr. Nick on 2006-07-15
The size of swap really depends on how much memory you have, I think some people say swap should be 1.5x your physical ram. I have 1gb of ram and dont even have a swap and its fine.

To speed up boot try here
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

I havent done this before though.

---

### Post by favad on 2006-07-16
I tried installing the decoders, using the steps given on [http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full)
However it only updates the links to the correct repositories, and I need to be connected to download the correct decoders. Is there a way with which I can download these complete codecs set in Win XP, and then install them in Ubuntu, or can I install them from the default install CD?

favad

---

### Post by Dr. Nick on 2006-07-16
is your modem your only means of webaccess?

You can get the w23codecs in windows and install it on ubuntu pretty easily, the others like gstreamer-xx are more difficult because they have dependencies that need to be handled.

look on the internet for a .deb for w32codecs, They are out their, but I dont think I can provide a link here since they can be illegal in some circumstances

---

### Post by favad on 2006-07-17
14MB .deb file from the w32codecs link on this page [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 
However when I wanted to install it, it said that the Archieve manager did not support this format. Could u please help me in this regard.

Furthermore is it possible to setup a home network through my LAN Card with another Win XP PC.

---

### Post by Dr. Nick on 2006-07-17
> **favad said:**
> 14MB .deb file from the w32codecs link on this page [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 
However when I wanted to install it, it said that the Archieve manager did not support this format. Could u please help me in this regard.

Furthermore is it possible to setup a home network through my LAN Card with another Win XP PC.

On that link you posted did you use the wget command? If you did then run 
[SIZE=4][B][SIZE=3]
[SIZE=2] sudo dpkg -i w32codecs_20060611-0.0_i386.deb[/SIZE][/SIZE][SIZE=2]
[/SIZE] [/B][SIZE=2]
right after the download completes from the same terminal window, If you didnt then just 
open up a terminal and cd to the diretory containg the deb file and run the line above
[/SIZE] [SIZE=2]
You need samba to set up a network, I havent used it though[/SIZE]
[/SIZE]

---

### Post by favad on 2006-07-18
The package was saved in my USB aswell as my Ubuntu desktop. I wrote 

the command in Terminal and this is what I got. I guess I couldn't 

provide the correct location. 

[B]favad@ubuntu:~$ sudo dpkg -i w32codecs_20060611-0.0_i386.d
dpkg: error processing w32codecs_20060611-0.0_i386.d (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
w32codecs_20060611-0.0_i386.d[/B]

Secondly I was also not successful in mounting the NTFS partitions. The 

first few steps worked right but **sudo nano /etc/fstab** command 

did **not** show any NTFS stuff like the one ([B]/dev/hda1 

/media/hda1 ntfs defaults 0 0[/B]) shown in example over here 

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
I have pasted in bold a copy of the commands and their results ias 

shown in the Terminal.


[B]favad@ubuntu:~$  sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1670    13414243+   7  HPFS/NTFS
/dev/hdc2            1671        3035    10964331    7  HPFS/NTFS
/dev/hdc3            3036        9729    53769555    f  W95 Ext'd (LBA)
/dev/hdc5            3036        5959    23486998+   7  HPFS/NTFS
/dev/hdc6            5960        9729    30282493+   7  HPFS/NTFS

Disk /dev/hdd: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         450     3614593+  83  Linux
/dev/hdd2             451         524      594405    5  Extended
/dev/hdd5             451         524      594373+  82  Linux swap / 

Solaris

Disk /dev/sda: 126 MB, 126976000 bytes
16 heads, 32 sectors/track, 484 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         485      123984    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(482, 15, 32) logical=(484, 5, 32)
favad@ubuntu:~$ sudo mkdir /windows
favad@ubuntu:~$ sudo cp /etc/fstab /etc/fstab_backup.
favad@ubuntu:~$ sudo nano /etc/fstab







# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0    

   1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0










                                [ Read 9 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur 

Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To 

Spell[/B]

I'd again request u to please read all this and then solve my problem 

for good.

favad

---

### Post by Dr. Nick on 2006-07-18
!st problem, It is .deb not .d  Judging by your output
[B] dpkg: error processing w32codecs_20060611-0.0_i386.d (--install):
cannot access archive: No such file or directory 

[/B]it is saying it cant find w32codecs_20060611-0.0_i386.d when it should be w32codecs_20060611-0.0_i386.deb, so try from the termial in either your usb dir , or your desktop dir

[B] sudo dpkg -i w32codecs_20060611-0.0_i386.deb
[/B] 
On your 2nd problem, your ntfs will not show up in fstab by default sometimes. you simply need to add the correct lines, Looking at your fdisk output it would appear that you have several ntfs partitions
[B] /dev/hdc1   *           1        1670    13414243+   7  HPFS/NTFS
/dev/hdc2            1671        3035    10964331    7  HPFS/NTFS
/dev/hdc3            3036        9729    53769555    f  W95 Ext'd (LBA)
/dev/hdc5            3036        5959    23486998+   7  HPFS/NTFS
/dev/hdc6            5960        9729    30282493+   7  HPFS/NTFS

[/B]Your situation is a bit different from the example since it looks like you have multiple physical hard drives, that may be why its not their already. this is what I would add to your fstab** /dev/hdc1**[B] /windows        ntfs    nls=utf8,umask=0222        0       0
[/B]In linux your first ide hard drive is hda, your second is usually hdb and so forth.[B]

that will add one of the ntfs partitions, If you want to add the others try adding 

[/B]** /dev/hdc2**[B] /*somedir*        ntfs    nls=utf8,umask=0222        0       0
[/B]** /dev/hdc5**[B] /*somedir*        ntfs    nls=utf8,umask=0222        0       0
[/B]** /dev/hdc6**** /*somedir*        ntfs    nls=utf8,umask=0222        0       0**

I have used ***somedir*** because you need to have a seperate directory for each partition you are mouning, you will already have one mounted in /windows from the first ntfs partition in your fdisk output. I dont know your partition setup, but if you have a partition of just mucic or something then run this

sudo mkdir /music

then replace /somedir in the fstab with /music on the approprite partition number

So if you just wanted to add your first ntfs partition your entire fstab should look like this, if you want to add other partitions then just do the mkdir command and specift that directory in your fstab as the moun point

```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0    

   1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#ntfs partitions

/dev/hdc1 /windows        ntfs    nls=utf8,umask=0222        0       0
```

after doing this run 

[B]sudo mount -a 

[/B]and see if it gives any errors

---

### Post by favad on 2006-07-18
I am sorry that I pasted it wrong, I did write it complete with .deb and doubly checked it. May be I am not accessing the USB or desktop dir completely, do I need to give some other command cuz I just opened terminal from my desktop and wrote sudo dpkg -i w32codecs_20060611-0.0_i386.deb

As regards your second answer I would thank you in advance. I have 4 NTFS partitions and will try to mount all of them separately.

favad

---

### Post by Dr. Nick on 2006-07-18
ok, well if you just launch a terminal chances are it is not in the desktop directory, you can run

** ls **

to get a file listing if you want. Just open a terminal from Applications - Accesories -  Termial

and then
[B]
cd Desktop[/B]

to get into your desktop, Capatilize the D, it is case sensitive, then rerun the commands sido dpgk -i .... and it should work.

---

### Post by favad on 2006-07-19
The good part is that I successfully mounted all my NTFS partitions as well as installed the codecs, the details of which are pasted below for reference.

[B]favad@ubuntu:~$ cd Desktop
favad@ubuntu:~/Desktop$ sudo dpkg -i w32codecs_20060611-0.0_i386.deb
(Reading database ... 56980 files and directories currently installed.)
Preparing to replace w32codecs 1:20060611-0.0 (using w32codecs_20060611-0.0_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20060611-0.0) ...
favad@ubuntu:~/Desktop$[/B]

However I was only able to play .avi files, and also couldn't see the video. .dat, .mpg and .wav files were not played, and it again said that it required codecs to play. Furthermore I selected that option from **Multimedia System Selector **which gave me that coloured small screen output when I pressed Test button. It was something with (No XV) in brackets. I would be grateful if you could guide me a bit here.

Lastly I created an extra folder when mounting my NTFS partitions, I could not delete it from the browser window, how else can I delete it?

favad

---

### Post by Dr. Nick on 2006-07-19
you can delete the extra folder only as sudo since you were sudo when you createed it

you can run 

**sudo rmdir /path to directory**

to remove it. Make sure you give the path as you did on the mkdir command so you dont erase the wrong one, its case sensitive aswell

example
sudo mkdir /windows
sudo rmdir /windows

The video is a somewhat different issue, I have had best luck with mplayer over totem, I dont know much on totem so if thats what you are using then unfortunately I cant be much help :(

---

### Post by favad on 2006-07-19
And where can I get that mplayer from, is it on the CD or will have to download from somewhere? Would it be able to play all common formats?

favad

---

### Post by Dr. Nick on 2006-07-19
It is not on the cd, but in the universe repository. If you have internet you can install it from synaptic after editing your /etc/apt/sources.list to include the universe repo..

If you have no internet then it is a real pain to get, but you could get it here
[http://packages.ubuntu.com/dapper/graphics/mplayer](http://packages.ubuntu.com/dapper/graphics/mplayer) but you would have to download all the dependencies seperate.

You could also look at vnc using the same methods, I would also open synaptic and search gstreamer and install all the gstreamer .1 pacages to get support for more codecs

---

### Post by favad on 2006-07-20
Ok thankyou I'll try to do that. A small word about modems. I was able to search and find the Linux drivers made for my **Fax Modem Lucent Dual Chipset Hardware modem V.92**. Now I remember you saying that you couldn't help me much as far as modems were concerned, but still if u could help me choose the correct driver out of the 3 given for various Linux distributions as there wasn't one mentioned for Ubuntu straightaway. I'd be grateful if you could give a quick look to this page.
[http://www.physcip.uni-stuttgart.de/heby/ltmodem/index.html#documentation](http://www.physcip.uni-stuttgart.de/heby/ltmodem/index.html#documentation)

Moreover please also tell me how to install from files like **ltmodem-8.31a10.tar.gz** Should I extract the files in a folder on Desktop or do I have to run some sudo command?

favad

---

### Post by Dr. Nick on 2006-07-20
I checked out that page and do not see any drivers that are for the 2.6 series of kernels which is the current. I followed a few links around thier and found some ubuntu drivers, but they to were for older kernels :( It looks like you may have just one of them pieces of hardware that can be a pain to get running.

This page will guide you for installing .tar.gz for future reference, alot of them also include a install file that will give instructions

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

If you can find out a specific model number of your modem ( I am not sure if thier is a more specific name/version then the **Fax Modem Lucent Dual Chipset Hardware modem V.92**.) then you may be able to find some info on the forums, or start another topic specifically for modem help and get a few more people to help some.

Good luck

---

### Post by favad on 2006-07-21
I tried the Live CD of Slax 5.06, it had builtin support for my sound, VGA and all, it played all Windows formats of video files, showed NTFS partitions. Moreover it was running quiet fast. It is only 200MB in size and should take 700MB when installed to hard disk. Now I know this is different from Ubuntu but I suppose an easier form of Linux for a newbie like me, and free from all those tools in Ubuntu that I don't intend to use atleast for the next 365 days. Although it also did not install drivers for my modem, but still it really did fascinate me. Do u think I should leave Ubuntu for the time being and go for it, or wait for the Ubuntu 6.06 to reach my place, install it and see if it does any good?

And again thank you for all the help and support u provided me and continue to do so.

favad

---

### Post by Dr. Nick on 2006-07-21
Its really up to you, you can always switch back and forth between them. To start off I would find the distro which requires the least effort to get started. This way you can become a little more accustomed to linux in general which might help in the future if you try other distros. 

One of the nice things about linux is that most distros have a realtively fast release cycle, The next version of ubuntu is planned to come out in 3 months or so, who knows how well it might work out on your hardware. Ubuntu wanst my first distro, more like my 5th, thier was always something bugging me about the previous ones I tried, until I found ubuntu which required the least to get running good for me.

Hope you get linux(whichever you choose) setup good for your needs

---

### Post by favad on 2006-07-24
Thank you for your piece of advice. Just in case u were wondering where I have been, I downloaded VMWARE 5.1, installed Ubuntu 5.10, and it is working though a bit slow asI have to share RAM. The good part is that I am able to connect to the internet through virtual networking with windows XP. I was trying to login into MSN through GAIM, and also read a few articles on the forums about setting things up, but it was continously giving me error **Unable to authenticate .NET Messenger Service** I tried Global Proxy settings, no proxy as well as Environmental Settings but was only able to receive the same error message.

favad

---

### Post by Dr. Nick on 2006-07-24
vmware is a pretty good idea to be able to get online in ubuntu, I never use msn messanger so not sure what the error message means, If it only occurs when you are trying to get into msn messanger then I would suspect that they dont like you using gaim or something. I think their is  aMSN in the repositories if you wanted to try it, I have never used amsn and only use gaim for aol IM

---

### Post by favad on 2006-07-29
I tried installing amsn 0.95-1.ubuntu but some errors occurred, I tried doing it again and the log is pasted below. I'll be grateful if u could tell me how can I make it work, and after installation where would it be located in my start menu or desktop. I guess there is some problem with dependencies.

**favad@ubuntu:~$ sudo -i root@ubuntu:~# dpkg -i /home/favad/Desktop/amsn-0.95-1.ubuntu.deb (Reading database ... 57602 files and directories currently installed.) Preparing to replace amsn 0.95-1 (using .../Desktop/amsn-0.95-1.ubuntu.deb) ... Unpacking replacement amsn ... dpkg: dependency problems prevent configuration of amsn: amsn depends on tcltls; however: Package tcltls is not installed. amsn depends on libgcc1 (>= 1:4.0.2); however: Version of libgcc1 on system is 1:4.0.1-4ubuntu9. amsn depends on libstdc++6 (>= 4.0.2-4); however: Version of libstdc++6 on system is 4.0.1-4ubuntu9. dpkg: error processing amsn (--install): dependency problems - leaving unconfigured Errors were encountered while processing: amsn **

favad

---

### Post by Dr. Nick on 2006-07-29
Actually amsn is in the repos if you have the "universe" enabled

try 
[B]
sudo aptitude install amsn[/B]

that should handle all the dependencies for you, I would guess it would show up in Applications - Internet

---

### Post by favad on 2006-08-02
I connected to the internet and started amsn, it automatically downloaded the missing packages after taking me through another small wizard, and has actually started working, so thanks for the idea.

Furthermore I feel I have got almost allof my stuff working besides modem **Fax Modem Lucent Dual Chipset Hardware modem V.92**. Presently I'm running Ubuntu on VMware with the help of which I can connect to the internet, but can only allocate a little more than 128MB RAM, so I really want to get my modem working at any cost. I am just wondering if Ubuntu 6.06 which I have ordered would have a better support for my hardware. Otherwise could u please tell me how to find any further details of my modem before starting a new thread for its drivers.

favad

---

### Post by Dr. Nick on 2006-08-02
are you on 5.1 stil like it says in your profie?

6.06 has batter hardware support then 5.1 But thier are not differnet versions of 6.06. A iso downloaded and burned will have the same hardware support as one ordered.

you can run the command

lspci

and it will show you details on all pci devices installed.

What may be easiest is to get a new modem that you know will work via researching some, not the best fix but may be easier then spending hours trying to get the current one to work.

---

### Post by favad on 2006-08-04
I am using 5.10, and am waiting for 6.06 to reach my place.
And as far as modem is concerned I also wanted to go for a cheap Linux supported internal 56k modem. I have seen a few with my local dealers as well as online but I couldn't really figure out if they would work with Linux. Here are a few models I found in the internal modems range. I will be grateful if you could tell me whether they would be supported by Ubuntu. Is there a site where I can check their compatability or see a complete list.

[B]Zoltrix Fax Modem
Conexant 1456VQH 56K V.92 PCI Modem
ESS 56K V.90 PCI Data/Fax Modem
NetoDragon ENF656 56K V.92 PCI Data/Fax Modem
ECS 56K V.90 PCTel AMR Modem[/B]

favad

---

### Post by Dr. Nick on 2006-08-04
6.06 will have more hardware support for the sole fact that it is abit newer, cant tell you though if it will support your current hardware or those you have listed.

If you want to try to get your current one running then you may look here
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

that seems to be very indepth on modems, I just saw it, but have never  set up any modem in linux so I dont understand all of it.

You may just read other threads on here about modems using the search and see if you see a trend of modems that work well

---

### Post by favad on 2006-08-04
> **Dr. Nick said:**
> I checked out that page and do not see any drivers that are for the 2.6 series of kernels which is the current. 
Good luck

Well thank you again for your continous support. I have actually found an updated version of more or less the same site which is supposedly providing drivers for my 2.6 series of kernels. It says here [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem) 
**For ltmodem support for 2.6 kernels, please go to [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/). **
Now over here could u please tell me how and what to download. As I believe they are for Lucent modems using 2.6 kernels.

favad

---

### Post by Dr. Nick on 2006-08-04
well on that 2nd link you mentioned their are some drivers made especially for ubuntu. Those are actually for 5.10 like you have. If they indeed work then they may have been included with the kernel in 6.06, that has been know to happen with some things in the past.

If you want to try them on 5,1 then open a terminal and type

uname -r

That will tell you which kernel you are running, If the result is either of these
[FONT=monospace]__[/FONT]
2.6.10-5-386
2.6.12-9-386
2.6.12-10-386
2.6.12-10-686
2.6.12-10-k7


Then go to [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem) and download the corresponding driver, If you have a choice I would get the 8.31b1 ones as they are probably newer. You must get the .deb file that matches the kernel version of uname -r exactly

After you have saved it then open a terminal and cd to the directory the .deb is saved in and run

[B]sudo dpkg -i [I]fullfilename

[/I][/B]and that should finish it.

Of course if you install 6.06 then the above driver .debs will not work since they are too old for 6.06, you may be able to get the .tar.bz2 files on the same server and build the drivers from source which can be a bit of a pain, Or 6.06 kernels may actually include the drivers

---

### Post by favad on 2006-08-04
I matched my kernel version **2.6.12-9.386** and downloaded and insatlled the **ltmodem-2.6.12-9-386_8.26b1_i386.deb** package. Then I also checked the hardware installed by giving lspci command, the resulting list also included the modem. I tried going through the logs of the commands I gave in terminal but couldn't really help myself :confused: . Unfortunately I wasn't even able to figure out if things had worked according to plan so I have attached the logs with the post. Moreover the Autodetect modem feature in Network Conections also failed to detect my modem, giving the error message "Modem busy or not connected".

I know this is quiet boring stupid stuff, but if u could guide me a bit further I may be able to finally get online through Ubuntu.

favad

---

### Post by Dr. Nick on 2006-08-05
hmm, maybe try this first

sudo apt-get isntall build-essential

I saw a few gcc errors in the logs, the above may solve that. also run 

sudo apt-get install linux-source

as I think I saw a error in refrence to kernel source.

Now that you have a bit more information and ideas on what to do, it may be worthwile to go ahead and start a new thread, starting a specific thread may get you help from people who have done this before unlike myself.

I am not sure how this will all work going through virtual pc, but it is worth a shot I guess


Good Luck

---

### Post by favad on 2006-08-05
Ok now the good part is that somehow when after restarting the system my modem was autodetected and I was actually able to dial and connect to the service provider. It actually did connect as my phone line got busy and there was a connection log with my service provider. However there wasn't any connected icon sort of thing like in Win XP. When I tried to open some website in Firefox and get online with amsn they also gave error message "could not connect to the server". Now one thing I am still not sure about is that do I need to configure some extra things in the modem properties area, like host name, DNS, or even something related to protocals.

I also tried the commands u asked me too but neither of them seemed to work. The log is pasted below.
[B]favad@ubuntu:~$ sudo apt-get install linux-source
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source
favad@ubuntu:~$ sudo apt-get isntall build-essential
E: Invalid operation isntall[/B]

Moreover I am doing all this on actual physical system and not on some Virtual Machine, although I have a separate copy installed on VMware, but it only picks a minimum set of required hardware and not other stuff like modems.

favad

---

### Post by Dr. Nick on 2006-08-05
well them 2 commands may not be necessary if the driver actually did install.

I see now that I had a typo in the 2nd command use "install" instead of "isntall" I am doing this all from 6.06 so some of the names may have changed abit since 5.10.

You can open synaptic and search for linux-source and you will probably see a specific version which matches the kernel, or you can try

sudo apt-get install linux-sourc*

Since you are doing this on a physical machine they may not work if the packages above we are trying to install are not included on the cd since you dont have a web connection anymore

But atleast your modem is deteced now, may just be a matter of getting some settings changed.

---

### Post by favad on 2006-08-06
Actually thank you yet again for all this help, but I'll probably not try them as my modem is working and am actually writing this after loging in from physical Ubuntu instalation.

Moreover I wanna install a few Windows based programs and games. I believe wine is required for that. Is it present in Ubuntu or otherwise where can I easily download it from.

favad

---

### Post by Dr. Nick on 2006-08-06
Wine is correct, their are a few pretty detaild howtos on it aready, like this one

[http://ubuntuforums.org/showthread.php?t=149585&highlight=wine+howto](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine+howto)

glad you got your modem to work.

---

### Post by favad on 2006-08-06
I think I forgot to mention that I had to manually add correct DNS nameservers for the dialup modem connection to work. 

Moreover I remember u telling me that Mplayer is supposedly the best as far as playing all common Windows Media formats like .dat, .mpeg and .wav etc is concerned. I downloaded the 3 basic files required for compiling the player. 
[B]MPlayer-1.0pre8.tar.bz2
essential-20060611.tar.bz2
font-arial-iso-8859-1.tar.bz2[/B]
Can u please guide me how to compile this, or if that is a difficult task what code can I write in terminal to automatically download the player or even just the right codecs as I can connect to the internet now.:) (thanks to u).

As regards wine I think that link's pretty useful so I'll try to get my things worke with it.

favad

---

### Post by Dr. Nick on 2006-08-06
I forget what I have mentioned and what i havent lol

but now that you have internet the automatix program may be just what you need

It will help you with some of the above/ mplayer,codecs,wine....

look here 
[http://ubuntuforums.org/showthread.php?t=223087](http://ubuntuforums.org/showthread.php?t=223087)

---

### Post by favad on 2006-08-07
And one more thing, over here it doesn't seem that I can make more than 1 connections and dial the one I want. **System > Administration > Networking** only allows me to permanently store **1** connection profile which it automatically starts dialing when system starts. Now can this not be like in XP where u can make as many connection profiles (for different Service Providers) as u want in Network Connections and then dial the one whenever u feel like (not necessarily at startup).

favad

---

### Post by Dr. Nick on 2006-08-07
click on the "location" box in networking and hit "create new location"

I tried using that method along time ago with limited suceess when dealing with wireless, It may be just what you need to have multiple profiles

---

### Post by favad on 2006-08-09
No doubt it is a Great "How To" for newbies like me, but there were a few problems when I tried to run wine for the first time using wt command. Here's the log, I would be glad if you could yet again help me fix things up from here.

[B]favad@ubuntu:~/winetools-0.9jo-III$ wt
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/favad/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
[/B]

As regards the location thing I tried it before too without success, it doesn't save separate profiles unfortunately, so I'll better stick to one account. Thanks anyways!

favad

---

### Post by Dr. Nick on 2006-08-09
Sorry dont know much of winw so not sure how to solve them errors, the link to automatix [here]("http://ubuntuforums.org/showthread.php?t=223087")
that I posted above allows you to install wine, not sure if it will fix the issue or not.

I guess they still have a few issues with the netwwork dialog, mine didnt save well either

---

### Post by favad on 2006-08-10
Ok I sucessfully configured samba networking client with another Win XP machine. Now I want to share my internet connection with that machine. Where can I start a wizard or pop up window to enable internet connection sharing. I could not find any option in the Networking panel in **System > Administration > Networking **. Can it be done without that dangerous terminal :rolleyes: 

favad

---

### Post by Dr. Nick on 2006-08-10
theis is not a option in the network panel.

I have never even attempted this before, but I believe the program "firestarter" has some options for this, Ive seen it before but never tested it. Irt doesnt look to har though

to install firestarter 
[B]
sudo apt-get install firestarter
[/B]
then to run it go to applications - Internet - firestarter.

Their will be a wizard run once it starts that has some options to configure it, If you need help you may have to just search around the forums since I havent done it before.

---

### Post by favad on 2006-08-15
When I gave the following command (**sudo apt-get install firestarter**) in terminal to run firestarter it listed some unmet dependencies and gave the following error. 

**W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)**

Anyways I'll try to fix that, and it isn't something really important too so thanks for your help. 

Furthermore I downloaded Real Player 10 for Linux .bin file and followed the 2 simople steps given here [http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8083677&pageregion=install_instructions&src=linux&pcode=rn&opage=linux](http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8083677&pageregion=install_instructions&src=linux&pcode=rn&opage=linux) but things didn't work. Are .bin files supported by Ub untu or will I have to download the .rpm package. May be u could share your thoughts on that.

favad

---

### Post by Dr. Nick on 2006-08-15
Yes, bin files should be suported. Find the .bin file and right click on t and hit "properties" then permission tab, make sure execture is checked.

Also automatix can install realplayer if you install it
you can get it here
[http://ubuntuforums.org/showthread.php?t=223087](http://ubuntuforums.org/showthread.php?t=223087)

---

### Post by favad on 2006-08-15
Actually I got my Ubuntu 6.06 CD today, so I now stand in equal terms as far as Ubuntu version is concerned.8) 

But somehow there was a serious problem connecting to the internet. Although it even installed the drivers itself and everything went fine but disconnedted within seconds or probably just dialed and never got connected. I tried 2 different ISPs and they worked on my WIN XP 5 minutes later. I think I need to decrease the modem speed which is causing connection to break and not establish on my slow telephone line. Is there a way I can change my modem speed or install the drivers I used in Ubuntu 5.10? Unlike Win XP Ubuntu dialer doesn't give the error messages, so it is difficult to trace the exact error.:confused: 

Moreover although it enabled my NTFS partitions and even showed them in My Compuiter it refused to open them and show the data. Now is this a problem which can be rectified or should I also opt for the older NTFS access method?

Thank you very much for taking out your precious time and helping me convert for good. maybe:) 

favad

---

### Post by Dr. Nick on 2006-08-15
not sure how to control modem speed, you can not use the older drivers though, they are specific to the 5.10 kernel, but if the modem is detected maybe drivers are now included..

Here is how I set up my ntfs
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

I would look at your /etc/fstab file and see if its different the **nls=utf8,umask=0222 0 0** part specifically. I had a bit of a issue with mine, if you tried this method make sure you werent sudo when you created the folder to mount it to, that will make it unreadable.

---

### Post by favad on 2006-08-25
Issues with my modem now almost stand resolved, as I finally managed to connect to internet today, thanks to the links u gave me. 

Now a word about codecs and videos. We have had enough discussion on that but could u please tell me 1 video format which Ubuntu 6.06 natively supports, so that I can atleast find out if its a codecs issue or some VGA Card Drivers problem.

Lastly as u have tried a number of Linux Flavours, could u please reccomend me the best Linux for a PC with only 128MB RAM and a slow old Intel machine. DSL, Puppyos etc etc :) 

favad

---

### Post by Dr. Nick on 2006-08-25
> **favad said:**
> Issues with my modem now almost stand resolved, as I finally managed to connect to internet today, thanks to the links u gave me. 

Now a word about codecs and videos. We have had enough discussion on that but could u please tell me 1 video format which Ubuntu 6.06 natively supports, so that I can atleast find out if its a codecs issue or some VGA Card Drivers problem.

favad

You would probably have best luch with a mpeg or avi. Its really hard to tell what is supported natively as a mpeg file can be encoded differently then another mpeg. I will say to avoind wmv files as they are windows media and are not supported "out of the box"

---

### Post by favad on 2006-08-27
While I try to setup my codecs, could u please help me edit GRUB Boot Loader. I have 2 Hard disks 
**1** 80GB Win XP
**2** 4GB Ubuntu 6.06
I have set up in BIOS disk **1** as first boot option, and disk **2** as second boot option. Whenever I want to boot from disk **2**, I have to enter the setup and select disk **2** as primary boot disk.

My GRUB Boot Loader is installed but obviously doesn't show Win XP as it is on the other hard disk with separate MBR written. I want to include this Win XP boot option in the list so that I can boot into Win XP or Ubuntu 6.06, without going into setup everytime. 8) 

Lastly as u have tried a number of Linux Flavours, could u please reccomend me the best Linux for a PC with only 128MB RAM and a slow old Intel machine. DSL, Puppyos etc etc :) 

favad

---

### Post by Dr. Nick on 2006-08-27
Grub is controlled by the file /boot/grub/menu.lst

If you open it up using

gksudo gedit /boot/grub/menu.lst

then you can add a windows entry. In your case I would think this entry would be correct

>   title        Microsoft Windows XP
                          root        (hd0,0)
                          savedefault
                          makeactive
                          chainloader    +1

The above root (hd0,0) is for the fisrst partition of the first hard drive, Which is where windows probably is. Just add that entry to the very bottom of the menu.lst file and set the bios to boot from disk 2 and see if that helps.

I ran a full gnome using regular Ubuntu breezy/dapper on my p2 366 with 128mb of ram. It wasnt the fastest but was tolerable. If you want speed you could look into xbuntu. I have briefly used dsl and puppy, they are both pretty fast but can take a little more to configure.

---

### Post by favad on 2006-08-27
[B]title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot[/B]

This is what it shows already. In Ubuntu Disk Manager it shows my Win XP boot drive as /dev/hdc1. 
So now could u please tell me what to do. In case if I do something wrong and make Ubuntu unbootable, would I be able to correct it by booting from Live CD or otherwise?

favad

---

### Post by Dr. Nick on 2006-08-27
as long as you dont mess with the ubuntu entries you shouldnt be able to make it unbootable, but if it did you should be able to correct it with the live cd.

dev/hdc sounds weird for the windows drive name, to confirm run

**sudo fdisk -lu** from the terminal and see which drive is ntfs.

If your windows hd is the primamry drive, and drive 1 in your bios then I would guess It should be /dev/hda 

The above entry that I posted may work, If not then you can try different combinations in the root(hdx,x) section until you get it to work. I will post the end of my file showing how mine is, I have 1 hd with windows on the 1st partition and  Ubuntu on the 3rd
```


## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-26-k7
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by favad on 2006-08-28
[B]favad@Intel2400mhz:~$ sudo fdisk -lu
Password:

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63    26828549    13414243+   7  HPFS/NTFS
/dev/hdc2        26828613    48757274    10964331    7  HPFS/NTFS
/dev/hdc3        48757275   156296384    53769555    f  W95 Ext'd (LBA)
/dev/hdc5        48757338    95731334    23486998+   7  HPFS/NTFS
/dev/hdc6        95731398   156296384    30282493+   7  HPFS/NTFS

Disk /dev/hdd: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders, total 8421840 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *          63     8000369     4000153+  83  Linux
/dev/hdd2         8000370     8418059      208845    5  Extended
/dev/hdd5         8000433     8418059      208813+  82  Linux swap / Solaris
[/B]

This is what is shown by the command, and I have already pasted you log of this command **gksudo gedit /boot/grub/menu.lst**. However I'm still confused how my Win XP boot partition is referred to as even the Linux partition over here is referred as hdd1 and in GRUB Boot Loader list as (hd0, 0)

I tried (hd1,0) and this (hd1,1), but they were mere guesses and they dint work. I dont think changing the boot options in BIOS should make a difference as long as I choose to boot from my Linux Hard Drive.

favad

---

### Post by Dr. Nick on 2006-08-28
Still weird that your 1st hard drive is hdc, but ohwell it shouldnt matter, just not what I am use to lol.  Is the computer a homebuilt or store bought? With it calling then hdc and hdd it would appear that both hard drives are plugged into a single ide cable which is plugged into the secondary ide port, not the primamry ide port on the motherboard. When I have 2 hds they are assigned hda and hdb while my cdrom on the secondary controoler gets the hdc.

The numbering method used by grub is sort of tricky at first, It starts at 0 instead of 1 
from [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

> **A Quick Guide to Grub's Numbering System  **First partition = 0  second partition = 1  third partition = 2 ... and so on 
                                       first hard drive = (hd0),   second hard drive = (hd1),   third hard drive= (hd2) ... and so on.
                                       floppy disk drive = (fd0)
                                       
                                       first partition on first hard drive = (hd0,0)            first partition on second hard drive= (hd1,0) 
                                        2nd partition on first hard drive = (hd0,1)            2nd partition on second hard drive= (hd1,1) 
                                        3rd partition on first hard drive = (hd0,2)             3rd partition on second hard drive= (hd1,2)  
Now windows appears to be bootable on the 1st partition of hdc, the * indicates the bootable partition. Since you have hdc It may be root(hd2,0) This is how I understand it to work

hd0 = hda
hd1 = hdb
**hd2 = hdc**
hd3 = hdd

But looking at your previous posted menu.lst file confuses me, it had ubuntu set to be root 0,0 which would mean that grub believes that ubnutu is on the first partition of the first drive, when it is actually on the 1st partition of the 2nd. I am not exactly sure how to troubleshoot that, I dont know why grub doesnt see your windows hd as hd0. I have a idea you could try, but I have never used it myself. It is the "map" option. map will trick windows into thinking it is on a different drive via the grub menu.lst file

I would have guessed that hd1,0 would have worked, what if any error messages did it give you? If you want to try the map trick then add this to the menu.lst 

>                                title        Windows XP
root        (hd1,0)
map        (hd1) (hd0)
map        (hd0) (hd1) 
makeactive
chainloader    +1 
That may or may not work. I havent seen many people with the same setup as yours (booting bios too 2nd hd) and i havent tried it myself. If the above doesnt get it to work correctly then you may start a specific thread for this issue to get more help.

It may be easier to install grub to the mbr of the windows drive and have the bios boot from the 1st hd instead of 2nd. I would think that would solve it for you. I would however check and make sure your drives are physically hooked up right, with the 2 hds on the primary channel and the cdroms etc on the secondaty channel. That may be a small part of the problem, but could probably be worked around if needed, Im just not sure how

---

### Post by --NightWing-- on 2006-08-28
since the thread says "using live cd", i have a big question. Am i supposed to be able to access internet when i boot off the live cd? coz i ve tried but it says server not found or some shit like that tho the computer has apparently been assigned an ip address through dhcp and the dns settings seem right.  Any suggestions?

---

### Post by favad on 2006-08-29
Actually the worst happened. Somehow Ubuntu managed to destroy my Win XP NTLDR. I tried FIXBOOT and FIXMBR to fix my Win XP using Recovery Console but without any luck. So much so that there wasn't even any Repair option in the Win XP setup and had to install all over over again. As regards Ubuntu I interchanged my primary and secondary masters.

At present they are like this:
[B]Both hard drives are plugged into a single IDE cable which is plugged into the primary IDE port on the motherboard.
Both CD ROM Drives are plugged into a single IDE cable which is plugged into the secondary IDE port on the motherboard.[/B]

I also have an explanation as to why it was showing (hd0,0) and not (hd1,0). When I installed Ubuntu 6.06 I physically disconnected my Primary Master (Win XP Hard disk) and so it could only detect one hard disk and create files and settings accordingly.

However I have told u my present IDE configuration and am not been able to boot into my Ubuntu installation. I think I can correct this menu list if I'm somehow able to access it from Live CD as u said before. I hope u can help me sort out this self created mess. :( 

favad

---

### Post by Dr. Nick on 2006-08-29
ew, sorry to hear the xp part. You can access the menu.lst from the live cd, when you doot off the live cd you may have your ubuntu drives already mounted, I dont recall how the ubuntu live cd does that.

If not then you can follow this page
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

and that should work, just make sure that you are not editing the menu.lst file for the live cd.

Good Luck

---

### Post by jerry_c on 2006-08-30
The live CD doesn't mount the hard drives. Those need to be mounted manually for browsing and editing. The link you gave is an excellent howto on that, Nick.

---

### Post by favad on 2006-08-30
Thank you people, I was able to access the file from the Live CD but it somehow got skrewed up again, leaving me with no option but to reinstall Ubuntu 6.06.

Now it has installed a GRUB Boot Loader on my Primary Master (i.e Win XP hard disk) Whenever I start my computer it starts, giving me options to start Win XP or Ubuntu, otherwise it boots Ubuntu after 10s. I want to configure it to automatically boot to Win XP by default and after waiting just 5 seconds (not 10). I hope you could help me do this. 

Furthermore I have successfully managed to setup networking with another Win XP machine using samba networking client. How can I enable Internet connection Sharing with internet connection available on Ubuntu machine?

Thanks for your continous help!

favad

---

### Post by Dr. Nick on 2006-08-30
I can help with the first half, The 2nd half may require the **firestarter **program that I mentioned a bit ago, I havnet ever done internet sharing though.

To make grub boot windows by default after 5 secs you can refer to a differnet part of the link above
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

Basicaly you change the number by **Default **to change the OS then change the number by **Timeout** to change the timer. So put a 5 next to timeout, and you will have to figure out the entry for default to get XP to boot as default, my guess  for the default would be 4, but you can double check that looking at the word "title" in the menu.lst as explained in the link, if you read through that part in the page it will explain a few ways to do it, and why everyones entry may be different

---

### Post by favad on 2006-09-01
Thank you very much that was a really helpful link indeed. It did exactly what I wanted. Moreover if something goes down with Ubuntu, I can reinstall it and it would fix itself as well as the Dual Boot MBR. However just in case my Win XP crashes, how can I repair it, cuz normally it would rewrite its own MBR, hence disrupting Ubuntu's configuration or would it be possible to install GRUB Boot Loader after reinstalling Win XP, so that it gives me option to start both OS again. 

Furthermore just wanted to know if Ubuntu 6.06 was codenamed Dapper? Is it the latest version? And this are these i386 and i686 different types of systems or is i686 a latest version sort of thing?

favad

---

### Post by Dr. Nick on 2006-09-01
Dapper is the latest version, the 386 and 686 just specify what processor it was meant for, the packages are the same version number with the same features, On the 386 installation you can install packages with a 686 or 386 in the name, either will work. The 686 packages are more customized for faster processors then the 386 ones are, the 386 are made to work on a wider array of systems, But the difference isnt really noticeable in some cases.

If XP crashes and you must reinstall it then you can reinstall grub using the live cd to restore your options to boot back into both. Reinstalling XP will overwrite grub, thier is no way to stop it

A few links to restore grub
[B][https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29)
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
[/B]
Thread about 363 vs 686 kernel
[B][http://ubuntuforums.org/showthread.php?t=243896&highlight=386+686](http://ubuntuforums.org/showthread.php?t=243896&highlight=386+686)

[/B]The kernel is the only package thus far besides mplayer that I notice a 386 and 686 version, If you have a realtively new processir , less than 5-6 yrs old or faster then 500mhz intel then the 686 should be just fine or the 386 will work aswell

---

### Post by favad on 2006-09-01
I have an Intel 2.4Ghz Celeron D, less than 3 years old. So by default does this CD install 386 packages or does it recognize the system automatically? 

As regards GRUB I installed puppyos on my older Intel 350MHZ. However it refuses to boot puppyos from its self-installed Boot Loader, (although it does boot Win XP) can I download and install GRUB separately through Ubuntu CD, Win XP or DOS to make both OS work from the boot options menu. :confused: 

favad

---

### Post by Dr. Nick on 2006-09-01
You can use synaptic to install linux-image-686 and then you will be fine, If you install that you will see a new option on the grub screen to use at boot, the old 386 option will remian just incase the new one doesnt work for some reason. 386 is always installed by default for simplicity sake since its the most compatible. Most packages it doesnt matter if you use a 386 or 686 one, most are made 386 but work just fine on 686. The linux-image package should be the  one that would really makes a difference if any

Not sure about the puppyos, never did a hard drive install, always stuck to the live cd. I dont think installing the grub from ubuntu cd would do much though as it should be the same version, or similar.

---

### Post by favad on 2006-09-03
Actually I don't really want to fiddle with my present Ubuntu configuration ifn there is any chance of messing things up. I'll definitely go for it if it makes a marked difference in speed. Moreover there are quiet a few options like 2.6.15-26.46, which is supposedly the latest: 

[B]Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP
This package contains the Linux kernel image for version 2.6.15 on
 Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV with SMP support,
the corresponding System.map file, and the modules built by the packager.

If you wish to update a bootdisk, or to use a bootloader to make
installing and using the image easier, we suggest you install the latest
fdutils (for formatting a floppy to be used as boot disk), and LILO, for
a powerful bootloader. Of course, both these are optional.

Kernel image packages are generally produced using kernel-package, and it
is suggested that you install that package if you wish to create a custom
kernel from the sources.[/B]

Do I just have to select it, apply and viola or is it something more than that?

And another thing about these programs Wine, Easy Ubuntu, Automatix, Real Player 10 etc. Do I always have to start them from Terminal, can I not put their short-cuts on start menu?

Plus I've actually downloaded and installed Automatix and Wine but donna where to start them??

Thanks for taking out your time! :) 

favad

---

### Post by 3rdalbum on 2006-09-03
> **favad said:**
> Do I just have to select it, apply and viola or is it something more than that?

It's that simple. It adds itself to your GRUB automatically. I didn't notice much of an improvement in speed when I went up to the k7 kernel, but if you're operating with lots of RAM it will probably improve things.

> **favad said:**
> And another thing about these programs Wine, Easy Ubuntu, Automatix, Real Player 10 etc. Do I always have to start them from Terminal, can I not put their short-cuts on start menu?

Many programs can be started from the Applications menu. I tried Automatix from its own repository, and that put itself onto the menu. Realplayer 10 I've had on the menu before. If you go to the Applications menu > System Tools > Applications Menu Editor, you can create new items for them.

Automatix can be started from the command "automatix". WINE is a special case; it doesn't have a graphical user interface, so you've got to launch it from the terminal. That's easy though: In the terminal, go to the directory which contains the program you want to run, and just do:

```
wine program.exe
```

(where "program.exe" is the program). Oh sure you can create launchers to Windows programs, but the first time you run one you should use the terminal... trust me on this.

---

### Post by Dr. Nick on 2006-09-03
I didnt notice a huge speed imporvememnt either going to the best kernel for my processor.

As said most programs can be used from the menu, Automatix made a shortcut for me under Applications - System tools. And it is usualy easierst to use wine from the command line, If you have one or two programs you always use wine for then you can make a shorcut on the desktop or panel by right cliking and hitting "create launcher" then using 

wine [B]program.exe

[/B]as the command

---

### Post by favad on 2006-09-04
Thank you 3rdalbum and good old Dr Nick! It really was helpful information.

However there is no System Tools menu atleast in my Ubuntu 6.06, I think it used to be in Ubuntu 5.10. 

Moreover I need a bit of help about using wine. Can I simply go to the folder in my Win XP NTFS partition and then write
Example: **wine IEXPLORE.EXE** or do I have to copy certain files in my Linux ext3 partition.

If I don't have to copy anything how can I access things. I tried to, just like in DOS i.e cd C: and then cd Windows cd Program Files etc, but here they are all mounted in folders, and so I couldn't really begin.

If I have to copy something can you please tell me what to copy exactly and where, in the case of Internet Explorer for example. I understand the rest with the help of it.

I also tried running a small .exe file game after pasting it onto my Ubuntu Desktop but failed to run. Here's the log:
[B]favad@intel2400mhz:~/Desktop$ wine LUMS CAR GAME.exe
wine: creating configuration directory '/home/favad/.wine'...
fixme: ole:ITypeInfo_fnRelease destroy child objects
wine: '/home/favad/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\LUMS.exe": Module not foun[/B]d

I'll be gald if you could help yet again.

favad

---

### Post by Dr. Nick on 2006-09-04
Go to Applications - Accessories - Alacarte Menu Editor

click System Tools on the first pane and see what options appear on the 2nd pane. put a check next to Automatix if you see it. The menu will not appear unless you have atleast 1 entry checked in alacarte. That may help you with shortcuts for real player aswell.

Its been to long since Ive messed with wine, But the cd and c: commands dont work with it if I recall. Just use ls and cd like you would regularry use in linux. 

I think the easiest thing to try would be 

wine sol.exe 

from your windows folder on the mounted windows partition, sol.exe is solitare I believe. I would use it since it most likely doesnt rely on any other files. If you are using wine mostly for Internet Explorer I believe thier is a guide on here for it

[http://ubuntuforums.org/showthread.php?t=149585&highlight=internet+explorer+wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=internet+explorer+wine)

That looks to be a pretty good guide on how to use wine

---

### Post by favad on 2006-09-05
Got my System Tools menu back, but how do I go to any of the disks from terminal. ex: my hda1 is mounted in tmp folder in my Filesystem. cd Filesystem from Terminal doesn't seem to work. I only know about cd Desktop which I think you told me before. Sorry about this but :-# 

favad

---

### Post by Dr. Nick on 2006-09-05
you can use **ls** to show a list of files and folders in the current directory. If the directory you want to go to is at the "top" of the file system you must do 

cd /tmp/whatever

if the folder you want to go to is a sub folder then its just

cd whatever

---

### Post by favad on 2006-09-07
Sir I&#8217;ll try to rephrase my question. I have understood what cd and ls do, but the thing is that my hda1 (Win XP partition) is mounted in tmp folder in my filesystem (which I think is also probably Home Folder). Now please tell me what to exactly do after opening Terminal to access my Win XP partition. Then I&#8217;ll be able to use those ls command to view files and folders and cd to open folders.

---

### Post by Dr. Nick on 2006-09-07
if it is in the /tmp then use

cd /tmp

tmp seems like a weird place for it to be mounted, /tmp gets erased on ecvery boot. just to confim the mount point I would use System - Administration - Disks and see what the "access path" says

---

### Post by fredBgl3 on 2006-09-07
Also a newcomer.  Have created the CD from the ISO & want to run Linux from the CD to see what it's all about.  Have done much reading & searching but still not clear on how to run it.  Do I have to alter the BIOS to boot from the CD or do I boot Windows (XP) first and then run Linux from the XP Start-Run command?  Apologies if you've seen the question a trillion times. fredB

---

### Post by favad on 2006-09-07
Dear fredb, simply turn on your computer, immediately press DEL or F8 key, until u get to setup, configure your BIOS to boot from CD, and off you go. In some cases you can simply boot from CD by pressing Control+F4 at system start, without requiring to enter your BIOS and manually boot from CD. So go give it a try.

favad

---

### Post by favad on 2006-09-08
It might be a very childish question, and prolly a stupid one aswell, but this little thing has become heck of a situation.

[B]favad@intel2400mhz:~$ cd /tmp/disks-conf-hda1
favad@intel2400mhz:/tmp/disks-conf-hda1$ ls
00007E00-E6C3E6C3       sqmdata04.sqm
Documents and Settings  sqmnoopt00.sqm
hiberfil.sys            sqmnoopt01.sqm
Inetpub                 sqmnoopt02.sqm
pagefile.sys            sqmnoopt03.sqm
Program Files           sqmnoopt04.sqm
RECYCLER                System Volume Information
sqmdata00.sqm           Volume{52C8E4FE-B853-42c1-9528-92978438BBF3}
sqmdata01.sqm           Volume{52C8E4FE-B853-42c1-9528-92978438BBF3}_Backup
sqmdata02.sqm           WINDOWS
sqmdata03.sqm
favad@intel2400mhz:/tmp/disks-conf-hda1$ cd Program Files
bash: cd: Program: No such file or directory[/B]

Unless I am able to open Program Files folder I cannot access anything. I can open cd WINDOWS but not this, I simply donna why?

favad

---

### Post by fredBgl3 on 2006-09-08
> **favad said:**
> Dear fredb, simply turn on your computer, immediately press DEL or F8 key, until u get to setup, configure your BIOS to boot from CD, and off you go. In some cases you can simply boot from CD by pressing Control+F4 at system start, without requiring to enter your BIOS and manually boot from CD. So go give it a try.

favad

Thanks for swift & helpful reply.  The CTRL+F4 doesn't work so will give the BIOS setting a go.  fredB

---

### Post by Dr. Nick on 2006-09-08
Ahhh, I totally forgot about something. I dont think Linussx likes spaces in the directory name. It only sees 'program" not "files" if I remember the solution is a "/ /" character to replace the spaces, 

look here
[http://www.mepis.org/node/7733](http://www.mepis.org/node/7733)

---

### Post by favad on 2006-09-10
Thank you I was able to access Program Files, was sort of looking for sol.exe in some bluddy directory. Besides when I write **cd P** and press TAB it automatically writes **cd Program\ Files/** and am able to open the folder. However if I want to open one of these
**My Music and My Pictures** I cannot, as writing **cd **M and pressing TAB only writes this **cd My\** and does not give the option to open any of the folders. Using // or \\ also has no effect. I'll be glad is could shed some light on that.

favad

---

### Post by bakert on 2006-09-10
> **favad said:**
> Thank you I was able to access Program Files, was sort of looking for sol.exe in some bluddy directory. Besides when I write **cd P** and press TAB it automatically writes **cd Program\ Files/** and am able to open the folder. However if I want to open one of these
**My Music and My Pictures** I cannot, as writing **cd **M and pressing TAB only writes this **cd My\** and does not give the option to open any of the folders. Using // or \\ also has no effect. I'll be glad is could shed some light on that.

favad

If you type the next letter or two and tab again all will be good.  Press tab twice to see a list of the alternatives.

So you can do this:

```

My, TAB, Mu, TAB

```

Does that get you what you want?

---

### Post by 3rdalbum on 2006-09-10
You can also enclose the paths in quotes:

```
cd "My Music"
```

This can be done for any command-line argument which has a space in it.

---

### Post by Ackowa on 2006-09-10
Are all the downloads of Ubuntu 6.06 live CD's?

---

### Post by Dr. Nick on 2006-09-10
> **Ackowa said:**
> Are all the downloads of Ubuntu 6.06 live CD's?


All downloads are bootable cd's 

The desktop cd will boot into a full useable gui which you can install from, or just test it without installing

the alternate install will boot directly into the text mode installer, no fully usuable gui like the desktop cd


either of the above 2 will ultimately end up at the same point after installing.

The server cd is like the alternate install cd, yet once installed their is not gui by default, only command line

---

