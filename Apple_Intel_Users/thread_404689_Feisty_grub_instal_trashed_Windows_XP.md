---
title: "Feisty grub instal trashed Windows XP"
date: 2007-04-08
forum: Apple Intel Users
---

### Post by henryjo on 2007-04-08
Hi,

Help!

Early this year I followed the triple boot howto ([https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)) and got OS X, Ubuntu 6.10, and Windows XP running. Very nice.

So I decided to upgrade to Feisty. Big mistake. The current versions of Feisty have a stuffed up X-server configuration script that stops the live CD and graphical install tools from working on the MacBook Pro laptops (well, mine anyway!)

I wanted to have grub as my boot loader so future upgrades would be easier. While stuffing around with getting Feisty to work, I installed grub onto my Windows partition. I then tired to remove it using the Windows XP Recovery Console. Ran fixmbr, fixboot for partition 4. The recovery console recognizes the Windows install, and all my files are still there, it just won't boot!! 

Stuff like disk error, hit any key to reboot, etc when you use reFIt, or alt-option or even grub to chainload partition 4 to boot. Here is my partition info:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     94781479  Mac OS X HFS+
 3       94781480    178929703  Basic Data
 4      178929704    234441607  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     94781479  af  Mac OS X HFS+
 3       94781480    178929703  83  Linux
 4 *    178929704    234441607  0c  FAT32 (LBA)

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 94781480:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 178929704:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 0c  FAT32 (LBA), active

I don't have a backup of the Windows install (big mistake!) and need it for my work. All the tools I've managed to find say there is nothing wrong with the Windows partition. Any ideas on how to get it to boot again?

Thanks
Henry

---

### Post by Herman on 2007-04-09
Hello henryjo,
You should be able to get it to boot with a special Windows XP boot floppy that you can make yourself, here's the web page with the official insrtuctions, [http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)
Note that you will be able to edit the boot.ini file in the floppy disk for whatever disk or paritition number you need from Linux,  because the floppy disk will be FAT32. [How to mount your floppy disk in Ubuntu]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_floppy_disk"). This floppy disk has NTLDR, boot,ini and NTDetect.com on it, so it can boot Windows almost no matter what.
Here's an even better web page with lots more instructions about all the things you can do to get Windows booting again,[ http://tinyempire.com/notes/ntldrismissing.htm]("http://tinyempire.com/notes/ntldrismissing.htm")

If you can follow the instructions from either of those sites you should have Windows booting in no time. I don't know why FIXBOOT didn't fix it already. If you installed Grub to your Windows bootsector, FIXBOOT is the right thing to do.

Regards, Herman :)

---

### Post by henryjo on 2007-04-09
Thanks Herman,

Thanks for the links you sent me. They have given me a few new ideas to try. It may be possible to get the sucker working via the Ubuntu partition. I'll try fixboot again. But I think it may have something to do with the rEFIt bootloader and GUID partitioning, which is an area I have very little experience with.

Many years ago I used to build dual boot boxes with Linux and Windows NT. Occasionally things would stuff up (fixboot etc won't work) and the quickest fix was a low level disk format, then re-install. I had an entire IT department at my disposal to provide support. Amazing how far Microsoft have progressed.

I am now a secondary school teacher who has a MacBook Pro. No floppies!! It is also running the GUID partitioning scheme.  Unfortunately I no longer do Windows support, and don't have stuff like Windows boot disks floating around. Being amazed at the fact that so many people would pay lots for OSes that are so flaky, I decided to no longer fork out money for operating systems. I'll try and get the school I work at to provide some support. But this is little out of their comfort zone.

Once again, thank you for your help!

Cheers

Henry

---

### Post by ronocdh on 2007-04-09
The few times I've made this mistake, using the WinXP SP2 CD and running a "fixboot" did indeed save the day. Sorry to hear it's not talking for you. =/ Given that you say your files are still intact, why not back them up now while you have them? You can mount the Windows drive in OS X or Ubuntu and then back it up any way you see fit! Do that now, before you tinker around more.

Also, sorry if I didn't glean this from your OP, but are you sure you've synchronized the boot sectors in rEFIt? To do this, start up the partitioning tool from the boot screen and it'll ask you for permission to sync, if indeed it needs done.

Good luck!

---

### Post by Herman on 2007-04-09
Hello again henryjo,
No floppy drive eh? If you have a good look through that last link I gave you, the author of that one has anticipated all kinds of problems that people might have and proposed alternative methods. He mentions how to make a CD that will do the same thing. I haven't tried that yet myself, I have tried the floppy disk method and it works great! That would get Windows to boot if you had a floppy drive but it wouldn't solve the problem. You would still need some Windows utility to do that.

I don't know anything about the rEFIt bootloader and GUID partitioning.

I do know that if you have the FAT32 filesystem in Windows, you can run a command from Ubuntu that will restore your Windows bootsector from its backup. I have tested that several times and it works well for me. This will actually fix the problem directly. Here is a link from my own website about how to do that from a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"). You can do the same from your Ubuntu operating system too, all you need to do is make sure the partition is unmounted, and place 'sudo' in front of the command. Here's the link,                    [When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup")  I have actually created the same problem you have deliberately and practiced recovering from it using this procedure.
You may need to replace the 'hda1' partition designation shown in those commands with one that is applicable to your partitioning arrangement. Is your Windows in partition 1 or 4? I'm not used to reading partition info in that format. I guess partition 4.
That might still work even if you have NTFS, but I'm reluctant to recommend it for NTFS because I have read about how delicate that filesystem is. Back up your files first if you are going to try it. Looking at the information you provided in your original post it looks like you have FAT32, so you're in luck! :)
That method should work as long as there's not something to do with the rEFIt bootloader and GUID partitioning I don't know about.

If you need to rescue or make a backup of your files first, this page will show you how to mount your Windows filesystem in Ubuntu giving you access to your files, [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").
That's half of the job, the other half is transferring the files to another media. If you're lucky enough to have a spare usb external hard drive handy that has room on it, that's very simple. Just plug it in and copy all the files over to it. Otherwise you can just copy the files to some CDs or DVDs. If there are a lot of files and you have another computer with hard disk space, you can easily network a Ubuntu computer to another Linux computer. Info on this page, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm").  You won't need a router as shown there. just a cat5 crossover cable will do, or two ethernet cables and a hub. If it's a Windows network you are connecting to, that's even simpler, just click 'Places'-->'Network Servers'--> (whatever icon). It's a while since I have connected to a Windows computer now, but I do remember it's very simple.
Even easier (if you have a Knoppix disk), here's my Knoppix Page's link to      [Knoppix File Rescues.]("http://users.bigpond.net.au/hermanzone/p20.html#Knoppix_File_Rescues") With Knoppix it's basically the same thing, but Knoppix does some of the things a little more automatically if you're feeling a bit lazy. :) Of course, Knoppix occupies the CD drive, so you won't be able to make a CD or DVD backup unless you have a lot of RAM to load Knoppix into RAM and eject the Knoppix disk. 
Puppy Linux does that automatically with only a moderate amount of RAM. That's another good way to rescue your files. Just download it from [Bigpond FIle Library]("http://files.bigpond.com/library/index.php?go=cat&id=32") for free.

I hope I'm being helpful, and good luck with it,
Regards, Herman :)

---

### Post by Caser on 2007-04-09
> **Herman said:**
> Hello henryjo,
You should be able to get it to boot with a special Windows XP boot floppy that you can make yourself, here's the web page with the official insrtuctions, [http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)
Note that you will be able to edit the boot.ini file in the floppy disk for whatever disk or paritition number you need from Linux,  because the floppy disk will be FAT32. [How to mount your floppy disk in Ubuntu]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_floppy_disk"). This floppy disk has NTLDR, boot,ini and NTDetect.com on it, so it can boot Windows almost no matter what.
Here's an even better web page with lots more instructions about all the things you can do to get Windows booting again,[ http://tinyempire.com/notes/ntldrismissing.htm]("http://tinyempire.com/notes/ntldrismissing.htm")

If you can follow the instructions from either of those sites you should have Windows booting in no time. I don't know why FIXBOOT didn't fix it already. If you installed Grub to your Windows bootsector, FIXBOOT is the right thing to do.

Regards, Herman :)

Mr.Herman,

thanks for the links ...they are very useful
my XP so far is good 
I&#8217;m still trying to dual boot feisty & winxp
I&#8217;m sure its in the grub ,
Thank again .

---

### Post by Herman on 2007-04-10
Thanks you for the favorable commant Caser. :) Normally [Super Grub Disk]("http://supergrub.forjamari.linex.org/") is the best all purpose boot-disk these days. These special Windows disks are only needed for special problems, but they are good to keep in your drawer or somewhere if you run Windows. They shouldn't be needed often though.
[Super Grub Disk]("http://supergrub.forjamari.linex.org/") would be more useful to the average dual booter, it has some other  good things for Windows users, plus lots of ways to help solve problems booting Linux as well. Nowadays people needn't be so scared of dual booting as they used to be. 
Are you having problems dual booting fiesty and XP? What seems to be the trouble, or what is the error messaage?
Regards, Herman :)

---

### Post by henryjo on 2007-04-11
Thanks so much Herman! And all the rest of the community who has responded. I was going to give up on Ubuntu and just restore my laptop to run XP and OSX, but now I am going to try and fix this!!

Big issues. Yes, I got /dev/disk0s4 partition to boot using the tools you pointed me to. However, because I had used the XP recovery console and read some crap on the Microsoft support site, I had at some stage started an "upgrade". Which meant the process was half way through. So the XP system booted in set up mode and needed the XP install disk to continue. Except that it seems that Apple laptops cannot eject a CD via hardware, only via software. So once I boot off a CD, it is stuck in the drive, unless it loads something to eject the disk. Also USB booting is not a simple matter either. See, no BIOS in an Apple box, it uses Open Firmware. That with the GUID stuff means a lot of the low level tools don't work correctly. At the moment, it is a totally random crap shoot whether or not the keyboard works when I boot with a Linix/DOS disk. So I spend my time  power cycling until I can get the muther to select a menu option!!

I don't care about the data (that's all on a remote server), just the fact it took me days to load all the licensed software I need to teach my classes.  Looks like MicroShaft has probably blown all that away. It may be possible to do a Automated System Restore. Unknown territory for me. Tell you what, next year (if I am still employed) I am pushing for Ubuntu Studio rather than proprietary packages. 

Ahh. Style versus substance. A very nice looking laptop the ol' MacBook Pro. But it is definitely not your average Intel box. I think I'll have to try and hassle Apple about this.

Once again, thanks for all the pointers. 

Cheers

Henry

---

### Post by henryjo on 2007-04-11
Hi Herman,

Super Grub and associated tools DO NOT boot on a CD-ROM in a MacBook Pro. I burnt the iso images and booted my Ubuntu ThinkPad with them, no worries! I'll have another go with the alternate boot Ubuntu CD, which does boot the Mac.

On the MacBook Pro, it just hangs on Grub - Loading Stage 2.

I'll keep the cd's in case I run across a boot problem on an "ordinary" PC!

Cheers

Henry

---

### Post by Herman on 2007-04-12
Thanks for the feedback henryjo, I'll make a note of that. Do you mean the CD itself doesn't boot? Or the CD boots but it can't boot any operating systems on the hard disk? 
Sorry for any inconvenience.

Regards, Herman :D

---

### Post by ronocdh on 2007-04-13
I'm bumping this because I'm interested in a response. Henryjo, what do you mean when you say the CDs didn't boot? Were you using rEFIt and selecting the CD icon? Did you hold down the C key during boot and do it that way?

I want to know! Please reply. =)

---

