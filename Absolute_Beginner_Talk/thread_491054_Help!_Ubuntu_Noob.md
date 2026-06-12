---
title: "Help! Ubuntu Noob"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by poysama on 2007-07-03
I have installed Ubuntu last week but....

It so happened that I gave the whole partition of my slave disk to the installation.
Is Ubuntu like this? It will like eat up the given partition to it. I usually had four drives in My Computer on Windows (lets say C,D,F,G) and after installing Ubuntu F was gone and non usable for Windows.

Can someone teach me how to properly install Ubuntu? Like how much partition should I give it? Will it be usable for writing files in Ubuntu and Windows?

One more thing, when I was using Ubuntu, I was happy that my Internet is working correctly without configuring it. But then a few problems bothered me in using Ubuntu. I have a printer which is located in a USB port and Ubuntu can't find it. Also, I have downloaded some softwares but sad to say, I have discovered that I can't run files with .EXE extensions. I know Ubuntu has a way but I don't know what.

I wish someone could post links in troubleshooting Ubuntu to execute executable files, and make Windows games run too.

Thanks!

Ubuntu is Super!

By the way, what is Sabayon? Is it better than Ubuntu? Is it free?

---

### Post by Malibu Illusion on 2007-07-03
If you follow the default installation and do not read the part about partitioning, you'll end up inadvertently telling the installer to use the entire drive rather than partition it.  If you've overwritten data like this then you should start paying more attention when installing things.

To install Ubuntu how you want it, you need to go through the installation and choose the "manual" option when you come to the partitioning stage.  You then need to create at least two partitions:

**1: ** The root filesystem mount.
**2: ** A swap partition.

I recommend installing with three partitions, so you can mount your /home files on a separate area, so:

**3: ** The home filesystem mount.

The swap partition should be about twice the size of your RAM, typically.  So, let's say you have a 100GB harddrive and 1GB of RAM for example, you could have the following set up:

**Partition 1:** Type: EXT3, Size: 15GB, Mount point: /
**Partition 2:** Type: EXT3, Size: 83GB, Mount point: /home
**Partition 3:** Type: SWAP, Size: 2GB

---

### Post by nitro_n2o on 2007-07-03
Ubuntu did not eat the whole partition... it's just that you formatted the drive to ext3(maybe) and windows can't recognize this format 

To install programs go to System->Administration->Synaptic Package Manger and choose the application u like, or you can type this in the terminal sudo apt-get install <package name> where package name is the name of the program. Check out this for more information about installing programs [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/) 

the .EXE files are windows sort of files, in linux there is no such thing called file extension so live is easier :). 
However if you want to run windows program on  ILnux use Wine 
sudo apt-get install wine 

google wine for more information 

good luck :)

---

### Post by poysama on 2007-07-03
Hmmmm..Thanks...I've heard of wine and googled it already.
I think I can handle running programs in Linux

But I find it complicated in the installation/partition part...so many things I don't understand

Anyway, Malibu Illusion mentioned these:
1. root filesystem mount
2. swap partition
3. home filesystem mount

can anyone enlighten me on these?
what's EXT and SWAP anyway? filesystems? what do they do?

and one more thing!!!!!

I can see that linux has GRUB. when I install Ubuntu, does GRUB always have to stay on my primary master?
I have two 40GB HDD's and used the first drive(primary master) for windows. Can I install Linux on my slave? also GRUB?

---

### Post by L Campbell on 2007-07-03
> **poysama said:**
> I have installed Ubuntu last week but....

It so happened that I gave the whole partition of my slave disk to the installation.
Is Ubuntu like this? It will like eat up the given partition to it. I usually had four drives in My Computer on Windows (lets say C,D,F,G) and after installing Ubuntu F was gone and non usable for Windows.

Can someone teach me how to properly install Ubuntu? Like how much partition should I give it? Will it be usable for writing files in Ubuntu and Windows?

One more thing, when I was using Ubuntu, I was happy that my Internet is working correctly without configuring it. But then a few problems bothered me in using Ubuntu. I have a printer which is located in a USB port and Ubuntu can't find it. Also, I have downloaded some softwares but sad to say, I have discovered that I can't run files with .EXE extensions. I know Ubuntu has a way but I don't know what.

I wish someone could post links in troubleshooting Ubuntu to execute executable files, and make Windows games run too.

Thanks!

Ubuntu is Super!

By the way, what is Sabayon? Is it better than Ubuntu? Is it free?

You ask, "what is Sabayon?"

By entering ' sabayon ' in Google I got:-

[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

I know NOTHING more than that about it but I think you will be able to find answers to your questions there.

---

### Post by nitro_n2o on 2007-07-03
Simply: 
root: is where your all ur system resides in the hard disk 
swap: is something like RAM used by programs to save running information 
home: is where users' directories live, for example /home/root is where root home files

There are also other partitions: 
bin: binaries (similar to exe stuff in windows)
lib: libraries (similar to dll in windows)
etc: contains many things like services and program settings in some sense 

hope that helps

---

### Post by nitro_n2o on 2007-07-03
check out this it's more concrete and complete [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

### Post by sparks0548 on 2007-07-03
Wine has worked great for running windows based games.  If you care to spend a few bucks Code Weaver's Cross Over Linux ran games like World of Warcraft like a champ.  Granted it is based on Wine,  I found the interface and installation process a bit easier to use.

---

### Post by poysama on 2007-07-03
> **L Campbell said:**
> You ask, "what is Sabayon?"

By entering ' sabayon ' in Google I got:-

[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

I know NOTHING more than that about it but I think you will be able to find answers to your questions there.

Yup! Hehehe..Which is better?

---

### Post by poysama on 2007-07-03
Thanks n2o.....how much space should I use for the root? Can the GRUB be installed on the same directory for linux? Coz it takes too much problem if I uninstall Linux

---

### Post by Bothered on 2007-07-03
I'll start at the beginning, so don't feel patronised if I mention something obvious.

Your hard drive is divided into sections called partitions. Each partition can be thought of (logically, not physically) as a separate drive, i.e. place to store files. There are different types of partitions, depending on the type of file system used to format it. Windows uses NTFS type partitions (or FAT partitions on older systems), and accesses the partitions using drive letters, e.g. C, F, G etc. Linux typically uses ext3 or reiserfs partitions, and accesses the partitions by mounting them to directories, e.g. one partition might be mounted to /home (store all your documents, settings, etc.), one partition mounted to /boot (store boot files, including GRUB) and one partition mounted to / (everthing else, including programs). Windows cannot read ext3 or reiserfs partitions and so these partitions will not appear as drive letters in Windows, although there are utilities to overcome this.

Additionally, operating systems usually use swap memory in addition to physical memory. This is an area of your hard drive that is used as if it were additional memory. In Windows, swap memory is stored on the drive as a file (the page file). In linux, swap memory is (usually) allocated it's own partition on the drive, the swap partition.

If you are unhappy with your current hard drive partitioning, I recommend that the re-install ubuntu (making all necessary backups etc. first), and select custom partitioning, following the advice as above. If you simply want to be able to access the linux partitions within Windows, I recommend the utility [Ext2 IFS for Windows]("http://www.fs-driver.org/") (I don't use this myself, but have seen it recommended many times).

I have never used Sabayon, but I have seen it tested together with other distributions (Linux Format 94) where it was rated lower than ubuntu in every category.

---

### Post by nitro_n2o on 2007-07-03
Check out the ubuntu docs [https://help.ubuntu.com/7.04/installation-guide/hppa/partition-sizing.html](https://help.ubuntu.com/7.04/installation-guide/hppa/partition-sizing.html) this should help

---

### Post by Bothered on 2007-07-03
In response to your later post, by default GRUB is installed on your ubuntu root partition. However, it is possible that the ubuntu installer overwrote the Windows master boot record on your Windows drive (it did on my system). If it did, ubuntu can be uninstalled by following the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=481046#post2891590"), although point 3 doesn't apply to you as you have multiple hard drives.

---

### Post by poysama on 2007-07-03
Gee..Thanks a lot guys! I now understand most of the terminologies and stuff on linux. 

Thanks especially to Bothered for a detailed info. 
and everyone. I think Im ready to install LINUX

hehehe...anyway, I've heard of Linux since it was non-gui.
It uses like the MS-DOS where you type several commands such as dir, cd, etc.

I once accessed a part of Ubuntu that my OS became like that of an MS-DOS but it is linux
I don't know what commands to type so I just restarted my PC

Is there any training or tutorial lesson, documentation on using non-gui linux?
commands and everything?

---

### Post by coolen on 2007-07-04
> **poysama said:**
> I have installed Ubuntu last week but....

It so happened that I gave the whole partition of my slave disk to the installation.
Is Ubuntu like this? It will like eat up the given partition to it. I usually had four drives in My Computer on Windows (lets say C,D,F,G) and after installing Ubuntu F was gone and non usable for Windows.

Can someone teach me how to properly install Ubuntu? Like how much partition should I give it? Will it be usable for writing files in Ubuntu and Windows?

Ubuntu requires at least 2GB to install. If you're going to use it seriously, I'd give it at least ten. My root partition is 50GB (made to match Windows...guess which only has eight left).
In response to why Windows can't see your F drive, it's formatted to ext3 (the standard for Linux). Windows doesn't understand anything other than Microsoft filesystems, natively. You can try this link: [http://www.fs-driver.org/](http://www.fs-driver.org/)
It gives Windows the ability to mount ext filesystems. Be careful, though. Windows will not respect file permissions, or hidden files, and the partition will be mounted as ext2 rather than ext3 (they're basically the same, except ext3 uses a journal, protecting it from corruption in the event of sudden power loss or incorrect shutdown. You will not have this protection).

> **poysama said:**
> One more thing, when I was using Ubuntu, I was happy that my Internet is working correctly without configuring it. But then a few problems bothered me in using Ubuntu. I have a printer which is located in a USB port and Ubuntu can't find it. Also, I have downloaded some softwares but sad to say, I have discovered that I can't run files with .EXE extensions. I know Ubuntu has a way but I don't know what.

What type of printer is it? Many of the more popular ones have released open source drivers. My mum had a Canon printer that worked like a charm. Do some reading up on the subject.
As for .exe files, no, Linux cannot run them. These are win32 executables. In other words, they're compiled to run in 32-bit Windows. You can use Wine (available from the repos) to run some .exe files (many use it for games and such), but I don't know about drivers. I recall ndiswrapper provides Linux with the ability to use Windows drivers. Most use it for wireless cards. Ask a more advanced user if it's possible to use it for printers, too.

> **poysama said:**
> I wish someone could post links in troubleshooting Ubuntu to execute executable files, and make Windows games run too.

Wine, from the repos, can do some games. Cedega is similar in concept, but focused on games. I think you need to pay a small fee to use it, though. Don't expect great things, though. There's no reason Linux should run Windows executables, and the fact that it can, even with limited success, is a real treat.

> **poysama said:**
> By the way, what is Sabayon? Is it better than Ubuntu? Is it free?

Sabayon is another GNU/Linux distribution, famed for its early adoption of compositing technology (ie, all those annoying Beryl videos you see on YouTube).
I hear it's a very nice system, although I've not used it myself. Debian based too, if I recall correctly.

---

### Post by coolen on 2007-07-04
> **poysama said:**
> Gee..Thanks a lot guys! I now understand most of the terminologies and stuff on linux. 

Thanks especially to Bothered for a detailed info. 
and everyone. I think Im ready to install LINUX

hehehe...anyway, I've heard of Linux since it was non-gui.
It uses like the MS-DOS where you type several commands such as dir, cd, etc.

I once accessed a part of Ubuntu that my OS became like that of an MS-DOS but it is linux
I don't know what commands to type so I just restarted my PC

Is there any training or tutorial lesson, documentation on using non-gui linux?
commands and everything?

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

Should get you going. By the way, if you wind up at the console again, use Ctrl + Alt + F7 to get back to your GUI. Ctrl + Alt + F1-F6 to get back to a console session, if you're interested ;)

---

### Post by Bothered on 2007-07-04
Sabayon is Gentoo based, not Debian based.

---

### Post by coolen on 2007-07-04
> **Bothered said:**
> Sabayon is Gentoo based, not Debian based.

Ahh, thanks for that. My apologies on the misinformation.

---

### Post by poysama on 2007-07-05
hmm....a very informative to me. Thanks to coolen, and everyone.

I am a little familiar with Ubuntu now.

It's getting user friendly.

---

### Post by coolen on 2007-07-05
> **poysama said:**
> hmm....a very informative to me. Thanks to coolen, and everyone.

I am a little familiar with Ubuntu now.

It's getting user friendly.

Happy to be of help. This is the learning curve of Linux...even a user friendly distro has it, and unless you're a serious developer, it never really ends. As Ubuntu gets easier to use, your need for it to be will decrease greatly :P

---

### Post by Bothered on 2007-07-05
Nice guide coolen. I've bookmarked that one :)

---

