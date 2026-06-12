---
title: "CD/DVD RW problem"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Mike1971 on 2007-04-05
Hi,

I'm new to Ubuntu so I'm not sure how to fix this problem. I have a CD DVD RW drive that reads CD's but not DVD's it says the disk is blank and asks if I want to make a DVD. Problem is the disk is not blank, it has all my pictures from my digital camera on it (JPEG I think!). I thought maybe the DVD disc was damaged so I put a movie instead but it say's the same thing DVD is blank. All works well under XP. Drive is fairly new. Maybe burned about 10 DVD's with it. Any Idea's would be greatly appreciated.

Mike

---

### Post by Kobalt on 2007-04-05
What do you burn your disks with under Windows ? I know of a few problems similar to your using the built-in CD/DVD burning feature of windows explorer... and unfortunately I never found a way to access data on these disks from something else than windows.

---

### Post by antoz on 2007-04-05
**Kobalt** I like your Avatar, Tintin et Milou ca me rapelle ma jeunesse.A

---

### Post by Kobalt on 2007-04-05
Thank you antoz! 
I do believe Tintin would support Ubuntu ;)

---

### Post by dannyboy79 on 2007-04-05
what does your 
dmesg | grep DVD

output state? I found the below on cdfreaks, have you tried to manually umount it and then remount and see  if it works than?

Posts: 6  DVD read problem (automount) 

--------------------------------------------------------------------------------

I have a NEC 4551A and some problems with certain dvds, even if they were burned with low speed.
I thought it was linux fault, so I upgraded default openSuSe kernel to 2.6.20, threw out unnecessary stuff and compiled just what I needed (I also unchecked generic IDE drivers from it).

But still automount didn't work since dvdrom is reporting inserted dvds as bad:

Quote:
Mar 8 22:36:10 linux kernel: hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Mar 8 22:36:10 linux kernel: hdc: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
Mar 8 22:36:10 linux kernel: ide: failed opcode was: unknown
Mar 8 22:36:10 linux kernel: ATAPI device hdc:
Mar 8 22:36:10 linux kernel: Error: Medium error -- (Sense key=0x03)
Mar 8 22:36:10 linux kernel: (reserved error code) -- (asc=0x02, ascq=0x00)
Mar 8 22:36:10 linux kernel: The failed "Read 10" packet command was:
Mar 8 22:36:10 linux kernel: "28 00 00 00 00 10 00 00 02 00 00 00 00 00 00 00 "
Mar 8 22:36:10 linux kernel: end_request: I/O error, dev hdc, sector 64
Mar 8 22:36:10 linux kernel: Buffer I/O error on device hdc, logical block 8  



But they are readable if I mount them manually:

Quote:
sudo mount /dev/hdc /mnt  



So it is clearly not a linux problem, it is automount precaution to void mounting when bad media is detected to possibly avoid dvdrom deadlocks or something (like when it is trying to read dvd for long time and you cannot eject media).

I was busting my head a loooooooong time with this and today I spontaneously discovered something. I decided to take a look at this problem again, so I reached to so called "faulty dvds" and started to test them. But now they were working. Every single one of them was working!
However copying was slower than declared dvdrom speed, it was about 4x. And then I remembered that I previously burned a dvd with 4x speed - so I thought that my dvdrom somehow got stuck on this read speed as well. To be sure I did a reboot and voila - dvds were not being automounted again.
I cannot force nec dvdrom to read dvds with lower speed, since it will completely ignore this:

Quote:
hdparm -E X /dev/hda  


and so I cannot do further tests. I tried again by burning another dvd with lower speed, but it didn't got stuck with it.
I tested same dvds on another drive, a liteon sohw812s and it doesn't have this problems. Also one of my friend owning a nec 3xxx series called me last time that has some problems with some dvds and when I checked dmesg I saw it was the same problem as mine.

I think this problem occurs only on multisession discs, when you insert them you can hear a shor buzz after spin-up (like the lens is being moved all the way).

---

### Post by Mike1971 on 2007-04-05
> **Kobalt said:**
> What do you burn your disks with under Windows ? I know of a few problems similar to your using the built-in CD/DVD burning feature of windows explorer... and unfortunately I never found a way to access data on these disks from something else than windows.

I burned those dvds with Nero.

---

### Post by dannyboy79 on 2007-04-05
exactly what command in nero? you didn't chose udf did you? you probably just did a data dvd correct?

---

### Post by Mike1971 on 2007-04-05
For the movie it was an iso image and for the pictures it was a data dvd

---

### Post by dannyboy79 on 2007-04-05
> **Mike1971 said:**
> For the movie it was an iso image and for the pictures it was a data dvd
is there any reason why you haven't responded regarding all the suggestions I gave?

---

### Post by Mike1971 on 2007-04-05
> **dannyboy79 said:**
> is there any reason why you haven't responded regarding all the suggestions I gave?

Yup, the reason is I'm at work... I'll try them tonight and let you know the results.

---

### Post by dannyboy79 on 2007-04-05
oh, you don't run a ssh server? cause im at work also, he he he.

---

### Post by Mike1971 on 2007-04-05
From what I've been reading it seems that a lot of people can't read cd's that were made under windows. I'll try and make a dvd in ubuntu to see if 1 I can create one and 2nd that it will be mountable and readable. Funny thing is it is my second installation in 2 days and in the first one it was readable for a while but I seemed to get conflics between me cd rw and my cd/dvd rw so I decided to do a complete reinstall with only one optical drive. I just hope my dvd with pictures didn't get damaged in the process because it was my only copy!

---

### Post by dannyboy79 on 2007-04-05
if you mount a dvd or cd with this in your fstab (/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0) you should be able to read any dvd or cd as I can. i own an Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive I just bought for $39.99 and it works great!! I did also have trouble with my old i/o blah blah generic dvd burner being able to burn dvd's (it could read them though) so I bought this NEW one instead as I couldn't troubleshoot it anymore. No problems burning or reading! 

Disc's get burned based on a standard and if the dvd-rom has it's firmware flashed with a recent firmware than you should be fine. Are you using cable select or master/slave? is it plugged into ide0 or ide1? or is it a sata dvd-rom? if it's sata, what controller is it?

lspci -v | grep SATA

---

### Post by Mike1971 on 2007-04-05
> **dannyboy79 said:**
> if you mount a dvd or cd with this in your fstab (/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0) you should be able to read any dvd or cd as I can. i own an Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive I just bought for $39.99 and it works great!! I did also have trouble with my old i/o blah blah generic dvd burner being able to burn dvd's (it could read them though) so I bought this NEW one instead as I couldn't troubleshoot it anymore. No problems burning or reading! 

Disc's get burned based on a standard and if the dvd-rom has it's firmware flashed with a recent firmware than you should be fine. Are you using cable select or master/slave? is it plugged into ide0 or ide1? or is it a sata dvd-rom? if it's sata, what controller is it?

lspci -v | grep SATA

Yeah my drive is an LG that I got for about 39$ as well and it is (from bios info) ATA66. It is set as slave on IDE0 (with hard drive) Bios recognizes it no problem as well. It  looks like it just doesn't recognize the files on the dvd. It sees a dvd, wants to make a dvd but cannot see that there is something on the DVD. Once I put the dvd in the light turns on and you can hear it spinning then nothing happens for about a minute or two then it say's you put in a blank disk, do you want to make a DVD? I think I'm going to reinstall XP  (not permanently!!) as dual boot and make sure nothing is busted on my drive. I want to get that assumption out of the way to make sure I'm not wasting my time on a busted drive.

---

### Post by dannyboy79 on 2007-04-05
you could try out virtualbox ([http://www.virtualbox.org/wiki/Downloads)](http://www.virtualbox.org/wiki/Downloads)), forget about dual-booting, when you do that you have to wait forever and shutdown, why not just run them side by side!! I have run ubuntu in windows xp pro using qemu with kqemu and it was almost just as fast as normal. if it was any slower, I might just do a dual boot but not having to shutdown the machine is WAY better! plus, no repartitioning etc etc. if you have dma on using ubuntu, than I would try to disable it and see if that helps. I have read more than once that dma on in linux can make some drives act very weird.

sudo hdparm -d /dev/hda

will tell you if you have dma set. replace hda with your device! then if that helps, then you need to make sure it's disabled at bootup, this is done with the /etc/hdparm.conf, there is a perfect exampe in there, just copy it, and then UNCOMMENT IT and change it from dma = on to dma = off. hopefully that fixes it. you could also get a bunch of info on the drive by issuing

sudo hdparm -I /dev/hda

good luck. see don't you wish you had a ssh server going, you could be doing all this while we talk from the comfort of your chair at work. getting paid to troublshoot your home computer problem!! he he he he

---

### Post by Mike1971 on 2007-04-05
good luck. see don't you wish you had a ssh server going, you could be doing all this while we talk from the comfort of your chair at work. getting paid to troublshoot your home computer problem!! he he he he

After I resolve my issue with my DVD, you'll have to explain to me how to get a ssh server going!

---

### Post by dannyboy79 on 2007-04-05
not a problem!!! it's awesome and probably one of the easiest things to set up! making it secure is just a tiny bit of work but nothing you can't handle.

---

### Post by Mike1971 on 2007-04-06
ok here's what happened last night:

I decided to try dreamlinux MM 2.2 to see if I would get better results with my dvd. result is no because the damn thing screwed up my boot sector. now every time I try to install Ubuntu, I get a disk boot failure. Reinstalled windows xp and this fixed my boot sector. Tried to read the dvd disks that were giving me a problem and all of them have unreadable LBA sectors. Thing is before I had my problems on ubuntu all my disks were ok, now they're no good anymore. Used nero to try and copy the dvd that had about a years worth of pictures and it worked partially. The dvd had about 80 lba sectors that were unreadable and lost about 90% of my pictures. Now need to find a place in town specializing in data recovery to see if they will have better luck. 

Now for the good stuff... I tried to reinstall ubuntu as dual boot but when I rebooted my computer after install I get a disk boot failure again. So I decided to repartition the hard drive in ubuntu install and install ubuntu as the only OS but when I reboot I get disk boot failure. I don't get it, with windows it works but since dreamlinux, I can't install ubuntu without getting a failure. Now I need help on how to fix this issue. Secondly, I'd like to know if anyone has any insight on what could of happened to the dvd's when I tried to mount them in ubuntu. 

God, it makes me wish I stayed with XP in the first place.

---

### Post by Mike1971 on 2007-04-06
forgot to mention, when I installed ubuntu the first time, I had 2 optical drives on IDE1 cd rw as master and cd/dvd rw as slave. I read somewhere that ubuntu doesn't like 2 optical drives on the same channel??

---

### Post by Mike1971 on 2007-04-06
help!!

---

### Post by dannyboy79 on 2007-04-06
well I am sorry to hear about the dvd disaster but if the disc wasn't a multi-session disc than there is no way that any OS would be able to screw it up as it gets "closed". here is a good article on bad burns ([http://www.infopackets.com/channels/en/windows/gazette/2005/20051103_recover_data_from_a_bad_burn.htm](http://www.infopackets.com/channels/en/windows/gazette/2005/20051103_recover_data_from_a_bad_burn.htm)) now I know you said that the disc was "ok" before but I just find this very hard to believe that somehow simply trying to read the disc could damage it, unless you did leave it open as a multi-session burn but I still find it hard to believe. have you tried to use dd_rescue on the dvd. this will basically copy bit by bit from the dvd and save it into an image. than you just mount that image and see the contents and then save the files out of the image and hopefully this will bet you back most of your pics. ddrescue works better than dd because dd often fails when bad sectors are hit, but ddrescure will just keep going. dd_rescue is in the repo's I believe but it's named 
or you could try this freeware called: ADRC Data Recovery Tools v1.0. i found it here: [http://www.winappslist.com/utilities/data_recovery.htm](http://www.winappslist.com/utilities/data_recovery.htm). 
here's another link with some suggestions for recovering the pics: [http://ask.metafilter.com/43343/Can-I-recover-data-pictures-from-a-bad-DVDR](http://ask.metafilter.com/43343/Can-I-recover-data-pictures-from-a-bad-DVDR)


next issue: i am not sure when the error is occuring? is the bios saying boot failure? you are booting the live cd installer right? or did you try the alternate install cd? if those aren't working. try to boot using the systemrescuecd here: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
it's basically a compilation of tons of very useful apps to help you recover a system. it's got gparted, partimage, File systems tools (e2fsprogs, reiserfsprogs, reiser4progs, xfsprogs, jfsutils, ntfsprogs, dosfstools): they allow you to format, resize, and debug an existing partition of your hard disk, it even has Ntfs3g, sfdisk, test-disk and tons of network apps. I use it because I work on computers as a side job so it's pretty invaluable to have. it basically is the linux kernel 2.6.19.7 with Reiser4  livecd environment built with Gentoo Catalyst-2.0. [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

let me know how it goes. good luck

---

### Post by Mike1971 on 2007-04-06
No the session was not closed, still had a lot of space on the disk. I agree that it seems improbable but the only disks that fail are the disks that I tried to mount (there were 3 of them). Thanks for the info on the softwares for recovery of the pictures. I will definately try them out. 

For the boot issue. The bois loads i get the boot from cd message (my bios is set so that I can boot from cd first) but when it doesn't find a cd and goes to my hard drive, I get a disk boot failure. If I put in the live cd (yes I installed from the live cd) and go into the menu, if I choose boot from hard drive, Ubuntu loads from hard drive no problem. I have a feeling the boot and mbr don't get updated correctly during installation anymore...

I saw in another post how to reinstall grub so I'll try that out. And let you know how it goes. I'm really determined to get rid of windows. When I installed windows last night and configured my internet, the first thing I got was a popup (through messenger) telling me to go to a web site because my windows is screwed up. no doubt to fill me up on spyware and what not. ;-)

By the way, thanks for taking the time to help me troubleshoot, it's REALLY appreciated.

---

### Post by dannyboy79 on 2007-04-06
yep, the boot disk issue sounds like grub didn't get installed at all and it's still somehow using ntldr? that's very odd! you can install grub from the command line with these steps:

```
sudo grub
```

This will get you a "grub>" prompt 

```
find /boot/grub/stage1
```

this will return a location, use the location in the next line.

```
root (hd?,?)
```

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Exit the grub shell

```
exit
```

BUT
First, you can install it to the Master Boot Record of your first hard drive. Second, you can install it to the boot sector of the active (bootable) hard drive partition.
If you intend to dual-boot Windows, then you should avoid installing GRUB to the MBR. The reason for this is that Windows occasionally overwrites the MBR, for instance, when you reinstall it, and that could be quite often. When that happens, your Linux system will seem to disappear as your system starts booting directly into Windows, bypassing the boot menu altogether. To avoid this, install GRUB to the boot sector of the active partition instead. Here an awesome grub guide to help if needed. 
[http://www.linuxjournal.com/comment/reply/4622](http://www.linuxjournal.com/comment/reply/4622)


full credit for the above code goes to Bulldog, i just copied his instructions he provided in another thread.

---

### Post by Mike1971 on 2007-04-06
believe it or not my boot sector and mbr are ok. I read in another thread that boot from cd rom first in bios can cause this problem so I went into my bios to boot from HDD first and the computer boots without a hitch. so I installed and reinstalled windows ubuntu and dreamlinux for no good reason. now let see what I can do about the DVD issue...

---

### Post by Mike1971 on 2007-04-06
Hey it's me again would you tell me how to run dd_rescue? I think I have to compile it first? How do I do this?

Thanks!

---

### Post by Mike1971 on 2007-04-06
a little update: while trying to us dd_rescue (which I don't know how to compile or use) I put in my dvd. As usual it does not see it. but when i tried to eject it, ubuntu sent a message writing data to dvd-r plase do not remove disk. so i removed it before it would do anymore damage. This is what I think happened the first time.

---

### Post by dannyboy79 on 2007-04-09
> **Mike1971 said:**
> believe it or not my boot sector and mbr are ok. I read in another thread that boot from cd rom first in bios can cause this problem so I went into my bios to boot from HDD first and the computer boots without a hitch. so I installed and reinstalled windows ubuntu and dreamlinux for no good reason. now let see what I can do about the DVD issue...

how did you come to think that they were ok??? If the bios is what was telling you boot disk failure than that means the hdd disk that is being booted has something wrong with it. if grub  was telling that to you then most likely it's the boot sector of the  partition that grub is trying to load. boot from cd first causing a problem would only mean that there is a problem with your bios or your first drive. a computer booting is a standard thing and has been for a long time and I believe some1 has simply told you to not boot to your cdrom first and it happened to work for you but that was only because you reinstalled your os's. I don't believe that was the real problem but I guess we'll never know unless of course you're saying that you didn't reinstall your os's before you changed that bios setting. I have always booted to floppy first, then cd, then hdd and I have never heard of that problem.

anyway, glad you're up and running again and hopefully you get that dvd issue resolved. did you go over to cdfreaks, maybe they can help. they're a forum all about cd/dvd issues. google it.

---

### Post by Mike1971 on 2007-04-09
It was the problem. I have 2 choices in my bios first boot device and second boot device. if I don't tell the bios where to boot on the second device it doesn't go any where else to try to boot. my first boot device was cd rom and second boot device was none, so if there was no cd in the drive it would cause a boot failure. My computer is now set up as first boot device cdrom and second boot device HDD0. so now it goes on cd rom and if there is nothing it boots my hard drive. Any way thanks for the help it was greatly appreciated. I got dd_rescue to work but it does not seem to work. I get a file but with zero bytes when its done. Either I didn't put in the correct parameters or it can't do anything with my dvd. Anyway I'm concidering this dvd episode as case closed and moving on to other chalenges like getting games to work with ubuntu!

---

### Post by dannyboy79 on 2007-04-09
i totally misunderstood. I thought you were saying that you couldnt' set your bios so that it would always be cdrom and then hdd. you're saying that your bios didn't have anything listed for it's 2nd boot device. yeah, that's a problem. :-)

check out wine: [http://www.winehq.com/](http://www.winehq.com/)
there are a ton of games. just be aware of what version is in the repo's as 0.9.34 doesn't work with some games, it's to new. 0.9.31 does I believe.

---

### Post by Mike1971 on 2007-04-09
Yeah I have wine installed but I'm having difficulties with it. I tried to install Unreal Tournament GOTY without it using a loki installer and it works great. Now I got to get medal of Honor working and I will be set. If I get BF2 to work, I'll be in heaven but from reading other threads its not flawless under linux (it ain't flawless under windows either...) How about you show me how to log on to my computer remotely? SSH?

---

### Post by dannyboy79 on 2007-04-09
if you start a new thread right now, and put "log into computer with ssh" in the title I'll help you out. let me know. or do you have im? my scrren name is new2linx and I use aim.

Well I waited 40 minutes and still post back here that you would do that and when I searched for the exact phrase I didn't find anything. so here's a good thread to help you out. but I don't think that thread tells how to install it.

sudo aptitude install ssh

then that's it. it should install it and start it. to check type this in a terminal

sudo netstat -pat

if you see ssh than you at least have it listening. now make sure it's secure. either you can use password authentification which isn't very secure or you can use public/private keys which is harder to setup but way more secure. if you just want to use password authentification its easy and I can help you with that, MAKE SURE YOU BACK UP THIS FILE FIRST. that would be
**sudo cd /etc/ssh/sshd_config /etc/ssh/sshd_config-backup**
now lets edit it: **gksudo gedit /etc/ssh/sshd_config**
make sure you have this:
PasswordAuthentication yes
and also make sure you have this:
# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication no
PubkeyAuthentication no
allowusers yourusernamehere
MaxStartups 10:30:60 #this will prevent outside attackers from trying to connect over and over if they trying to run a script and attack you
then save it and exit. also, this is leaving the default port which is 21. that setting is towards the top. if you have a router and want access to your ssh server from the outside, then you need to forward port 21 to your internal ip address. don't forget this is very unsecure but if you user a very smart password using characters and letters and upcase and lowercase letters it would take a script like 20 years to crack into your computer so its still ok. but this password is the same as your users password so if that one isn't secure you should change it OR set it up using public/private keys. that's more than I want to help with at this very moment. I am fixing a customers computer and need to get it done so I have to go. just gogle ssh using public key and you'll find a guide without a doubt or seach the ubuntu forums. good luck

---

### Post by Mike1971 on 2007-04-10
I posted under a new thread.

---

### Post by Mike1971 on 2007-05-16
well just a follow up to this thread, it turns out my motherboard was on its way out which explains all the issues I've been having. I'v had crash issues in games (especially BF2 in windows) and dvd issues in Ubuntu. My motherboard is one of many that had bad electrolytic capacitors on them (early 2000's) they start leaking after a while. Needless to say I changed my motherboard and all is well. no crashes since.

---

