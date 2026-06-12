---
title: "First Install Question"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by src2206 on 2007-07-21
Hello everyone

I am planning to make a fresh install of Ubuntu ver 7.0. Beofre I do that I would like to have the following doubts cleared:

1. Is it true that beryl now comes prepacked in Ubuntu Fiesty Fawn and during installation I do not install it separately?

2. It is very important that I have **NTFS Read-Write support**. I need to auto mount all my partitions and enable RW ability on those partitions by default.
How do I achieve this?

3. I have 2 HDDs. I intend to install the distro in the 2nd HDD. Is it possible not to install the GRUB of Ubuntu in the primary HDD so that the windows MBR remains intact? So I would like to install the Ubuntu boot loader in the first partitions of the 2nd HDD.

Please tell me whether it is possible and if yes, then I how do I do it.

4. Do I need to add the software sources manually or it will be preloaded while installing Ubuntu?

5. I would primarily use Ubuntu for general uses and mostly for compiling C and C++ programs [which I am going to start learning]. Do I need to install GCC separately?

I hope I have not asked too many questions and I hope some one from here will be kind enough to help me. :)

Please note that my experience with Linux is rather very limited so I would appreciate that if the reply is given in newbies terms as much as possible.

please help.

Thank you.

---

### Post by dptxp on 2007-07-21
> 1. Is it true that beryl now comes prepacked in Ubuntu Fiesty Fawn and during installation I do not install it separately?

COMPIZ is prepacked, disabled. No Beryl.

> 2. It is very important that I have **NTFS Read-Write support**. I need to auto mount all my partitions and enable RW ability on those partitions by default.
How do I achieve this?

You can do it. Shall post a bit later on how.

> 3. I have 2 HDDs. I intend to install the distro in the 2nd HDD. Is it possible not to install the GRUB of Ubuntu in the primary HDD so that the windows MBR remains intact? So I would like to install the Ubuntu boot loader in the first partitions of the 2nd HDD.

Can not say, let someone else reply on this.



> 4. Do I need to add the software sources manually or it will be preloaded while installing Ubuntu?

Many preloaded. Codecs and 10000+ packages using add/remove via net. Simple to add or remove

> 5. I would primarily use Ubuntu for general uses and mostly for compiling C and C++ programs [which I am going to start learning]. Do I need to install GCC separately?

YES

---

### Post by dougfractal on 2007-07-21
There are so many great guides for ubuntu here are some:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
[http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

It's a great os, have fun ;-)

---

### Post by src2206 on 2007-07-21
Thank you for your quick response.

Please also let me know how do I install the GCC module in Ubuntu!

What is the difference between Compiz and Beryl? Could you please enlighten me a little on this? Also please let me know how do I enable Compiz as it is disabled by default.

Thank you again.

PS: I tried to get the Ubuntu Book from the link in your sig, but it is giving me a 403 error [not permitted].

---

### Post by Mornedhel on 2007-07-21
apt-get install gcc as root or sudoing.

---

### Post by forestpixie on 2007-07-21
```
3. I have 2 HDDs. I intend to install the distro in the 2nd HDD. Is it possible not to install the GRUB of Ubuntu in the primary HDD so that the windows MBR remains intact? So I would like to install the Ubuntu boot loader in the first partitions of the 2nd HDD.

Please tell me whether it is possible and if yes, then I how do I do it.
```

I'm almost positively sure that there are other ways of doing this but this is what I would do. (mainly because I now use win very little)

I would think that this is possible - you would need to be able to access BIOS at start up and be able to change boot order so you could boot from whichever HDD you have a need to boot to.

If you are able to do that then you would need to unplug the HDD with Win on, then Ubuntu wouldn't know it was there.

Install Ubuntu to the HDD

Reconnect the HDD with windows 

Then change boot order in BIOS when you needed to.

---

### Post by Maxtorm on 2007-07-21
Re: NTFS mounting:
> **dptxp said:**
> You can do it. Shall post a bit later on how.
Absolute easiest way is to install Automatix ([www.getautomatix.com]("http://www.getautomatix.com")) and install the NTFS automounter.  "Manual" way is
```
sudo apt-get install ntfs-3g
```> **Mornedhel said:**
> apt-get install gcc as root or sudoing.
If you need gcc, chances are you'll need other build tools.  You might save yourself some time and effort later with
```
sudo apt-get install build-essential
```

---

### Post by dptxp on 2007-07-21
> **src2206 said:**
> Thank you for your quick response.

Please also let me know how do I install the GCC module in Ubuntu!

What is the difference between Compiz and Beryl? Could you please enlighten me a little on this? Also please let me know how do I enable Compiz as it is disabled by default.

Thank you again.

PS: I tried to get the Ubuntu Book from the link in your sig, but it is giving me a 403 error [not permitted].

Yes, I saw the 403 error today. Thanks, I shall remove the link in a day or two if error continues.
Compiz too is for desktop effects, I think Compiz and Beryl have joined hands now.

You enable by enabling desktop effects in SYSTEM>PREFERENCES or maybe SYSTEM>ADMINISTRATION menu. I have removed the menu, these are in Beta stage, do not always work, and slow down systems unless you got a good one ( 1 GB or more RAM).

Go to the PROGRAMMING SECTION for compilers etc., you will find better info.

---

### Post by src2206 on 2007-07-21
Thank you everyone for your great help.

So I have three options to enable NTFS RW capability in Ubuntu: 
1. NTFS config
2. Automatix
3. ntfs-3G

Now as you are far more experienced with any or all of these tools, please tell me which one is the least buggy and easiest to install and use. As I said my need is simple: **Auto mount NTFS partitions in the RW mode**.

@Maxtrom

After installing ntfs-3g as you pointed out, do not I need to configure it? Please be kind enough to point me to a guide suitable for a newbie like me.

@ [forestpixie]("http://ubuntuforums.org/member.php?u=288995")

Thank you for your response. Is it absolutely necessary to unplug the windows disc? That one is SATA HDD and the drive I intend to install Ubuntu is a PATA HDD. During installation, would not Ubuntu give me an option to choose the location of Boot Loader? BTW, **I can change the Boot sequence from BIOS**.


@[dptxp]("http://ubuntuforums.org/member.php?u=249750")

Thank you very much for your response. I have 1GB RAM, Intel C2D 4300 processor. :)



---

### Post by gn2 on 2007-07-21
> **src2206 said:**
> 
. Is it absolutely necessary to unplug the windows disc? That one is SATA HDD and the drive I intend to install Ubuntu is a PATA HDD. During installation, would not Ubuntu give me an option to choose the location of Boot Loader? BTW, **I can change the Boot sequence from BIOS**

The answer to this question is that the Live CD installer for older versions of Ubuntu did not give the option to select where to install GRUB, 
it just over-wrote the C: drive MBR, therefore some people (me included) used to advocate unplugging the windows drive during install.

With 7.04 this has changed, so that you can now select where to write GRUB during the installation process from a Live CD, so disconnecting the Windows drive is no longer necessary to keep it's MBR Grub free.

Because of this and as you can set the BIOS to boot from the Ubuntu PATA drive, leave the SATA Windows drive connected during the installation process.

As far as NTFS auto-mounting and write support, I can't see past the Automatix auto-mounter.

The official Ubuntu stance is that other methods are preferable, but if like me you want the minimum of fuss, Automatix can't be beaten.

If required Automatix has it's own support forums. 
Automatix has yet to cause me a single problem, but I'm not a "fiddler" and leave things alone mostly.

---

### Post by forestpixie on 2007-07-21
> **src2206 said:**
> 
@Maxtrom

After installing ntfs-3g as you pointed out, do not I need to configure it? Please be kind enough to point me to a guide suitable for a newbie like me.

@ [forestpixie]("http://ubuntuforums.org/member.php?u=288995")

Thank you for your response. Is it absolutely necessary to unplug the windows disc? That one is SATA HDD and the drive I intend to install Ubuntu is a PATA HDD. During installation, would not Ubuntu give me an option to choose the location of Boot Loader? BTW, **I can change the Boot sequence from BIOS**.


@[dptxp]("http://ubuntuforums.org/member.php?u=249750")

Thank you very much for your response. I have 1GB RAM, Intel C2D 4300 processor. :)

There you are - I knew there'd be a way  - must say I haven't seen an option as to where to install grub - but then again I wasn't looking for one :)

AS far as configuring ntfs-3g goes - it's one or two mouse clicks.

Good luck with the installation

---

### Post by src2206 on 2007-07-21
> I'm not a "fiddler" and leave things alone mostly me ditto. I prefer things in their default settings unless I am really compelled to change something.

Thank you very much gn2 for your reply.

So during the install of ver 7.04, which location of the PATA drive should I choose for GRUB Loader to install?

Regarding Autimatix, I found this in their homepage:

> [LIST]
[*] Automatix2 is a graphical interface (written in python and bash) for automating the installation of the most commonly requested applications in some Debian based distributions.[/LIST]
I could not find anything regarding auto mounting NTFS and giving  RW access! Did I miss something? Or while installing Automatix, the etc/fstab file gets edited automatically to mount NTFS drives in RW mode?
Thank you again.

---

### Post by src2206 on 2007-07-21
Thank you very much [forestpixie]("http://ubuntuforums.org/member.php?u=288995") :D

---

### Post by Maxtorm on 2007-07-21
> **src2206 said:**
> 
After installing ntfs-3g as you pointed out, do not I need to configure it? Please be kind enough to point me to a guide suitable for a newbie like me.

My preference would also be Automatix (and, of course, there are a ton of other goodies in Automatix including VMWare etc.).

However, if you're a sucker for punishment like I am, according to this post: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) , if you
```
sudo apt-get install ntfs-config
```
it will configure automatically.  Much more info is in that post.

---

### Post by Maxtorm on 2007-07-21
> **src2206 said:**
> Regarding Autimatix, I found this in their homepage:

I could not find anything regarding auto mounting NTFS and giving  RW access! Did I miss something? Or while installing Automatix, the etc/fstab file gets edited automatically to mount NTFS drives in RW mode?
Once you have installed Automatix, you'll be given an extensive list of add-on applications, drivers, etc. that you can choose to install.  In the "Miscellaneous" menu, you'll find "Automatix read/write NTFS and FAT32 Mounter".  Screenshot attached.

---

### Post by src2206 on 2007-07-21
Great Maxtorm, you have really cleared all my doubts. I am surely going for Automatix....no doubt about it now.

I shall also choose the 2nd HDD as the location to install the GRUB loader...and one small thing..do I need to make a separate partition in that disc for the GRUB Loader?

Thank you very much :D

---

### Post by Maxtorm on 2007-07-21
> **src2206 said:**
> ..do I need to make a separate partition in that disc for the GRUB Loader?
No, you don't.  GRUB installs in the master boot record, which is separate from the partition table.

---

### Post by src2206 on 2007-07-21
> **Maxtorm said:**
> No, you don't.  GRUB installs in the master boot record, which is separate from the partition table.

Yes I understand that but the MBR is at the beginning of C:\ drive in my SATA HDD, where I am not going to install GRUB. That is why I thought whether I need to create a new partition.:confused:

Do you think that about 8GB of space will be enough for Fiesty Fawn installation? I have separate 1.2GB SWAP partition.

Thank you again. :popcorn:

---

### Post by Maxtorm on 2007-07-21
> **src2206 said:**
> Yes I understand that but the MBR is at the beginning of C:\ drive in my SATA HDD, where I am not going to install GRUB. That is why I thought whether I need to create a new partition.:confused:

Do you think that about 8GB of space will be enough for Fiesty Fawn installation? I have separate 1.2GB SWAP partition.
I believe (and I would defer to one of the previous posters who clearly know more about this kind of thing than I do) that the two drives will be set up the same way, the only difference being that your first drive uses the Windows boot loader and the second drive uses GRUB.  Once you tell the machine to boot from the second drive, it's going to look for the second drive's MBR -- i.e. GRUB (which will be outside of the partition table).

8GB is loads of space to install Feisty.

---

### Post by src2206 on 2007-07-21
Thank you very much Maxtorm :D

Now I can venture in the unknown with a lot more confidence, for that thanks to you and other friends of mine here.

---

### Post by src2206 on 2007-08-18
Sorry folks for digging up this old thread,

but I was wondering whether it is possible to access the **NTFS partitions in both Read-Write mode** while using **Ubuntu in the Live CD mode**.

---

### Post by dougfractal on 2007-08-18
**ntfs-3g**

With the livecd's kernel-based ntfs driver, you'll only be able to get read-only access, so it is recommended to install the read-write ntfs-3g driver (you'll need a ubuntu 7.04 livecd to do this, though, the earlier versions don't have ntfs-3g in the repos):

sudo apt-get update
sudo apt-get install ntfs-3g

Then, assuming that your Windows drive is /dev/sda1 (adjust line accordingly, you can use sudo fdisk -l to find it out; see whichever one says HPFS/NTFS on the type line), mount the partition using ntfs-3g:

sudo ntfs-3g /dev/sda1 /media/windows

---

### Post by src2206 on 2007-08-18
Hello dougfractal

Thank you for your response. According to the previous advisers in the same thread I have decided to install Automatix after installing Ubuntu on my HDD.

Can the process that you have kindly described be used to access the NTFS drives in Read-Write mode while using **Ubuntu as a Live CD**? I have the latest **7.04 **version of the Ubuntu (Fiesty Fawn).

---

### Post by src2206 on 2007-08-18
I would also like to have another issue resolved. I hope you guys will help me as usual.

I have a old 6.06 CD of Ubuntu and one of my friend recently borrowed and installed it in his PC as a dual boot with Windows. Everything was fine untill he tried to install nVidia kernel drivers for Ubuntu. He uses nVidia MX4000 AGP card. After installation the X Window system refused to load/start.

Was it an issue with the old version and has it been resolved with the latest one? In that case my fried will also update the Ubuntu installation.

Thank you.

---

### Post by dougfractal on 2007-08-18
> Can the process that you have kindly described be used to access the NTFS drives in Read-Write mode while using Ubuntu as a Live CD? I have the latest 7.04 version of the Ubuntu

yes 
> sudo apt-get update
sudo apt-get install ntfs-3g

sudo ntfs-3g /dev/XXXX /media/windows


> 
I have a old 6.06 CD of Ubuntu 
I find old ubuntu disk may be useful if you have a troublesum motherboard. But Linux evolves so fast. 1 year is a very long time, with ubuntu really tring at ease of use, he's missing loads of  features.  
Also ubuntu is very "stepped" - it takes a snapshot of whats going on at that time, then makes a distro. And the only main way of getting the latest software is to **apt-get dist-upgrade** to the next snapshot. 

I'm not keen on Automatix, to me it's a kind of hack fix. and  defeats the purpose of apt.
It was useful in edgy, but you can get most things by adding the repos to the sources.list 

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

If you must use it use it sparingly.

---

### Post by src2206 on 2007-08-19
Thank you dougfractal for your reply. I hope that you won't mind me asking the reasons for your reservations about Automatix.

BTW, do you have any idea about the failure of nVidia module installation?

---

### Post by dougfractal on 2007-08-19
nVidia MX4000 AGP is a legacy card 

sudo apt-get install nvidia-glx-legacy
sudo dpkg-reconfigure xserver-xorg

**upgrade 6.06**
sudo apt-get upgrade
sudo apt-get dist-upgrade

> reasons for your reservations about Automatix
Automatix, to me it's a kind of hack fix. It was useful in edgy. But in feisty you can just add the repos.
One of the get things about apt is that it controls all your packages, updates them, keeps things in order.

I havn't look at automatix or wine lately but it may be useful there. But I wish the automatix team just built 3rd party deb packages like "Envy" rather than create there own manager.

---

### Post by philinux on 2007-08-19
GCC is already install with Feisty

---

### Post by Maxtorm on 2007-08-19
> **src2206 said:**
> Thank you dougfractal for your reply. I hope that you won't mind me asking the reasons for your reservations about Automatix.
You might also be interested in the article here: [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html) that details some of the security issues with Automatix.  That said, I still use it, but I think I'll bite the bullet and go back to apt-getting the required packages when I upgrade to Gutsy.

---

### Post by src2206 on 2007-08-25
Hello everyone :)

At last, yesterday night I installed Ubuntu form the CD kindly provided through ShipIt (Thank you Ubuntu and ShipIt :) )

I thank you all for the help that you have provided.

I have some issued with display and desktop effect for which I have started a new thread here: [http://ubuntuforums.org/showthread.php?p=3251671#post3251671]("http://ubuntuforums.org/newthread.php?do=newthread&f=73")

I hope to see all there.

I have installed Automatix and I am really impressed.

---

