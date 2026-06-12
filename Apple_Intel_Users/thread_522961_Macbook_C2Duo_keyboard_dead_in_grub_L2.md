---
title: "Macbook C2Duo keyboard dead in grub L2"
date: 2007-08-11
forum: Apple Intel Users
---

### Post by spudzik on 2007-08-11
Hi to all, and thanks in advance for any assitance. :)

I recently set up my Macbook Core 2 duo (2ghz) to triple boot (OS X, Ubuntu 7.04, XP Pro) but have not been able to get to the XP partition during grub boot up as the keyboard is unresponsive throughout the grub window. before and after it works fine, Any ideas?

thanks,

:guitar:

---

### Post by cyberdork33 on 2007-08-11
normal behavior. please search through the forum for more info. there is no sure fire way to fix it.

---

### Post by russo.mic on 2007-08-11
Install rEFIt, and put each bootloader on it's respective partiton only.  Grub will normal to boot Linux, and you'll have to wait 10 sec or remove the timeout.

Good Luck!

---

### Post by cyberdork33 on 2007-08-11
> **russo.mic said:**
> Install rEFIt, and put each bootloader on it's respective partiton only.  Grub will normal to boot Linux, and you'll have to wait 10 sec or remove the timeout.

Yep, I can usually get the keyboard working in Grub by unplugging and replugging my keyboard (on an iMac) but I haven't see anyone have luck with that on the portables.

---

### Post by david_edmundson on 2007-08-12
> **russo.mic said:**
> Install rEFIt, and put each bootloader on it's respective partiton only.  Grub will normal to boot Linux, and you'll have to wait 10 sec or remove the timeout.

Good Luck!

I tried installing GRUB on my various partitions which boot 'Buntu
(using grub-install /dev/sda5 ) but all that happens is I get two Tux icons in REFIT both seemingly linking to the same grub menu.

I've never really understood GRUB, could you elaborate on how to two Ubuntu partions to appear in reFIT properly.

Thanks.

---

### Post by cyberdork33 on 2007-08-12
you need to fix the MBR with windows, then it will contain the windows bootloader.

---

### Post by david_edmundson on 2007-08-13
Sorry I wasn't very clear. I don't have Windows. I have two Ubuntu installs - Fiesty and Gutsy. And this keyboard issue is really bugging when trying to switch between them, I end up changing menu.lst each time.

From reading what you said - both in this post and others. It would seem possible for each Ubuntu partition to have their own copy of GRUB which has it's own menu listing the relevant install. But for some reason despite having 2 Tux icons - both have the same menu, even though their "/boot/grub/" folder is different.

---

### Post by Jaymo on 2007-08-14
I've found a ghetto solution that works around 40-50% of the time. When grub is in stage1.5, press the down arrow on your macbook keyboard a few times, this sometimes gives me control.

Failing that, I have another solution that I also use. I have several grub menu.lst files:
menu.lst
menu.lst.win (Windows being the first GRUB option)
menu.lst.lin (Linux being the first GRUB option)
I just create launchers to copy over and replace the menu.lst file whenever I wish to change the OS.

Linux->Windows
Launcher: Reboot into Windows
Command: gksudo cp /boot/grub/menu.lst.win /boot/grub/menu.lst && gksudo reboot

And then from Windows, I can execute a batch files to do the opposite.

This becomes problematic when you update your kernel and it messes up your grub, but you can easily modify your respective menu.lst.* files to suit the new kernel(s).

---

### Post by Zelut on 2007-08-14
I've found that if I boot into OS X (the keyboard always works for me during rEFIt) and then reboot the keyboard is more responsive.. oddly enough.

Does anyone have links to launchpad bugs for this issue?  we should really make sure its documented or that we all add info to it if needed.

---

### Post by russo.mic on 2007-08-14
Wow,  everybody is over-complicating this issue!

rEFIt simply looks at each partition on what ever media is mounted on the computer at the time of boot, and figures out what is on each one based on the format of the partition.  (i.e. if you have a USB jump drive plugged in, it will think it's either windows or a legacy OS, based on if it's NTFS or FAT32 or whatever).

you need to install grub twice.  as you run through the Ubuntu installer, at the very end of the process (but before it starts copying files) hit the advanced button, and type in /dev/sda3 or /dev/sda5/ or whatever installation your working with at that time.  rEFIt should start booting into that respective partition, and from there refer to THAT partitions menu.1st file.  each partition lists it's OS as it's default OS to boot, then set the wait time to 1 sec or so.  There is other ways of installing GRUB, but you can use this without killing any data on the existing partitions as well.

It doesn't fix the keyboard thing, but it certainly works around it.  And to my knowlage, the keyboard problem is COMPLETELY random.  it might seem like hitting a few keys at the exact right time SOMETIMES gets it to work, but plot that out over 100 times, and you find no matter what you do it's 50/50.

My advice is to remember before doing this to install the windows bootloader so that you can use it to boot windows.  boot into recovery mode, do a fixboot and fixmbr, then install GRUB ONLY ON THE PARTITIONS WHERE UBUNTU IS!!!  this will allow windows to boot up based on it's loader.  I've currently got VISTA, OSX, Ubuntu, and Dreamlinux installed this way.

Good luck!

Russo

---

### Post by cyberdork33 on 2007-08-14
> **russo.mic said:**
> Wow,  everybody is over-complicating this issue!
yep partially my fault as I misunderstood what was going on. Sorry.

> rEFIt simply looks at each partition on what ever media is mounted on the computer at the time of boot, and figures out what is on each one based on the format of the partition.  (i.e. if you have a USB jump drive plugged in, it will think it's either windows or a legacy OS, based on if it's NTFS or FAT32 or whatever).Yes, but having grub in the MBR (as is the default) will kinda mess things up. This is why I think you have 2 linux icons pointing to the same grub config file.

> you need to install grub twice.  as you run through the Ubuntu installer, at the very end of the process (but before it starts copying files) hit the advanced button, and type in /dev/sda3 or /dev/sda5/ or whatever installation your working with at that time.  rEFIt should start booting into that respective partition, and from there refer to THAT partitions menu.1st file.  each partition lists it's OS as it's default OS to boot, then set the wait time to 1 sec or so.  There is other ways of installing GRUB, but you can use this without killing any data on the existing partitions as well.yea, although ubiquity is just using the grub-install command.

> It doesn't fix the keyboard thing, but it certainly works around it.  And to my knowlage, the keyboard problem is COMPLETELY random.  it might seem like hitting a few keys at the exact right time SOMETIMES gets it to work, but plot that out over 100 times, and you find no matter what you do it's 50/50.Really? I think my odds are worse than that. Not that I care, replugging the keyboard works EVERYTIME for me :)

> My advice is to remember before doing this to install the windows bootloader so that you can use it to boot windows.  boot into recovery mode, do a fixboot and fixmbr, then install GRUB ONLY ON THE PARTITIONS WHERE UBUNTU IS!!!  this will allow windows to boot up based on it's loader.  I've currently got VISTA, OSX, Ubuntu, and Dreamlinux installed this way.Yea, and unless you find a way to replace the MBR bootloader, you are probably gonna keep having the issue with refit detecting it. fixmbr ought to do it though.

---

### Post by eriksmith200 on 2007-08-15
I have the same problem: keyboard not working in GRUB after my fresh install of Windows XP and Kubuntu Feisty (so no mac OSX).

If i understand correctly I need to fix my windows MBR and then install GRUB only to the Kubuntu (boot?) partition?

I cannot get into windows, how do I fix the MBR? Windows install cd?

How do I then install GRUB to the Kubuntu partition? And to which partition exactly? Boot?

help is much appreciated

---

### Post by cyberdork33 on 2007-08-15
boot the windows Cd to the recovery console and use the 'fixmbr' command. Note, that you will need to config the windows bootloader to allow you to select ubuntu.

You can install grub manually to the correct partition with this command where X is the correct partition number. You want to install to the boot partition (this is the root partition as is default for ubuntu, unless you created a separate /boot partition.)
```
grub-install /dev/sdaX
```

---

### Post by duffman25 on 2007-08-15
> **cyberdork33 said:**
> boot the windows Cd to the recovery console and use the 'fixmbr' command. Note, that you will need to config the windows bootloader to allow you to select ubuntu.

You can install grub manually to the correct partition with this command where X is the correct partition number. You want to install to the boot partition (this is the root partition as is default for ubuntu, unless you created a separate /boot partition.)
```
grub-install /dev/sdaX
```

Hi
I originally filed the bug here:

[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172)

For the record, I filed it in debian and fedora. AFAIK this happens on many distro's including opensuse (but I don't want to create another bugzilla account for it...), I've tried some other distros (mepis) and it seems grub works, so maybe there's a solution for this problem, but until now the ubuntu dev's haven't fixed it.

It would be great if more people confirmed if this works fine on mepis live cd. See the bug report for details.

bye

---

### Post by cyberdork33 on 2007-08-15
> **duffman25 said:**
> Hi
I originally filed the bug here:

[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172)

For the record, I filed it in debian and fedora. AFAIK this happens on many distro's including opensuse (but I don't want to create another bugzilla account for it...), I've tried some other distros (mepis) and it seems grub works, so maybe there's a solution for this problem, but until now the ubuntu dev's haven't fixed it.

It would be great if more people confirmed if this works fine on mepis live cd. See the bug report for details.

bye

As far as I understood it, it was a bug with the Apple firmware. I will have to checkout mepis.

---

### Post by duffman25 on 2007-08-15
> **cyberdork33 said:**
> As far as I understood it, it was a bug with the Apple firmware. I will ahve to checkout mepis.

Apple hasn't released any fixes right?

---

### Post by cyberdork33 on 2007-08-15
> **duffman25 said:**
> Apple hasn't released any fixes right?

of course not, they don't care if grub works or not.

---

### Post by eriksmith200 on 2007-08-15
Hi,
I think i've figured out the steps to have my setup boot with the windows bootloader, just wanted to run it by you guys just to be sure.

These are my partitions:

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB    30.0GB  30.0GB  primary   ntfs         boot
 2      30.0GB    30.3GB  255MB   primary   ext3
 3      30.3GB    32.3GB  2048MB  primary   linux-swap
 4      32.3GB     160GB   128GB   extended
 5      32.3GB    47.3GB  15.0GB  logical   ext3
 6      47.3GB    67.3GB  20.0GB  logical   ext3
 7      67.3GB    160GB   92.7GB  logical   fat32

Checklist:

1. make a backup of /boot/grub/grub.conf

2. copy linux boot record:
dd if=/dev/sda2 of=bootsect.lnx size=512 count=1
put in windows C:\bootsect.lnx

2. fix windows boot record:
boot the windows install cd to the recovery console and use the fixmbr command
is this enough? do i need fixboot as well? that supposedly wipes the bootrecord, does this mean i will lose data/partitions?

3. edit windows bootrecord:
edit the file c:\boot.ini. Add the line c:\bootsect.lnx="Kubuntu" to
the end of the file

4. install grub to correct partition (boot):
grub-install /dev/sda2


This all sounds pretty easy, will it work like this? Do i risk losing data/having to do a new OS install?

---

### Post by cyberdork33 on 2007-08-15
> **eriksmith200 said:**
> Checklist:

1. make a backup of /boot/grub/grub.conf

2. copy linux boot record:
dd if=/dev/sda2 of=bootsect.lnx size=512 count=1
put in windows C:\bootsect.lnx

2. fix windows boot record:
boot the windows install cd to the recovery console and use the fixmbr command
is this enough? do i need fixboot as well? that supposedly wipes the bootrecord, does this mean i will lose data/partitions?

3. edit windows bootrecord:
edit the file c:\boot.ini. Add the line c:\bootsect.lnx="Kubuntu" to
the end of the file

4. install grub to correct partition (boot):
grub-install /dev/sda2


This all sounds pretty easy, will it work like this? Do i risk losing data/having to do a new OS install?


looks pretty good, except there is a little more to the fixmbr command:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

you shouldn't need the fixboot, you are just fixing the MBR, and you are not deleting or overwriting anything (except the MBR) so the only place I could see you losing data is doing the dd command incorrectly (dd is very powerful), but you would really have to screw it up to do that.

---

### Post by russo.mic on 2007-08-15
well, cyberdork,

funny how it's all worked for me....quit flexing your brain, as your head might explode.

---

### Post by cyberdork33 on 2007-08-15
> **russo.mic said:**
> well, cyberdork,

funny how it's all worked for me....quit flexing your brain, as your head might explode.
huh? I never said what you did wouldn't work... In fact, I agreed with you.

---

### Post by russo.mic on 2007-08-16
Sorry cyberdork.  

Bad day at work, mis read, took it out on my keyboard.  My fault, no offense.

Russo

---

### Post by eriksmith200 on 2007-08-17
hm my windows bootloader doesn't recognize my keyboard either...
i've seen mentioned that it's possible to get both the windows and the linux partition visible in rEFit, can someone maybe explain how?
i do have some difficulty getting into linux now :P

---

### Post by cyberdork33 on 2007-08-17
> **eriksmith200 said:**
> hm my windows bootloader doesn't recognize my keyboard either...
i've seen mentioned that it's possible to get both the windows and the linux partition visible in rEFit, can someone maybe explain how?
i do have some difficulty getting into linux now :P
yea, except I think you need OSX for rEFIt, which you stated earlier that you do not have.

You are the first person I know of that has said that the keyboard isn't working with the windows bootloader. did you do a complete format to a MBR disk? That would make sense to do, especially if you are not using OSX.

---

### Post by eriksmith200 on 2007-08-17
> **cyberdork33 said:**
> yea, except I think you need OSX for rEFIt, which you stated earlier that you do not have.


i do see the rEFit screen where i can select a disk to boot from, if i can select either windows or linux from here i'm good to go

---

### Post by cyberdork33 on 2007-08-17
> **eriksmith200 said:**
> i do see the rEFit screen where i can select a disk to boot from, if i can select either windows or linux from here i'm good to go

ok well you must have installed it before removing OSX, I assume. If it is not detecting both, then I don't know what to tell you. grub should be installed to the ubuntu partition, and windows bootloader to the MBR.

---

### Post by eriksmith200 on 2007-08-17
is there a way to get completely rid of the rEFIt / gray mac boot screen?

---

### Post by eriksmith200 on 2007-08-17
I decided to restart from scratch:

1. windows setup: deleted all partitions, created 1 new NTFS partition, full format
2. booted kubuntu 7.4 install cd
3. first did partitioning: guided, resizing partition 1, then went back and did a manual partition (see below)
4. after partitioning, before the actual install, by clicking on advanced i selected (hd0,1) (=linux boot partition) as the grub device

* parted output of result:
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number	Start	End	Size	Type	File system	Flags
 1	32.3kB	33.1GB	33.1GB	primary	ntfs		boot
 2	33.1GB	33.4GB	255MB	primary	ext3
 3	33.4GB	48.4GB	15.0GB	primary	ext3
 4	48.4GB	160GB	112GB	extended
 5	48.4GB	68.4GB	20.0GB	logical	ext3
 6	68.4GB	70.4GB	2048MB	logical	linux-swap
 7	70.4GB	160GB	89.6GB	logical	fat32

* grub> geometry (hd0):
drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82
   Partition num: 6,  Filesystem type is fat, partition type 0xb

When i now hold the option (alt) key during bootup (apple gray screen) i only get the windows disc as an option,
Anybody know what i'm doing wrong?

[edit]One thing i noticed after not shutting down windows properly: after reboot i got a menu for booting in safe mode etc, keyboard wasn't working...[/edit]

---

### Post by cyberdork33 on 2007-08-17
Well, I don't know what else to tell you. Maybe one of these guys that have a similar setup as you are trying to get working to help you some. (benanzo?)

---

### Post by ronocdh on 2007-08-17
> **cyberdork33 said:**
> Well, I don't know what else to tell you. Maybe one of these guys that have a similar setup as you are trying to get working to help you some. (benanzo?)
I'm also interested to see how Benanzo has his system set up, because IIRC he doesn't have OS X either (I assume Cyberdork meant this when he called the setups similar). I apologize if I'm oversimplifying, but isn't the problem that something like rEFIt is EFI-aware, whereas running GRUB and Windows, the system doesn't at all know how to access a GPT configuration? I don't exactly know what the solution is, but I would think ELILO would be worth a try.

Please tell me if I'm off-target here, because I've never bothered with ELILO; I still use rEFIt chained to GRUB on my triple boot setup.

---

### Post by pxwpxw on 2007-08-17
**eriksmith200**

The MBR is still msdos and will boot the active partition, which is windows.
I am looking now at this system which is intel PC, MBR partition.
Solution: put grub stage1 on the MBR (hd0). ( setup (hd0) )

Then you have to use 
```

title		WinXP
root		(hd0,0)
makeactive
chainloader	+1

```
for windows.

The separate grub boot partition is actually a waste of space.

You might be able to do it another way, by leaving the DOS MBR and setting the primary partition boot flag for your ext2 partition2, instead of partition 1 where it is now. You do this with either or both parted and fdisk, I forget which works. That would boot to grub menu, if you got the grub installation right.

To really see whats going on with flags (if sda is your drive)
```

 sudo hexdump -C -n512 /dev/sda
####lines deleted
000001b0  00 00 00 00 00 00 00 00  1e fd 1e fd 00 00 80 01  |................|
000001c0  01 00 07 fe 7f fd 3f 00  00 00 3f 04 7d 00 00 00  |......?...?.}...|
000001d0  41 fe 83 fe ff ff 7e 04  7d 00 c0 14 2a 01 00 fe  |A.....~.}...*...|
000001e0  ff ff 05 fe ff ff 3e 19  a7 01 c3 63 d7 01 00 00  |......>....c....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```
The 80 in the 1b0 line is the boot flag for the 1st primary.
It is a good idea to save a copy of the DOS MBR with dd.

BTW, the keyboard problem is in the mac firmware, nothing you do is going to fix it, I tried the windows ntbootloader menu too, no dice. (on MacBook c2d), on that I currently have Macosx, and 2 penguins with different menu, but not using windows.

---

### Post by eriksmith200 on 2007-08-18
> **pxwpxw said:**
> **eriksmith200**

The MBR is still msdos and will boot the active partition, which is windows.
I am looking now at this system which is intel PC, MBR partition.
Solution: put grub stage1 on the MBR (hd0). ( setup (hd0) )


that is where i started, when selecting the HD from the apple boot menu i entered grub where i couldn't use my keyboard most of the time. when the keyboard did work i could boot into windows.

is there a way to put both windows & linux in the apple boot menu?

---

### Post by pxwpxw on 2007-08-18
Yes, not much use if the keyboard is unreliable. I lost the plot.

I have had a MBR only system on the MacBook C2d (due to an unfortunate accident with gparted), cant remember what it did icon wise.

Hope to hear from **benanzo** about that.

But I wanted Macosx and Linux the easy way, and so use Refit, also to get some idea what EFI is about.

I think you need Refit.

My currrent mixed MBR/GPT partitionng (as installed by macosx), uses Refit or mac firmware booting, Macosx and 2 linux boots.

The firmware boot selector (option icon picker) will only offer 1 "windows" icon for one of the MBR partitions even if you have more bootable. It will also display one internal (Macox or Refit) and one external usb Refit (choise of 3). Refit offers a lot more icons if there are grub stages elsewhere, but cant actually get booted from non-primary MBR partitions.

I have checked this when having 2 linux boot sectors in use, and bootable from rEFIt, together with a Macosx icon. That could have been (from refit) MacosX, Linux, Windows.
I have partitions 5 and 6 setup from linux as LBA partitions, not seen in the MBR system, and there is no MBR "extended" partition, just 4 primaries.

But refit must be on a Macos HFS+ partition, and you need macosx to install and configure refit.
However you can put refit on a separate small macos (hfs+) partition (have tried that). The refit docs suggest it is also possible to put it on the 200MB EFI partition (fat32), I dont know how, it involves smart use of the bless function.

I have only used Refit on a HFS+ MBR primary, but you might be able to put it on a GPT LBA partition anywhere (beyond MBR reach), then pull down and re-use the MacosX primary if you want. So that would leave you with another primary for booting.
 
1. EFI 200MB (unused place marker)
2. Linux (ex Macosx)
3. Linux
4. Windows
=======end of MBR====
5. HFS refit
6. swap
7.....
======

The point being that you can preset the 2 Linux menus to different kernels or whatever, so you choose from 2 boots without hangups most of the time, and can eventually get the keyboard for the occsional situation needing something else.

This whole shambles is due to the keyboard problem, because with one reliable grub menu we can boot almost anything (except macosx) anywhere, including get to command line to do it manually. 

If you put Refit on a usb stick and enable it using macosx, you can boot it from the apple firmware boot selector, and it is a useful tool for a MBR/GPT system, has its efi shell utilities to see what is on the drive etc.

I dont know if you have actually had windows working. I understood it requires apple mac drivers usually installed by bootcamp, I have not yet got Bootcamp Assistant to work, it refuses to accept my partitoning, and wont do anything at all. I can live without windows, but would like to try the system some time.

---

### Post by cyberdork33 on 2007-08-18
> **pxwpxw said:**
> I dont know if you have actually had windows working. I understood it requires apple mac drivers usually installed by bootcamp, I have not yet got Bootcamp Assistant to work, it refuses to accept my partitoning, and wont do anything at all. I can live without windows, but would like to try the system some time.

The driver cd image is on your mac you can pull it out of it;s installed location and burn it manually. You do not need to run the bootcamp assistant.
[http://www.mactelchat.com/tips-n-tricks/229-install-bootcamp-mac-drivers-without-burning.html](http://www.mactelchat.com/tips-n-tricks/229-install-bootcamp-mac-drivers-without-burning.html)

---

### Post by pxwpxw on 2007-08-18
> **cyberdork33 said:**
> The driver cd image is on your mac you can pull it out of it;s installed location and burn it manually. You do not need to run the bootcamp assistant.
[http://www.mactelchat.com/tips-n-tricks/229-install-bootcamp-mac-drivers-without-burning.html](http://www.mactelchat.com/tips-n-tricks/229-install-bootcamp-mac-drivers-without-burning.html)

Yes, thanks I found it now, just open the bootcamp assistant app package contents and the driver disk .dmg  is right there.

---

### Post by cyberdork33 on 2007-08-21
> **cyberdork33 said:**
> As far as I understood it, it was a bug with the Apple firmware. I will have to checkout mepis.

Just as a a follow up, I booted the Mepis Live CD and had the same issue.

---

