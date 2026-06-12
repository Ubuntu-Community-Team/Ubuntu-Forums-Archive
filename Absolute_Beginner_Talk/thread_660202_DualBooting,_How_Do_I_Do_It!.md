---
title: "DualBooting, How Do I Do It?!?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by 2Dum2Kno on 2008-01-06
Now i need some help, i recently downloaded the Ubuntu 7.10 Live CD and I would like to dual boot it to my computer!

I Own a:
```
| Acer Aspire 5570 (Laptop)
| 1GB Of Ram
| 160GB Hard Drive, Defaultly  Partitioned To Make It 2 Hard Drives at 70GB Each
| Intel Centrino Duo Processor
| Im Running On Windows Vista Home Edition (Pro)
```

So How Would i go about Dual Booting my laptop, so i can boot both operating systems on it, so it wont load Ubuntu All the time?

If So please let me know

_______________________________________________
2Dum2Kno
N00B At DualBooting:lolflag:

---

### Post by philinux on 2008-01-06
[http://vista.blorge.com/2007/11/03/how-to-dual-boot-vista-with-linux-adding-linux-on-vista-machine/](http://vista.blorge.com/2007/11/03/how-to-dual-boot-vista-with-linux-adding-linux-on-vista-machine/)

---

### Post by 2Dum2Kno on 2008-01-06
Thanks for the link but... GRUB is that included with Ubuntu?

---

### Post by Fraser from Scotland on 2008-01-06
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

that is a great guide, i used it to dual boot Ubuntu 7.10 and Windows XP. However, I dont know if that guide applys to Vista, I think Vista can be tricky to dual boot. Wait for some more replies to be on the safe side.

EDIT: Too slow :) lol

---

### Post by (((X))) on 2008-01-06
yes, Ubuntu wil install GRUB too.

---

### Post by 2Dum2Kno on 2008-01-06
> **(((X))) said:**
> yes, Ubuntu wil install GRUB too.

ok so the partition will automatically work and i wont have to do extra things

---

### Post by nnamdi on 2008-01-06
simply create a space for your Ubuntu OS then install it on that partition durin installation u should install a boot loader called grub that will comfortablin handle your windows and linux together


or 


u could try out vmware or virtual box

---

### Post by 2Dum2Kno on 2008-01-06
> **philinux said:**
> [http://vista.blorge.com/2007/11/03/how-to-dual-boot-vista-with-linux-adding-linux-on-vista-machine/](http://vista.blorge.com/2007/11/03/how-to-dual-boot-vista-with-linux-adding-linux-on-vista-machine/)
with this link it says to use Ubuntu 7.04 - wil it still work with 7.10


ALSO tell me this do i have to download grub to make it work? or is it included with ubunu?

______________________________
2Dum2Kno
Sorry For the Questions?:popcorn:

---

### Post by philinux on 2008-01-06
All above good advice. The real important thing is to use vista to resize you existing hard drive to make space for ubuntu.

7.1 should be no bother. Grub is installed along with the OS. Just back up any important stuff and make sure you have vista recovery disks.

---

### Post by 2Dum2Kno on 2008-01-06
how much space do i need for ubuntu?
like i said above, i have 2 harddrives at 70GB each

---

### Post by Joeb454 on 2008-01-06
You can get away with just using 15GB for Ubuntu...especially if you just want to try it out.

Although I would DEFINITELY recommened booting from the LiveCD first...to see if you're likely to have issues with anything (wireless etc.) And also, make sure that any space partitioned for Ubuntu is just empty space (not formatted to anything) Otherwise you'll have to do GRUB yourself.

If you follow that...then when you're running the installer, all you need to do is click "***use largest continuous free space***" and it should all work great :)

---

### Post by philinux on 2008-01-06
Just re-read, you've done the first bit and partition the hard drive. So install ubuntu into the spare partition. It will sort itself out and recognise your vista install. Just backup and ensure you've got recovery disks.

As mentioned try out the live cd first.

---

### Post by Fleece Flamingo on 2008-01-06
I dual booted with vista premium and I had no problems at all. I just installed gutsy and it auto-installed grub. I didn't have to do one little thing except for partitioning. Just clicked install and all is fine.

---

### Post by 2Dum2Kno on 2008-01-06
> **Joeb454 said:**
> You can get away with just using 15GB for Ubuntu...especially if you just want to try it out.

Although I would DEFINITELY recommened booting from the LiveCD first...to see if you're likely to have issues with anything (wireless etc.) And also, make sure that any space partitioned for Ubuntu is just empty space (not formatted to anything) Otherwise you'll have to do GRUB yourself.

If you follow that...then when you're running the installer, all you need to do is click "***use largest continuous free space***" and it should all work great :)


i have used the live d and love it but i want to use full version, would i be able to get away with 12GB on a partition?
if not how do  i make it biiger?

---

### Post by PeterJS on 2008-01-06
Yeah 12Gb should be fine. there's a thread about sizing over here:
[http://ubuntuforums.org/showthread.php?t=660259](http://ubuntuforums.org/showthread.php?t=660259)

---

### Post by 2Dum2Kno on 2008-01-06
> **PeterJS said:**
> Yeah 12Gb should be fine. there's a thread about sizing over here:
[http://ubuntuforums.org/showthread.php?t=660259](http://ubuntuforums.org/showthread.php?t=660259)

OK TYVm, im gonna install Ubuntu

---

### Post by Joeb454 on 2008-01-06
Post back when you're done so we know it's all ok :)

---

### Post by 2Dum2Kno on 2008-01-06
> **Joeb454 said:**
> Post back when you're done so we know it's all ok :)

ive got a problem....

im on Step 4/7 and ive come to a problem with selecting the harddrive im on manual mode and i cant select my partition :(

Halp me plz

it says no rot fyle system is selected

---

### Post by 2Dum2Kno on 2008-01-06
> **2Dum2Kno said:**
> ive got a problem....

im on Step 4/7 and ive come to a problem with selecting the harddrive im on manual mode and i cant select my partition :(

Halp me plz

it says no rot fyle system is selected

sorry i messed that pic up

---

### Post by timbounceback on 2008-01-06
click on the partition you are installing it on, click edit partition, then select mountpoint as "/". :) good luck

---

### Post by 2Dum2Kno on 2008-01-06
> **timbounceback said:**
> click on the partition you are installing it on, click edit partition, then select mountpoint as "/". :) good luck

ok, heres a screen of what it loks like, can figure out


sorry for asking so many questions

the only mount points i have are
/dos
/windows

---

### Post by Joeb454 on 2008-01-06
You can't install it to an NTFS file system...I'd recommend checking that there's absolutely nothing on that partition, or if there is, then make sure it's backed up.

Then use it as ext3 instead of NTFS

---

### Post by 2Dum2Kno on 2008-01-06
> **Joeb454 said:**
> You can't install it to an NTFS file system...I'd recommend checking that there's absolutely nothing on that partition, or if there is, then make sure it's backed up.

Then use it as ext3 instead of NTFS

it a blank partition, can i format it form ubuntu?

---

### Post by 2Dum2Kno on 2008-01-06
heres a screen

---

### Post by PeterJS on 2008-01-06
Looks good except for the mount point. If that's your primary partition it should be /

---

### Post by 2Dum2Kno on 2008-01-06
> **PeterJS said:**
> Looks good except for the mount point. If that's your primary partition it should be /

o now its letting me continue...
Help again

---

### Post by timbounceback on 2008-01-06
ok, create a new swap partition from some free space (about 1 or 2 gigs should be good), and make the mountpoint "swap".

Cheers,
Tim

---

### Post by PeterJS on 2008-01-06
> **2Dum2Kno said:**
> o now its letting me continue...
Help again

Depends how much RAM you have, swap space is used when your ram fills up, it's much slower but it lets your system keep functioning. If you've got 1 gig or more of RAM you shouldn't need swap unless you're planning on running 3d games or video editing. If you've got 2 gigs you'll probably be fine as long as you don't try to do both at once, and any more than that and it's kinda silly. You may need to go back a step and add swap space as needed.

---

### Post by 2Dum2Kno on 2008-01-06
ok, i dont need i plan to upgrade my ram anyways

---

### Post by timbounceback on 2008-01-06
you can do it from ubuntu, just resize an existing one, then create a new one with the type swap and the mountpoint swap.

---

### Post by 2Dum2Kno on 2008-01-06
53%

---

### Post by timbounceback on 2008-01-06
when it's done be sure to check that everything works correctly, and, if so, mark the thread as solved. if not, report back :-)

---

### Post by 2Dum2Kno on 2008-01-06
ok i will

---

### Post by nnamdi on 2008-01-06
yeah the 70gig is enough just have 
a partition for /
then another partition for /home
the a swap partition which is normally twice the size of your ram

---

### Post by 2Dum2Kno on 2008-01-06
Emergency Emergency Help Help

---

### Post by 2Dum2Kno on 2008-01-06
Help Please, I Dont Know What To Do?!?!?!?!?




](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)]

---

### Post by PeterJS on 2008-01-06
That is indeed a fatal problem, the boot loader is kind of important. Can't think of any reasons off the top of my head why grub wouldn't install, but that's what google is for. Research time!

---

### Post by 2Dum2Kno on 2008-01-06
> **PeterJS said:**
> That is indeed a fatal problem, the boot loader is kind of important. Can't think of any reasons off the top of my head why grub wouldn't install, but that's what google is for. Research time!

OK REPORT BACK TO ME, IM A N00B TO UBUNTU AND GRUB
should i finish installing?

---

### Post by 2Dum2Kno on 2008-01-06
ok now im going crazy, its not working 

HELP HELP

---

### Post by philinux on 2008-01-06
Does vista still boot ok?

---

### Post by 2Dum2Kno on 2008-01-06
havent tried, but i have no bootloader and the guy i was talking to over msn said dont reboot until resoved

---

### Post by 2Dum2Kno on 2008-01-06
im starting to think that nonoe has an solution!

---

### Post by timbounceback on 2008-01-06
Don't get discouraged - smilar kind of things have happened to me a few times. Try downloading and burning a copy of super grub disk, or install grub manually from ubuntu using the grub-install command, or, lastly, simply reinstall. Good luck!

Tim

---

### Post by philinux on 2008-01-06
Ok dont panic. The worst case is that the MBR (main boot record) has been overwriten. This means vista cant boot either but your vista install is intact as are all your files on the vista partion.

it could be that grub (grand universal boot loader) failed to install also. 

You have the live cd which will boot and give you internet access. No harm rebooting to see what gives.

As long as you have the vista boot disk you can use the vista recovery option to fix the mbr by using fixmbr. This will remove grub, if it got installed at all.

---

### Post by PeterJS on 2008-01-06
Sorry about the confusion, I just didn't want you to reboot right that second and to instead try to install grub from the liveCD didn't mean to give the wrong impression.

---

### Post by 2Dum2Kno on 2008-01-06
> **philinux said:**
> Ok dont panic. The worst case is that the MBR (main boot record) has been overwriten. This means vista cant boot either but your vista install is intact as are all your files on the vista partion.

it could be that grub (grand universal boot loader) failed to install also. 

You have the live cd which will boot and give you internet access. No harm rebooting to see what gives.

As long as you have the vista boot disk you can use the vista recovery option to fix the mbr by using fixmbr. This will remove grub, if it got installed at all.

im not giving up, im gonna reboot and see what happens, if i cant get it to work ill load super grub disk

---

### Post by 2Dum2Kno on 2008-01-06
> **2Dum2Kno said:**
> im not giving up, im gonna reboot and see what happens, if i cant get it to work ill load super grub disk


ok im back!!

it didnt load GRUB, but i got ino vista not ubuntu :(

so im gona download the .S.G.D.
and see what hapens, do i have to load it in ubuntu?

---

### Post by 2Dum2Kno on 2008-01-06
problem alert 2

with version of super grub do i download?
USB KEY
ISO IMAGE

---

### Post by philinux on 2008-01-06
I'd use the iso and burn the image. Then you just boot the cd. by the way i've never used this so someone else may guide you on this,.

---

### Post by 2Dum2Kno on 2008-01-06
i think im gonna reinstall the OS

---

### Post by 2Dum2Kno on 2008-01-06
ok what do i do with the disk?

---

### Post by 2Dum2Kno on 2008-01-06
allright im gonna reinstall, im officaly fudtrated!

---

### Post by 2Dum2Kno on 2008-01-06
now reinstalling, my boot loader should be (hd0) right?

---

### Post by timbounceback on 2008-01-07
yes, hd0 should be where you want to install it.

---

### Post by 2Dum2Kno on 2008-01-07
> **timbounceback said:**
> yes, hd0 should be where you want to install it.

oh well i think i almost have it ill know soon!

---

### Post by Joeb454 on 2008-01-08
Have you managed to get the full system installed yet? Bootloader included :)

---

### Post by 2Dum2Kno on 2008-01-08
i think Acer hates me, the dualbooter wont install from the disc, so im trying FREEBSD
and im having a bit of luck just gotta fix this part of the code:

```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries

title Ubuntu
find --set-root /boot/vmlinuz-2.6.17-10-generic
kernel /boot/vmlinuz-2.6.17-10-generic ro root=/dev/sda5
initrd /boot/initrd.img-2.6.17-10-generic
```

thats the code but heres my problem:
```

find --set-root /boot/vmlinuz-2.6.17-10-generic

```

can you help, possibly put the code together for me?

---

### Post by Joeb454 on 2008-01-08
Did you try the super grub disc?

---

### Post by timbounceback on 2008-01-08
Yeah, Super Grub Disc can solve pretty much any boot problem you're having. I'd try that first :-).

---

### Post by 2Dum2Kno on 2008-01-08
yes i have and it failed :(
it said linux couldnt be found

maybe i should do a live cast of me doing an install...
and see if you guys can halp me

---

### Post by PeterJS on 2008-01-08
Did you ever follow up on the BIOS MBR write protection?

---

### Post by 4partee on 2008-01-09
> **philinux said:**
> [http://vista.blorge.com/2007/11/03/how-to-dual-boot-vista-with-linux-adding-linux-on-vista-machine/](http://vista.blorge.com/2007/11/03/how-to-dual-boot-vista-with-linux-adding-linux-on-vista-machine/)

The very first step is a problem for me, namely:

Go to Disk Management - right-click “My Computer”, Manage, Disk Management.

There is no "My Computer" anywhere that I can find.  This is on a Compaq F572US lappy bought new with Vista Home Premium.

John

---

### Post by PeterJS on 2008-01-09
> **4partee said:**
> The very first step is a problem for me, namely:

Go to Disk Management - right-click “My Computer”, Manage, Disk Management.

There is no "My Computer" anywhere that I can find.  This is on a Compaq F572US lappy bought new with Vista Home Premium.

John

Should be right on the desktop somewhere, also I thin in Vista they shortened it to just Computer.

---

### Post by 2Dum2Kno on 2008-01-21
JTLYK i gave up and i will continue to use it from disk

---

