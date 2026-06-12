---
title: "Apple computers &amp; Ubuntu"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-03-02
I was just talking to someone from Apple computers and they told me that Ubuntu would NOT run on their laptop computers !!!

Do they know what they are talking about ?

Thanks.

---

### Post by fusiachi on 2007-03-02
No, they don't.  

There are builds of Ubuntu for both their PPC and Intel-based notebooks.

---

### Post by wpshooter on 2007-03-02
That's what I thought, just wanted to make sure.

Thanks.

---

### Post by ubix on 2007-03-03
> I was just talking to someone from Apple computers and they told me that Ubuntu would NOT run on their laptop computers !!!

Do they know what they are talking about ?:lolflag: 

Indeed, they do know very well, what they are talking about, the question is do we (you) understand them? The trouble with Apple is their compliance with a disk organization schema, which is based on **GUID Partition Table (GPT)** rather than on _**Master Boot Record (MBR)** used with BIOS_.

GUID Partition Table (GPT) is a standard for the layout of the partition table on a physical hard disk. It is a part of the [COLOR="Blue"]Extensible Firmware Interface (EFI) standard proposed by Intel[/COLOR] as a replacement for the outdated PC BIOS. The GPT replaces the Master Boot Record (MBR) used with BIOS.

Therefor, there are two different architectures here to deal with, and **Linux** understands them both. Trouble is that GRUB and LILO are not perfectly aware of these two disk schemmas, and they do not handle "BIOS-less" **PowerPC** at all. However, Linux comuniti has addressed this issue long ago, and one can install Linux on PowerPC's too. There is an equivalent of BIOS-aware GRUB which we use on Intel platforms, for **PowerPC**s which is called [COLOR="Blue"]**yaboot**[/COLOR]. It is the Macintosh Open-Firmware loader.

Apple is trying to make it hard to put any Linux on their hardware, by exploiting the two OS Platforms and the two disk schemas, which gives them 4 different combinations for setups and installation instructions. Some of these are addressed here: [http://r[COLOR="Red"]**EFI**[/COLOR]t.sourceforge.net/myths]("http://rEFIt.sourceforge.net/myths"), **however, though they provide us with sufficient info to investigate this issue further, some of their facts are plainly wrong!**

So far it is possible to install Linux on all contemporary Apple hardware, and I believe it will continue to be so, in fact I believe things will get better, when GRUB and LILO loaders will be made aware of EFI disk layout. [COLOR="Blue"]Apple will have trouble preventing other OSes to run from their hardware, unless, they will intentionally modify requirements suggested by  the Extensible Firmware Interface (EFI) standards.[/COLOR] ;)  :biggrin: ):P

---

### Post by andou on 2007-03-03
> **ubix said:**
>  

Indeed, ....standards.



That's a really great post! If all questions were answered this well, the world would be a better place. Thanks ubix :D

---

### Post by wpshooter on 2007-03-04
> **ubix said:**
> :lolflag: 

Indeed, they do know very well, what they are talking about, the question is do we (you) understand them? The trouble with Apple is their compliance with a disk organization schema, which is based on **GUID Partition Table (GPT)** rather than on _**Master Boot Record (MBR)** used with BIOS_.

GUID Partition Table (GPT) is a standard for the layout of the partition table on a physical hard disk. It is a part of the [COLOR="Blue"]Extensible Firmware Interface (EFI) standard proposed by Intel[/COLOR] as a replacement for the outdated PC BIOS. The GPT replaces the Master Boot Record (MBR) used with BIOS.

Therefor, there are two different architectures here to deal with, and **Linux** understands them both. Trouble is that GRUB and LILO are not perfectly aware of these two disk schemmas, and they do not handle "BIOS-less" **PowerPC** at all. However, Linux comuniti has addressed this issue long ago, and one can install Linux on PowerPC's too. There is an equivalent of BIOS-aware GRUB which we use on Intel platforms, for **PowerPC**s which is called [COLOR="Blue"]**yaboot**[/COLOR]. It is the Macintosh Open-Firmware loader.

Apple is trying to make it hard to put any Linux on their hardware, by exploiting the two OS Platforms and the two disk schemas, which gives them 4 different combinations for setups and installation instructions. Some of these are addressed here: [http://r[COLOR="Red"]**EFI**[/COLOR]t.sourceforge.net/myths]("http://rEFIt.sourceforge.net/myths"), **however, though they provide us with sufficient info to investigate this issue further, some of their facts are plainly wrong!**

So far it is possible to install Linux on all contemporary Apple hardware, and I believe it will continue to be so, in fact I believe things will get better, when GRUB and LILO loaders will be made aware of EFI disk layout. [COLOR="Blue"]Apple will have trouble preventing other OSes to run from their hardware, unless, they will intentionally modify requirements suggested by  the Extensible Firmware Interface (EFI) standards.[/COLOR] ;)  :biggrin: ):P

Well, from what I understand that you are saying here, then Apple either does NOT know what they are talking about or they are not telling the true to people they are having telephone conversations with.  I am not saying which it is.

Thanks for your reply.

---

### Post by ubix on 2007-03-04
I do not think you can use these words, to describe what they at Apple are telling to the people over the phone. There is truth in what they say if you look at it from their point of view. After all, what is an Apple without the Apple (OSX)?  

First thing to be aware of is the fact that all my efforts to install Linux alongside Mac OS X failed, and based on that, I concluded the  solutions advertised on the net, whereby one can utilize Apple's beta **BootCamp** dual boot loader, to create two partitions, by shrinking the original **Mac OS X** partition,  hence creating  the second free partition for **Linux**, or even as some claim use the second partition for Linux, and possibly latter on tweak Mac's disk format schema to add the third for a **Microsoft OS**, and the fourth for your **Linux swap**, are either misleading, or just plainly wrong!

Contrary to what you may learn on the following web pages: [http://r[COLOR="blue"]**EFI**[/COLOR]t.sourceforge.net/myths]("http://rEFIt.sourceforge.net/myths"), _and this is not [COLOR="blue"]**Apple**[/COLOR], it is not true that, without some kind of undocumented tweaking, **Mac OS X** can be installed on disks setup for **MBR**  partition  schema on **i386 Mac Mini** hardware_! Namely, there is no way to change the original GPD (EFI) partition schema to the so called hybrid **MBR/EFI** without repartitioning and reformatting the entire disk, which destroys the factory installed **Mac OS X**.  After that Linux can be installed with as many partitions as  you want, the only limitation is the disk hardware limitation, which for SCSI disk is 16 partitions. However, **Mac OS X** CD will not install anymore, unless you revert the disk partition schema back the original factory setting, which neither **GRUB** nor **LILO** can handle.

---

### Post by patchkov on 2007-03-05
Is it true? Really you couldn't install Ubuntu (or any other linux) along side with Mac OS X? It means users are forced to whether use Linux or Mac? Weird... I would even say hard to believe.

Cheers

---

### Post by wpshooter on 2007-03-06
> **patchkov said:**
> Is it true? Really you couldn't install Ubuntu (or any other linux) along side with Mac OS X? It means users are forced to whether use Linux or Mac? Weird... I would even say hard to believe.

Cheers

Well, actually that would be fine with me.  Because if I am going to use a computer, I want just **ONE** O/S on it.  

If I wanted to run OS X or M/S, I would not be putting Ubuntu/Linux on the computer.

I am of the opinion that writers and users of O/Ss have a hard enough time getting just one O/S to run PROPERLY on a system, might less trying to get two or more to co-exist.  If you want the frustratation of trying to get two or more to run together, more power to you.

Thanks.

---

### Post by ubix on 2007-03-06
[COLOR="Blue"][SIZE="6"][CENTER]Ubuntu installs along MacOSX on  Mac  Mini after all[/CENTER][/SIZE][/COLOR]

> **patchkov said:**
> Is it true? Really you couldn't install Ubuntu ...From your post I sense a suspicious tone, in particular I do not think, that Apple folks are involved in intentionally setting up some obstacles. They are just happily exploiting the fact that open systems and the community are slow to respond in some areas, like graphic cards, and lately the newly emerging MBR/EFI Disk Partitioning schemes.

Though Linux is well equipped to work with both, LILO and GRUB are not. When I modified the Ubuntu installation script to disable bootloader, by commenting out the object **self.configure_bootloader()** somewhere near line 385, in the file **/usr/share/ubiquity/install.py**, installation completes. However without **grub** installed there is no way to boot the system.

I also installed **LILO**, and it also blows up. Lilo is more specific when identifying the problem, it clearly doesn't think that devices defined in **/etc/fstab** as **UUID=...** are not proper disk devices.

Grub on the other hand, when executed manually, and apparently also in the installation script (not shown when run in GUI), consistently blows up with the message:```
 /target/boot/grub/stage1 not read correctly
```.However if you do not insist on installing both MacOSX and Linux, and set the disk formatting table to MBR/EFI hybrid GRUB does not experience these problems anymore.

P.S. I found Ubuntu much better in all respects than Mac OS X on i386 Mac Mini, except for BlueTooth, which is not yet supported in Ubuntu on Macs, [COLOR="Blue"]however not to worry, also Apple's BlueTooth as well as USB mouse suck[/COLOR], [COLOR="Red"]moreover I had to pay almost $100 for Apple tech. support over phone, just to figure out they sold me their hardware that just doesn't work not even with their own macosx, and now I'm stuck with a total expense over $400 and crippled basic Mac's I/O[/COLOR], which finally, when I was asked to buy a third party **SteerMouse** to inadequately and far from satisfactory fix even the behavior of the USB mouse on Mac Mini, :confused: :mad:  I decided to replace the nicely wrapped ... with Ubuntu :)

[CENTER][COLOR="Red"][SIZE="6"]Dual boot works[/SIZE][/COLOR]
[/CENTER]

My latest discovery is that Ubuntu and Mac OS X can be both installed on Mini Mac after GPT and Mac OS X partitions, moreover you can install Ubuntu over as many partitions as you like. I installed it over eight partitions, so there are all together ten partitions on my Mini Mac GPT disk and everything works flawlesly. 

One should be using Debian's rEFIt and download it from [http://ftp.debian.org/debian/pool/main/r/refit/refit_0.7-3_i386.deb]("http://ftp.debian.org/debian/pool/main/r/refit/refit_0.7-3_i386.deb")  just prior installation into Ubuntu running of the Live CD just prior installation, start the installation to create required partitions and finally as described in [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook") install the downloaded refit_0.7-3_i386.deb and run the command ```
sudo gptsync /dev/sda && sudo sfdisk -c /dev/sda 3 83
```not before the installation window tells you it finished creating your Ubuntu partitions, but before GRUB is written to hard drive. You have plenty of time wait until installer says **"Copying files"**, which takes over 15 minutes. 

My mistake earlier was to try to use **rEFIt** CD, created from the **rEFIt-0.8.dmg** in MacOSX, which I downloaded from [http://r[COLOR="blue"]**EFI**[/COLOR]t.sourceforge.net]("http://rEFIt.sourceforge.net") after and before the installation. Clearly Debian's (-.deb) package is needed because Ubuntu's disk partitioning during installation process overrides the **GPT/MBR** and does not care to **resync** it. Apparently in Ubuntu 7.x this is  fixed, and the download from Debian will not be required during installation.

Sorry, folks I took you along on an unnecessary investigative ride :( However, look at the bright side, we finally have a very good news to celebrate rogether. It all works and will be even better in the future! :) :) :)

---

### Post by ubix on 2007-03-07
[CENTER][SIZE="6"][COLOR="Blue"]Dual boot on Mac Mini works[/COLOR][/SIZE][/CENTER]

I need to bump up this thread, because of the update above :)

---

### Post by stmiller on 2007-05-28
Linux is thriving on Macs, and has been for some time. You have been able to dual boot with Linux since the OS 9 days. Dual booting works same as dual booting on any other computer: make one partition for OS X and install there; the other partition for Ubuntu and install.

Check out the PPC or Apple Intel section of this forum.

---

