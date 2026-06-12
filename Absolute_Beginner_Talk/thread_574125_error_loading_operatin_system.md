---
title: "error loading operatin system"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-10-12
hi guys

after installing 7.04 i am unable to boot. getting the message - error loading operating system. looked at the other threads on the subject but was not sure what exactly to do.

system specs are Intel Pentium D 3 GHz, 1 GB Ram, 2 HDD.
First HDD is 40GB ( used to install linux)
second HDD is 160GB ( Win XP installed. One partition used to install Linux)

Thanx:guitar:

---

### Post by santy_kushwaha on 2007-10-12
i'm not sure what the problem bcoz u didn't specify where the error comes but i will suggest that reinstallation would help u

---

### Post by sandysandy on 2007-10-12
thanx.

i have already tried that 4 times already.
the only way i am able to boot is from live CD.
is any change required to any system file.

---

### Post by jgrabham on 2007-10-12
It could be that your Hard drive is not set to boot at all.  Check your BIOS

---

### Post by Sbarton on 2007-10-12
Sometimes this is a 'Bios' issue and can mean that a change in Bios access to hard drive, 
maybe from 'Auto' to 'Large'. Looking at your setup (dual boot with XP) it may be  a grub issue! However, look at the Bios first. If you do not have anything else on that drive perhaps a reinstall may be worthwhile. Hopefully other members may have solutions. Also in dual boot systems it is better to have XP(windows) installed first and linux second.
regards

---

### Post by sandysandy on 2007-10-12
thanx.

initially the first booting option was HDD and the message "error loading operating system" came.
i changed the booting option to CD ROM and thats how i am able to boot thru live CD.
But even with using live CD at time of booting - using option - boot thru first hard disk does not do the trick.

---

### Post by jgrabham on 2007-10-12
Is the HDD IDE?  If so, check your jumpers.

---

### Post by sandysandy on 2007-10-12
i am not sure of that.
but i can see the folders of both hdd after i boot thru live cd.
that means that the both hdd are accessible- i think.
is any booting command required to be added.
thanx

---

### Post by Sbarton on 2007-10-12
Did you check the Bios to see if LBA is enabled?
regards

---

### Post by sandysandy on 2007-10-12
what is LBA and how do i check that in BIOS.
thanx

---

### Post by Sbarton on 2007-10-12
sandysandy, have you entered the Bios before?
regards

---

### Post by jgrabham on 2007-10-12
> **sandysandy said:**
> what is LBA and how do i check that in BIOS.
thanx

Logical block addressing

Whats your motherboad model?  It could help us try to work out your BIOS.

---

### Post by Tlon on 2007-10-12
That's a message that Windows is giving you, not BIOS / GRUB / etc.  It's trying to load Windows but failing.  Something must have gone awry at some point during the partitioning process.

---

### Post by Sbarton on 2007-10-12
Tion is correct to say that often this is a 'windows' error, however it can still point to a Bios issue. Tion is also correct to say that something MAY have gone wrong at some point, and may suggest a reinstall is best.I have looked at your setup and see you have 2 HDD's, on one you have Linux (40gb) and the other XP & Linux(on a partition) I take it the linux (on the partition) was installed after XP is that correct?
regards

---

### Post by sandysandy on 2007-10-12
thats correct.
linux was installed after windows XP.

i have entered BIOS before. my motherboard is Gigabyte 945 series for intel core 2 duo.

also i am attaching the following:-
 
[COLOR="Red"]sudo fdisk -l[/COLOR]

[COLOR="Blue"]Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         294     2361523+  83  Linux
/dev/sda2            4559        4865     2465977+  82  Linux swap / Solaris
/dev/sda3   *        2362        4558    17647402+  83  Linux
/dev/sda4             295        2361    16603177+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       16581   107587305    f  W95 Ext'd (LBA)
/dev/sdb3   *       16582       19457    23101470   83  Linux
/dev/sdb5            3188        8286    40957686    7  HPFS/NTFS
/dev/sdb6            8287       13385    40957686    7  HPFS/NTFS
/dev/sdb7           13386       16451    24627613+   7  HPFS/NTFS
/dev/sdb8           16452       16581     1044193+  82  Linux swap / Solaris[/COLOR]
ubuntu@ubuntu:~$ 

thanx

---

### Post by sandysandy on 2007-10-12
> **Sbarton said:**
> Did you check the Bios to see if LBA is enabled?
regards
thanx

i enabled LBA just now in BIOS.
after rebooting with live CD, i selected the option of booting from first hdd (first hdd is 40GB loaded only with Linux)
**[COLOR="Red"]the following message came[/COLOR]**

booting from local disk
Isolinux: Disk error 01, AX=0201, drive 80
Boot failed: press a key to restart.

thereafter i rebooted with live CD as before.

does this info help in solving the problem.
thanx

---

### Post by Sbarton on 2007-10-12
sandysandy, Is your master drive (the 40gb) the one with ubuntu? What is your 2nd (slave drive)XP & what other OS?
regards

---

### Post by sandysandy on 2007-10-12
thats right

the master drive (40GB) is one with ubuntu.

the second drive (160GB) has Win XP, one partition also has ubuntu

thanx

---

### Post by Sbarton on 2007-10-12
ok! sandysandy, it seems you have 'Sata'not 'IDE'drives. regrettably the next suggestion is the only one I have left. Not being to familiar with 'sata' I was going to suggest you  disconnect the 40gb drive, make the XP & Linux drive the master drive and reinstall grub on that disc. If this does not work you will need the XP disc to restore the windows MBR.
Failing anyone else offering any solutions, maybe using another Ubuntu disc to reinstall on the 40gb drive may help, in case the original was corrupt. I do wish you good luck!
regards

---

### Post by sandysandy on 2007-10-12
Thanx

one more question. how does one reinstall grub.

regards

O:)

---

### Post by Duck2006 on 2007-10-12
> i enabled LBA just now in BIOS.

You may find that after changing the BOIS you will have to reinstall.
Because the geometry of the disk has been changed

---

### Post by sandysandy on 2007-10-12
thanx

i will try that now.

wish me luck

---

### Post by sandysandy on 2007-10-12
no luck.
the same message comes
**[COLOR="Blue"]Isolinux: Disk error 01, AX=0201, drive 80[/COLOR]**

---

### Post by Sbarton on 2007-10-13
sandysandy, I use Super Grub Disc to reinstall grub. You can download from this site:
[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml).
If you want to use this I suggest you have a good look at it first, before using it.
This site has some useful info on Super Grub Disc:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Also I use G-Parted to partition.Download from here if you need it.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Just maybe your Ubuntu install disc may be corrupted, perhaps installing from another Ubuntu disc may help.Sorry I cannot be more positive about a solution!
regards

---

### Post by SonicSteve on 2007-10-13
If you don't mind here are my 2cents.

Disconnect the 160g drive just as an experiment. Try to install Ubuntu on the 40G drive. See what happens. 

If even 1 of your drives are sata and your bios is anything like the ones I work with this is the way you bios may need to be configured. 

There is one setting in the bios for boot order and another setting for which hard drive to boot from. 
So you need to specify the master 40 as the boot drive and then set the boot order. Installing Ubuntu however without the 160G drive attached however will mean the grub.lst file will need to be manually edited so that it is aware of the slave 160G drive. Thats why installing Ubuntu with just the 40G drive attached is just a test.

It may well be that if you specify in the bios that the 40G drive is the primary boot drive that your problems go away, without any re-installation at all.

---

### Post by Sbarton on 2007-10-13
Good point from SonicSteve about having just the 40gb HDD installed. If the OS is OK! and grub is installed OK! that should boot.
regards

---

### Post by sandysandy on 2007-10-13
thanx

i reinstalled grub within ububtu 

when i boot from HDD the grub loader started to come up with variou options (some headway) for booting like

linux kernel...
Win XP etc

when i select any choice, " error booting.." comes up.
when booting from live Cd, when i choose " boot from first hard disk"
error message "Isolinux: Disk error 01, AX=0201, drive 80" comes.

(40 Gb is master and set for booting first  and 160Gb is slave)
thanx

---

### Post by alx.joom on 2007-10-13
I installed ubuntu 7.04 today for the first time and i experience the same problem.
The installation is at the same hard disc drive with windows xp ( I have 4 partitions in this drive. two for winxp , one for linux root and one for linux swap)
I also have two other hard disks (For windows)

Although at a start up i have the options to choose to boot between ubuntu and winxp
when choosing ubuntu i get "error loading"
and when i choose winxp i get "ntldr is missing".

I fixed the boot manager of windows again from winxp cd, so now i can only boot on windows.
Does everyone know if there is a way to install only the boot loader from the ubuntu live cd and not have to reinstall the entire ubuntu distribution again? ( i m sure there is a more elegant solution than reinstalling it..)

---

### Post by Duck2006 on 2007-10-13
Post #24 from sbarton gives it to you

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You can try to see if it boots with super grub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Duck2006 on 2007-10-13
Just having a quick look around and this person has the same problem as you

[http://ubuntuforums.org/showthread.php?t=574597](http://ubuntuforums.org/showthread.php?t=574597)

mite be worth keeping an eye on to.

---

### Post by Sbarton on 2007-10-13
> **Duck2006 said:**
> Just having a quick look around and this person has the same problem as you

[http://ubuntuforums.org/showthread.php?t=574597](http://ubuntuforums.org/showthread.php?t=574597)

mite be worth keeping an eye on to.

Hi Duck 2006, I think it is the same poster with 2 similar posts.

---

### Post by Sbarton on 2007-10-13
sandysandy, did you try  post #25 from 'sonicsteve'.?

---

### Post by sandysandy on 2007-10-13
thanx

will give it a try and get back.

---

### Post by sandysandy on 2007-10-13
> **SonicSteve said:**
> If you don't mind here are my 2cents.

Disconnect the 160g drive just as an experiment. Try to install Ubuntu on the 40G drive. See what happens. 

If even 1 of your drives are sata and your bios is anything like the ones I work with this is the way you bios may need to be configured. 

There is one setting in the bios for boot order and another setting for which hard drive to boot from. 
So you need to specify the master 40 as the boot drive and then set the boot order. Installing Ubuntu however without the 160G drive attached however will mean the grub.lst file will need to be manually edited so that it is aware of the slave 160G drive. Thats why installing Ubuntu with just the 40G drive attached is just a test.

It may well be that if you specify in the bios that the 40G drive is the primary boot drive that your problems go away, without any re-installation at all.

i disconnected the 160GB drive and reinstalled Ubuntu 7.04 on the 40 GB drive.
the booting priority was set to the 40 GB HDD.
while booting the message came" [COLOR="Blue"]Disk boot failure reinsert system disk and press enter"[/COLOR]

Will try and reinstall GRUB. maybe it will help

regards[COLOR="Red"][/COLOR]

---

### Post by Sbarton on 2007-10-13
*"Disk boot failure reinsert system disk and press enter".*.... 'very windows like'!!
Well, reinstalling grub, I do not think that is going to help you!!
You seem to have 2/3 different posts going on the same problem, so let's see if we can keep it to one!
Are you using the same Ubuntu disc to reinstall??
Try another Ubuntu disc!!
I take it the 40gb disc has one OS (Ubuntu)? which is not working! Try deleting all partitions until the HDD is clean.Reinstall Ubuntu using a different and working disc.
If this does not work you have other problems and I do not think it is Ubuntu that is the problem!
regards

---

### Post by sandysandy on 2007-10-13
i have been using the same ubuntu disk to reinstall (have only one disc, the iso image is on windows 160gb disc, dont know how i can cut another ubuntu cd as windows is not booting)
the 40 gb disc has only one OS which is ubuntu.

thanx

---

### Post by Sbarton on 2007-10-14
Sorry mate, I don't think I can help you any further. Good Luck, hope you find a solution, and if you do please post back with the solution.
regards

---

### Post by sandysandy on 2007-10-14
i have repaired the win XP  MBR without losing any data using the Win setup CD. The WIn XP is available. 
Kindly guide me to a good site where i can get step by step info on co-loading Ubuntu 7.04 on same HDD as Win XP for dual booting.

thanx for all the help and support.
will try loading ubuntu again after gaining more info on dual booting.

regards:guitar:

---

### Post by Sbarton on 2007-10-14
Glad you got XP up and running! This site is just one offering dual boot loading:
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

regards

---

### Post by SonicSteve on 2007-10-15
> **sandysandy said:**
> thanx

i reinstalled grub within ububtu 

when i boot from HDD the grub loader started to come up with variou options (some headway) for booting like

linux kernel...
Win XP etc

when i select any choice, " error booting.." comes up.
when booting from live Cd, when i choose " boot from first hard disk"
error message "Isolinux: Disk error 01, AX=0201, drive 80" comes.

(40 Gb is master and set for booting first  and 160Gb is slave)
thanx


OK so if you just have the 40gb installed can you install windows on it? forgive me for being a dog with a bone but you really have to find out if that 40gb drive is functioning properly. A bad sector in the wrong spot or a flaky controller (on the drive) can cause some very strange behaviour.
So far you know it doesn't like Linux for whatever reason. Try an experimental install of windows. We really need to know that hardware we are using is stable. Then look at bugs in the software.

I find that the most annoying errors occur when I have taken something for granted. In this case we might be assuming incorrectly that this drive is good.

---

### Post by sandysandy on 2007-10-17
ur right in saying that the 40GB hdd may be having problem. this may be because it is an older disc (IDE about 4 years old from my previous computer) and may not be compatible with my new computer BIOS. this i could make out as i was unable to boot even windows after loading it on th older 40 GB HDD.
however i could repair the windows MBR on the 160GB hdd and have not lost any data.
i will try loading ubuntu on one partition of the newer 160GB hdd as the older 40 Gb hdd is not seeming to be bootable with Intel Pentium D 2 core machine with either windows or linux, though the hdd is ok as far as storing data is concerned.

regards

---

### Post by ed_d on 2007-10-17
I had a similar issue. It seemed that grub had the wrong boot partition. I noticed after 3 install after 2nd burned cd.  Check the grub boot area to make sure you are booting to the partition you choose.

---

### Post by sandysandy on 2007-10-18
hi

how do you check that

regards

---

### Post by erundil on 2007-10-20
Hey sandysandy.

I am unsure whether I can help since I'm also new to Linux but I had installed a CLEAN copy of Windows XP and then did the default installation of Ubuntu 7.10 (using the guided resizing of partition option).

When I rebooted i got the "Error Loading Operating System" and I tried all sorts of things including fixmbr with no luck.

I don't know if my way is the 'right way' but what I did was use [Super Grub Disc]("http://supergrub.forjamari.linex.org/") and restored Grub from there.

Also take note of the respective entries for them (I forgot how to do that) but you will see something like hd0,0 or hd0,4 (basically hd being the ID assigned by Grub to the HD and the following number is the partition number as I understand it)

After when I booted up, it then gave me a list of options of OSes to boot from, but trying to boot from them gave me the error of cannot find the operating systems.

I booted into LiveCD and then edited the menu.lst and found that the references to the HDs were all wrong. Using the info I got from Super Grub, I edited all of the entries to correspond to the correct HD and partition and also deleted any 'map ' entries in the Windows XP section.

Rebooted and it all worked.

---

### Post by sandysandy on 2007-10-21
thanx

 i will try that out.

regards

---

### Post by sandysandy on 2007-11-05
> **erundil said:**
> Hey sandysandy.

I am unsure whether I can help since I'm also new to Linux but I had installed a CLEAN copy of Windows XP and then did the default installation of Ubuntu 7.10 (using the guided resizing of partition option).

When I rebooted i got the "Error Loading Operating System" and I tried all sorts of things including fixmbr with no luck.

I don't know if my way is the 'right way' but what I did was use [Super Grub Disc]("http://supergrub.forjamari.linex.org/") and restored Grub from there.

Also take note of the respective entries for them (I forgot how to do that) but you will see something like hd0,0 or hd0,4 (basically hd being the ID assigned by Grub to the HD and the following number is the partition number as I understand it)

After when I booted up, it then gave me a list of options of OSes to boot from, but trying to boot from them gave me the error of cannot find the operating systems.

I booted into LiveCD and then edited the menu.lst and found that the references to the HDs were all wrong. [COLOR="Red"]Using the info I got from Super Grub, I edited all of the entries to correspond to the correct HD [/COLOR]and partition and also deleted any 'map ' entries in the Windows XP section.

Rebooted and it all worked.

i was able to boot into ubuntu with Super Grub Disc though i am figuring out how to boot the hdd normally with ubuntu. 
how do you get the info from Super Grub to cross check the entries in menu.lst.

regards

---

