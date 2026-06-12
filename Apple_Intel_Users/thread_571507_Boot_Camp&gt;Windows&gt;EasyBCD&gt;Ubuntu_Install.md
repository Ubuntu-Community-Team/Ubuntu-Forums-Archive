---
title: "Boot Camp&gt;Windows&gt;EasyBCD&gt;Ubuntu Install?"
date: 2007-10-09
forum: Apple Intel Users
---

### Post by Hatfield on 2007-10-09
I have a Macbook C2D which I used Boot Camp on for Vista.

I want to add a partition for Ubuntu 7.04 that I can boot into using EasyBCD which I know can be done cause I asked over at the EasyBCD forums(Boot Camp Menu>"Windows">EasyBCD menu>Ubuntu).
[http://neosmart.net/forums/showthread.php?t=998](http://neosmart.net/forums/showthread.php?t=998)

Vista Disk Management sees:
200MB>Healthy(GPT Protective Partition) <-Mac
96GB>Healthy (Primary Partition) <-Mac
108MB>Unallocated
52.73GB NTFS> Healthy (System, Boot, Page File, Active, Crash Dump, Primary Partition)  <-C:

I tried using the directions from [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) last night, but somehow FUBARed everything(Linux Partitioner couldn't see the 6.43GB of unallocated space I had created; Tried a Guided install="Operating System Missing") and lost my Vista partition completely so I started everything from scratch within the past hour.  Restored the MacBook to full startup disk and reran Boot Camp to reinstall Vista.  The above partitions are current as of 10min ago.

What now?:confused:  I'm a complete newb when it comes to boot loaders and what-not.  I figured EasyBCD would be the easiest way since all I would have to do is "Add Entry" under EasyBCD once I get Linux installed into it's own partition.  I'd greatly appreciate any help.:)

---

### Post by jingo811 on 2007-10-09
You're having Vista on your Mac?  Are you using the kind of Mac with Intel motherboards?  If I were in your shoes then I would try and find a Full Windows XP installation CD.  It's better than Vista doesn't require as much juice and supports more Windows software :)
If you can get Win XP ( full install CD ) then I can help you make the bestest of partitions 8-[ ( me likey doing partitions on ppl from scratch !! )

Haven't tested resizing existing Windows nor Mac partitions before so I can't really help you in that department.  If that's the way you want to choose.

---

### Post by Hatfield on 2007-10-09
Thanks for replying, Jingo.  I don't have an XP disk and I actually like Vista...although I easily spend more time on the Mac side of my MacBook.:)

I'm wondering if I should use Disk Utility on the Mac side to create the partition for Linux.  Would that make a difference?  Whether I use Vista's Disk Management to create the partition or Mac's Disk Utility?:confused:

---

### Post by jingo811 on 2007-10-09
When partitioning for your Linux operating system use Linux's own partitioning program that comes with the Feisty Desktop LiveCD.

The only thing that Mac Os and Vista needs to do is defragment themselves to make room for Linux.  Then you put in the Ubuntu LiveCD to partition Linux.
I'm guessing that you didn't choose the manual partition option in LiveCD that's why you're having problems cutting up your disk like you want.  You get more control with manual partition than guided.

Read my guide before you attempt to do so!  It might make you better prepared for the storm when you're out in no mans land by yourself.
Specifically **Chapter 5** for this scenario.  It might make more sense if you read **Chapter 4** also they're related to eachother!!
[http://virtualseafarer.com/renaissance/allsparks/chapter5.html#ch5](http://virtualseafarer.com/renaissance/allsparks/chapter5.html#ch5)

---

### Post by cyberdork33 on 2007-10-09
gparted can shrink your hfs+ partition (OSX).

---

### Post by Hatfield on 2007-10-09
I got lost in the Ubuntu partitioner.:confused:  But I'm willing to give it a shot.

Right now, I'm "defragmenting hard disks" in Vista, but does that defrag the WHOLE disk or just the C drive/Windows partition?

---

### Post by cyberdork33 on 2007-10-09
> **Hatfield said:**
> I got lost in the Ubuntu partitioner.:confused:  But I'm willing to give it a shot.

Right now, I'm "defragmenting hard disks" in Vista, but does that defrag the WHOLE disk or just the C drive/Windows partition?just the windows partition. (Or other selected partition)

---

### Post by Hatfield on 2007-10-09
OK, I've run the 7.04 CD, clicked install, and gone through the menu choices before the partitioner(language, time, keyboard(macintosh right?)).
Clicked Manual and I see:

/dev/sda
free space  0MB(size)
/dev/sda1 fat32 /media/EFI system partition 209MB(size) 209MB(used)
/dev/sda2 103079MB(size) 36600(used)
free space 134MB(size)
/dev/sda3 ntfs /media/Untitled 2 56618MB(size) 12200MB(used)
free space 0MB(size)

What now?  I'm assuming I need to create another partition at the "end" of sda3 and I want it to be 10GB.  But how do I do it?

When I double click the last "free space", "Create Partition" comes up asking "size"(10, 240MB?), "location"(end?), "Use as"(:confused:), "mount point"(nothing drops down).

---

### Post by cyberdork33 on 2007-10-09
Don't use the installer, use gparted first to resize everything the way you want, then just install to the partition. Make sure you backup!

---

### Post by jingo811 on 2007-10-09
I'm having trouble analyzing your info. :-k See if you can run this command in 
_Applications> Accessories> **Terminal** _
and then write down on paper and try to reproduce how it looks originally.

```
~# **fdisk -l**
```

When I'm root I can see this I'm hoping you can see somthing similar even though you don't have root setup.

```
root@renaissance:~# fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/hda1   *           1        1278    10265503+   c  W95 FAT32 (LBA)
/dev/hda2            1279        3831    20506972+   c  W95 FAT32 (LBA)[/B]
/dev/hda3            3832        4998     9373927+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hdb1               1         131     1052226    b  W95 FAT32**
/dev/hdb2             132         261     1044225   82  Linux swap / Solaris
/dev/hdb3             262        4998    38049952+  83  Linux
root@renaissance:~# 
```

All other unmarked file-Systems are Linux related as you can see.

---

### Post by Hatfield on 2007-10-09
> **cyberdork33 said:**
> Don't use the installer, use gparted first to resize everything the way you want, then just install to the partition. Make sure you backup!

When I try to run gparted from the terminal, it says I can't because I don't have root privileges.

---

### Post by Hatfield on 2007-10-09
I'm in Terminal and I can't get it to work...being my first time in the terminal.  LOL

My prompt=
ubuntu@ubuntu: ~$

"fdisk -1" isn't working.


And darn it!  I have to leave right now to go to class...an A+ Certification class.  :lolflag:  Oh the irony!  I wish they'd teach more Linux.

I'll be back at 10pm EDT if you guys could please continue helping me out.

---

### Post by cyberdork33 on 2007-10-09
when something says you need to be root, or you don't have permission, you have to precede the command with sudo. Your normal user does not have free reign. This prevents mistakes and accidents. You don't use Linux as 'Administrator' like most people do in Windows.

Gparted should be available in the menus of the live cd (although it might be called something else). Partition Editor?

by the way it is fdisk -l not 1, that's a lowercase L. Be careful with fdisk though as it does not cooperate with GPT/GUID partitioning, while gparted does.

---

### Post by jingo811 on 2007-10-09
Also do this command in Terminal.


```
root@renaissance:~# **df -h**
Filesystem            Size  Used Avail Use% Mounted on
**/dev/hda3             8.8G  3.0G  5.4G  36% /**
varrun                506M  116K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  128K  506M   1% /proc/bus/usb
udev                  506M  128K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
[B]/dev/hdb3              36G   23G   12G  67% /home
/dev/hda1             9.8G  2.7G  7.2G  28% /media/hda1
/dev/hda2              20G  5.2G   15G  27% /media/hda2
/dev/hdb1             1.1G  454M  573M  45% /media/hdb1[/B]
root@renaissance:~# 
```

The highlighted filesystem pattern is what will interest you the most even though you might see something like 
**/dev/sda1** or something similar instead.

---

### Post by Hatfield on 2007-10-09
Bingo!  Got into gparted.  It's called "GNOME Partition Editor" under System>Administration>...   But I'm betting all you guys already knew that.

But...now what?:)  Where can I find a good tutorial on what to do...unless you guys want to continue to walk me through it.

GParted sees:
/dev/sda1  !  <Green>Fat32 200MiB(size)   boot(flags)
/dev/sda2     <purple>hfs+  96GiB(size)  34.10Gib(used)  61.90GiB(unused)
unallocated   <"darkpurple"> unallocated 128MiB(size)
/dev/sda3     <teal>ntfs   52.73Gib(size)  11.39Gib(used)  41.34GiB(unused)

I want 10GB out of the Windows partition(/dev/sda3) to be re-partitioned for Ubuntu.

---

### Post by cyberdork33 on 2007-10-10
> **Hatfield said:**
>  I want 10GB out of the Windows partition(/dev/sda3) to be re-partitioned for Ubuntu.

Note, this is risky without a backup...

Just select the windows partition (NTFS) and try to use the resize tool.

---

### Post by Hatfield on 2007-10-10
> **cyberdork33 said:**
> Note, this is risky without a backup...

Just select the windows partition (NTFS) and try to use the resize tool.

You're not kidding.:lolflag:  I have not even gotten to installing Ubuntu yet, and GParted has "hidden" my Vista partition.:(  No big deal though.  Remember I had just reinstalled Vista before the first post of this thread.:)

I actually ran the GParted LiveCD since I couldn't unmount the drives from the Ubuntu GParted.  I followed directions [here](http://gparted.sourceforge.net/larry/resize/resizing.htm) and chose the first choice(auto-configuration) at the first menu.  I don't think it was the right choice because my mouse didn't work well at all and it wouldn't let me Exit after I was through; I ended up having to just turn off the machine.  I couldn't even get into any of the menu items.  I later tried the "Macbook" option which I had previously overlooked and everything worked fine.  Maybe I shouldn't have continued to run GParted when it wasn't recognizing my hardware correctly?

GParted ran for a loooooong time.  About 2 hours.

Now Boot Camp can't see Windows at all at start up.  I know it's still there b/c I can see what appears to be all the Windows files in Finder.  When I hold down the Option key, I only get a choice for Macintosh.  I had defragged my C drive right before running GParted.

So I'm now searching around for answers to where in the heck my Vista went.

---

### Post by cyberdork33 on 2007-10-10
> **Hatfield said:**
> GParted ran for a loooooong time.  About 2 hours.

Now Boot Camp can't see Windows at all at start up.  I know it's still there b/c I can see what appears to be all the Windows files in Finder.  When I hold down the Option key, I only get a choice for Macintosh.  I had defragged my C drive right before running GParted.

So I'm now searching around for answers to where in the heck my Vista went.
Repartitioning will likely confuse the bootcamp loader. You should install refit. Gparted took so long because resizing a partition that has data on it is a delicate process. It takes awhile. If windows doesn't show up in refit, then post back. You will likely need to boot the Vista disc and repair something.

---

### Post by Hatfield on 2007-10-10
I figured as much.  Tried to repair the Vista partition, but it said it couldn't be repaired.
Wiped out Boot Camp's partition for Vista(again) and I'm reinstalling now.  The 10GB I freed up are still there though which is a good thing.:)

Update:  The 10GB I freed up with Gparted is not there anymore.:(

Should I run GParted again(the right way(macbook) this time)?  Or try the Vista Disk Management this time?

I'll take a look at rEFIt too.

---

### Post by cyberdork33 on 2007-10-10
> **Hatfield said:**
> I figured as much.  Tried to repair the Vista partition, but it said it couldn't be repaired.
Wiped out Boot Camp's partition for Vista(again) and I'm reinstalling now.  The 10GB I freed up are still there though which is a good thing.:)

Update:  The 10GB I freed up with Gparted is not there anymore.:(

Should I run GParted again(the right way(macbook) this time)?  Or try the Vista Disk Management this time?

I'll take a look at rEFIt too.
You shouldn't have done the complete reinstall without trying rEFIt. 

Since you are reinstalling everything anyway... There are several guides on getting Triple Boot working. 
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)
[http://ubuntuforums.org/showthread.php?t=533330&highlight=triple+boot](http://ubuntuforums.org/showthread.php?t=533330&highlight=triple+boot)

---

### Post by jingo811 on 2007-10-10
I don't quite follow here with all the BootCamp talk and stuff that I've never heard before.  Must be because you're using Mac stuff.

But I think the Ubuntu Alternate CD (i386) should be able to handle the partitioning much smoother and stable than the GUI G-parted.  Does Macs use i386 architecture?  I couldn't find any Mac architecture CD.iso to download from the Ubuntu install page.

[LIST]
[*]When you install Vista use Microsoft's partition program.
[*]Then when you install Mac OS use Apple's partition program.
[*]Last when you're going to resize the other older partitions and install Ubuntu use the Linux partition program.  And let the Linux bootloader GRUB handle all your 3 operating systems!
[/LIST]

You seem very attached to that BootCamp thingy let it go.  And try welcome GRUB (GRand Unified Bootloader).

---

### Post by cyberdork33 on 2007-10-10
> **jingo811 said:**
> Try welcome GRUB (GRand Unified Bootloader).
You do use Grub, after you load it from the EFI bootloader. On a Mac, you have to use another EFI loader to get Grub started, then you can boot either Ubuntu or Vista for that... (Or better yet, install grub to the ubuntu partition, and load vista directly from rEFIt).

Follow one of the guides I posted. Gparted gives you a nice graphical interface that I thought you could see what you are doing better. Since you are not concerned with keeping the data on your vista partition anymore, and you have the OSX partition already the size that you want it, then follow the triple boot guides after the part where you would normally have to resize the OSX partition.

---

### Post by Hatfield on 2007-10-10
Hell yeah!  I got it! ........but I didn't use EasyBCD and I really don't exactly know what I did.:lolflag:
Maybe you guys can explain it and maybe it'll help somebody else out.

After countless "failed" attempts, I "Restored full startup disk" in Mac's Boot Camp 1.4 to yet again start from scratch.  I already had a Windows driver disk so I didn't need to burn another.

1)I setup Boot Camp (again) for Vista.  Partitioned 35GB of the 160GB for Vista.
2)Installed Vista.
3)Once Vista is booted up, install the Boot Camp Windows Drivers CD you created from the Mac Boot Camp side.
4)Downloaded EasyBCD BUT I didn't end up using it so I'm **pretty sure you can skip this step**.
5)I defragged the C drive.
6)Booted a GParted Live CD holding down C to load up GParted.
7)In GParted's startup menu, I chose "Macbook" since the last time I did "auto-config" the mouse wouldn't work right and I couldn't exit properly(I had to just shut it down).  In Gparted, I Resized the 35GB Windows partition to 25GB leaving 10GB for Ubuntu.  It took a lot less time this go around which I'm assuming had to do with choosing "Macbook," but I'm not sure.
8 )Exited out of GParted and put in the Ubuntu LiveCD to install.  I figured I'd rather at least have it installed somewhere so I could try to boot it.
9)Installed Ubuntu choosing "Use the largest continuous free space" and it worked this time.  I just went through the installation without going into Advance or anything.  To tell you the truth, I don't remember even seeing any other options.  Just basic "Import other user stuff?", "name", password, name of computer.  Installed fine.
10)It rebooted and I held down the Option key to see if my Windows choice in Boot Camp was still there since a couple times it wasn't.  It was there!
11)Chose "Windows" and it took me to the GRUB menu.:confused:  And there was an option for Vista!:)  So I chose Ubuntu and I was booted into Ubuntu.:guitar:
12)Rebooted while holding the Option key again and chose Windows again.  In Grub, I chose Vista and got an error massage.

"Windows Boot Manager
Windows failed to start.  A recent hardware or software change might be the cause.  To fix the problem:
1)Insert the Windows installation disc and restart your computer...
<blah><blah><blah>.....
File: \Windows\System32\winload.exe
Status: 0xc000000e
Info: The selected entry could not be loaded b/c the application is missing or corrupt."

13)It wouldn't let me go any farther than that error page(couldn't shut down properly) so I inserted my Vista install CD, turned the computer off and back on while holding the C button.
14)Got loaded into the menu to "start Windows in safe mode" so that's what I chose.  Took me to the Install screen and I chose Repair.  Went through a bunch of scripts.  It worked!
15)Rebooted and it again went into Vista through the Grub menu.  Windows ran a Check Disk this time(probably b/c it saw it's shrunken partition for the first time) and took awhile starting up.  But then I'm in Vista.  Works like a charm.

Question is, what the hell did I do?  This doesn't sound like anything some of the other guides talk about doing.:confused:  I didn't have to configure Grub at all, no rEFIt, and no EasyBCD.  I'm just curious.

But I'm not sad that I got it working.  I now have a triple-boot 'puter.:)  I want to thank you guys for ALL your guidance.

---

### Post by jingo811 on 2007-10-11
I don't know what happened by reading your steps.  I guess it's one of those things you have to experience live in order to see every little quirk.

Which makes me curious.  I'm thinking about experimenting with the same setup as you had.
What kind of PC / Laptop did you use?
Did your operating systems come bundled with your Laptop purchase?
Or do you have a full Install CD for both Mac OS and Windows Vista?

I want to write a new partition tutorial based on this setup that you had.

---

### Post by cyberdork33 on 2007-10-11
> **Hatfield said:**
> **pretty sure you can skip this step**.
yep
> 5)I defragged the C drive.no need to do that on a new install, it is already defragged.

> 7)In GParted's startup menu, I chose "Macbook" since the last time I did "auto-config" the mouse wouldn't work right and I couldn't exit properly(I had to just shut it down).  In Gparted, I Resized the 35GB Windows partition to 25GB leaving 10GB for Ubuntu.  It took a lot less time this go around which I'm assuming had to do with choosing "Macbook," but I'm not sure.Likely more to do with that fact that the filesystem was nice and tidy

> 9)Installed Ubuntu choosing "Use the largest continuous free space" and it worked this time.  I just went through the installation without going into Advance or anything.  To tell you the truth, I don't remember even seeing any other options.  Just basic "Import other user stuff?", "name", password, name of computer.  Installed fine. Sounds normal

> Question is, what the hell did I do?  This doesn't sound like anything some of the other guides talk about doing.:confused:  I didn't have to configure Grub at all, no rEFIt, and no EasyBCD.  I'm just curious.

First, You should still install rEFIt. It will make your life easier. It takes two seconds to install in OSX, no 'configuration' needed. It will will greet you with a nice graphical boot menu each time you start your Mac, no need for Option key.

Ubuntu configures GRUB for you when it sees a windows partition. If you don't mind having to go through grub for windows, then just leave it alone, you are done.

---

### Post by Hatfield on 2007-10-11
> **jingo811 said:**
> ...
What kind of PC / Laptop did you use?
Did your operating systems come bundled with your Laptop purchase?
Or do you have a full Install CD for both Mac OS and Windows Vista?

I want to write a new partition tutorial based on this setup that you had.
Model Identifier:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.16 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per processor):	4 MB
  Memory:	2 GB

So yes my OS came bundled.
System Version:	Mac OS X 10.4.10 (8R2218)
  Kernel Version:	Darwin 8.10.1
  Boot Volume:	Macintosh HD

Boot Camp 1.4 for Vista Home Premium OEM.  I have not ever used the Mac's system restore disk.



Cyberdork, I'll consider rEFIt, but right now it's running smoothly and I don't want to risk messing anything up.  I'm going on a [cruise](http://ubuntuforums.org/showthread.php?t=568918) in a week(no internet connection) and I want the system working.  I intend to use my downtime on the cruise as a crash course learning Linux.

---

### Post by jingo811 on 2007-10-11
Hmmm would you say that many ppl uses this kind of Triple OS setup?  Or are you part of a minority?

Tip:  When you go on that cruise focus reading on SSH that will enable you to remotely work on an Internet connected Linux machine.  Working as root it's really cool.
ssh root@192.168.0.78 ( or something similar )
I only played with it at class in a LAN environment.  So I don't know exactly how to do it over the Internet, but if you read I'm sure you'll figure out howto.  Then you can teach me I'm too lazy to read books :-)

But then it requires you to know how to navigate and manage files with the text only CLI interface.  So read up on filesystems and terminal navigations first.
[http://ubuntuforums.org/showthread.php?t=573471](http://ubuntuforums.org/showthread.php?t=573471)
[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by cyberdork33 on 2007-10-11
> **jingo811 said:**
> Hmmm would you say that many ppl uses this kind of Triple OS setup?  Or are you part of a minority?
I'd say half of the Mac users here are triple booting OSX / Ubutnu / XP or Vista others are dual-booting, and even even other are just single booting Ubuntu.

---

### Post by jingo811 on 2007-10-11
Hmm... would you say that the majority who triple boots have a Full install Vista/XP cd or uses that Bootcamp Windows merger thingy:confused:

---

### Post by cyberdork33 on 2007-10-11
> **jingo811 said:**
> Hmm... would you say that the majority who triple boots have a Full install Vista/XP cd or uses that Bootcamp Windows merger thingy:confused:
I don't think you understand what bootcamp is. Bootcamp requires a full windows install CD. ALl that bootcamp allows Mac users to do is non-destructively repartition their hard drive (for windows) and it also includes a windows driver cd for the Mac hardware.

The paritioning aspect is just a front end to a Mac commandline tool which some people use by itself. That is how I initially shrank my OSX parition. I have also use gparted to shrink it further. The Mac tool is the only tool that can restore your OSX partition to the entire disk though. We also all use rEFIt as an OS chooser.

---

