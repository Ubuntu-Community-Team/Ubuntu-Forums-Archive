---
title: "ext2IFS vs. ext2FSD : which is better at assessing ext3 in windows?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by mijj on 2007-05-01
I would find it useful to be able to read/write access my ext3 linux partition in windows.

After some searching i've found these alternative windows solutions: ext2IFS ext2FSD.
[[COLOR="SeaGreen"]_*[SIZE="3"]ext2IFS[/SIZE]*_[/COLOR]]("http://www.fs-driver.org/index.html")
[[COLOR="SeaGreen"]_*[SIZE="3"]ext2FSD[/SIZE]*_[/COLOR]]("http://ext2fsd.sourceforge.net/")

now .. i'm no wizz at windows nor linux ... so .. some expert guidance is needed.

Are there benefits/hazzards of one method over the other ... or .. are there no real differences?

---

### Post by Rhubarb on 2007-05-01
I've successfully used ext2IFS a few years ago.  It was easy to install, and worked straight away (after a windows reboot).

Though I don't use windows anymore :)

---

### Post by msandersen on 2007-05-06
Never tried ext2FSD, it's still early Beta  (or Alpha; v0.31) from what I can tell. I have used ext2IFS for a while though, and haven't had any major issues with it. There was one issue when a volume filled up, eg a large download/file transfer; the driver didn't recognise it and the system slowed to a crawl. Known bug, may be fixed in the upcoming 1.11 release. It will have full Vista and 64-bit support, as well as the ability to set a volume as Read-Only and recognise dot-files as Hidden files. It is the more mature of the two.

---

### Post by zerosystem on 2007-05-06
Just like msandersen, I've only used ext2IFS, and I've found it to have no problems whatsoever..

I didn't even have to reboot after installing it. Instant access to my Ubuntu partition.

---

### Post by KB8 on 2007-08-14
I have been using Ext2FSD for more than 4 years. It never ever cause me any problem. Stable and reliable. Recently I started to use its writing support for ext2 partitions (since 1+ year ago). It also works very well. It is unfair to label it as a beta product based on its version number, as this is an open-sourced software. I never use ext2ifs (because I don't see the need), but ext2ifs is NOT open-sourced (I vaguely remember either its early versions or its ancester product had source public available, please correct me if I am wrong). However, ext2fsd is GPL'd. I consider this as a big advantage over ext2ifs.

Also, Mart,  the developer of ext2fsd, is very friednly and responsive to user questions. I asked him how to automatically mount ext2 partitions via email and got his response in minutes. As a GPL'd software, the developor has no desire to bump up the version number with no technical point to attract people.

---

### Post by nvrpunk on 2007-08-14
I have used both, Ext2FSD allows you to write to ext3 but has to have some icon on the toolbar where as ifs doesnt make you have to mount it.  It is more built in.  FSD is newer and in the end I would have to say better, although less transparent.

---

### Post by KB8 on 2007-08-14
It turns out there are at least two ext2ifs products, chek here for another one, by John Newbigin:
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)
This one is GPL'd but it seems not actively developed any more:

And check here for history of Stephan Schreiber's ext2ifs:
[http://www.fs-driver.org/author.html](http://www.fs-driver.org/author.html)

John listed four products and Stephan's work is the only close-sourced one among the list.

I myself also used explore2fs
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs-old.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs-old.htm)
This is again developed by John Newbigin and it is open-sourced. Apprently explore2fs isn't as convenient as a native ext2 system driver like ext2fsd/ext2ifs though, from a user prospective.

---

### Post by KB8 on 2007-08-14
From my understanding, both Ext2FSD and Ext2IFS (by Stephan) treat ext3 partition as ext2 for writting support. that is they ignore the journal.

I guess the volume manager from ext2fsd was recently added for more convenience. At least for versions 0.2x and 0.19, the default installation does not contain the volume manager. Therefore for those versions you don't have the systray icon. And you could mount the ext2 partitions without the help of the volume manager. Of course you can mount them without rebooting windows, just as ext2ifs does. With some configurations you can also make the partitions automatically mounted when you boot your computer - this would have the same effect as the ext2ifs. With the volume manager, you have a bit more flexibility. Say if I have multiple ext2/3 partitions, I can mount one partition as read-only and another with write support, and another with different code page, etc. This is easy and intuitive with the volume manager. I am trying to work out how to achieve this without the volume manager.

---

### Post by impulse1618 on 2007-08-14
I've been using Ext2FSD for a few months after switching from Ext2IFS. I haven't had problems with either, but I preferred an open source solution. Also, it looks like Ext2FSD has a more active development.

> **nvrpunk said:**
> I have used both, Ext2FSD allows you to write to ext3 but has to have some icon on the toolbar where as ifs doesnt make you have to mount it.  It is more built in.  FSD is newer and in the end I would have to say better, although less transparent.

I was annoyed by both the icon and the tray, but these are pretty easy to disable if you don't mind editing the registry. First, open the Ext2FSD Volume Manager through either the start menu or double-clicking the icon. From the menu, select Tools > Service Management. Under Service Startup Mode, select SERVICE_SYSTEM_START. Click Apply and close the window.

Now, from the start menu select the command prompt or just Run. Type regedit to open the registry editor. You want to navigate to My Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run. I don't remember the key you want to delete (I deleted it already), but I think it points to Ext2Mgr.exe in the Ext2Fsd path that you installed to. It should be fairly obvious, but you might not want to do this if you are unsure.

In any case, this is where programs that run on startup are, so you can delete whatever you don't want to run at startup (and didn't know about). An alternative would be to replace HKEY_LOCAL_MACHINE with HKEY_CURRENT_USER to see if you have any particular things running at startup that aren't for all users.

Once you do this, reboot and there should be no splash and no icon, but you can access your Ext2/Ext3 partitions without a problem. If you need to configure anything, just run the Ext2FSD Volume Manager. You can close it when you are finished. If you don't want your partitions to automatically mount on startup, you might want to change the Service Startup Mode to something else. I haven't tried other options.

---

### Post by brodiepearce on 2007-08-24
I'm using Ext2FSD on my XP installation to access my Ext3 media partition on another drive, however, Ext2FSD isn't mounting it automatically?  Every time I start up I have to manually change the drive letter through the Ext2FSD Volume Manager.

It's set for SERVICE_SYSTEM_START, but it's till not mounting it automatically.

---

### Post by KB8 on 2007-08-28
To make my post complete, and to answer some users' question on how to automatically mount the ext2/ext3 volumes when windoze boots up, using ext2FSD of course. Hre is how:

Firstly there are two ways to do it, as far as I know. The first one is to use the mount.exe utility and run a dos batch file when system boots; the second method is to edit registry key (only one key will added per ext2/ext3 partition) . Each has advantage and disadvatnage.

1. Use mount.exe and run it automatically with a dos tach file:
The mount.exe is from the same author of Ext2FSD. Before version v0.30, the Ext2FSD installation file contained this utility. But for the latest version (0.31a at the date of this posting), this utility needs a separate download. To make you happy, I dig this link out, for all ext2fsd project related downlaods:
  [http://sourceforge.net/project/showfiles.php?group_id=43775](http://sourceforge.net/project/showfiles.php?group_id=43775)
On that page, you should download "Mount". As usual download and unzip, the binary executable, mount.exe, is included. You can move the executable to wherever you see it fits and just use it, no need to install. I usually put it in the same foler where majority of ext2fsd files stay, i.e.,
  **C:\Program Files\Ext2FSD\**
(I customised my windows installation, so for me "C:\Program Files" folder becomes "C:\Programs", :) )
The mount.exe binary is actually two pragrams in one: mount and umount. The former for mount an ext2/3 partition and the latter for umount it. For umout purpose you use it with "/u" option, or duplicate a copy and rename it umount.exe then use umount straightaway. The usage of mount/umount are all in documation anyway (FAQ or readme? can't remember).

The rest is to create a dos batch file that uses mount.exe to mount the ext2/3 partition. Here you again have two choices here for the running the batch file automatically when system boots up: (i) to create a link to the batch file in
 **C:\Documents and Settings\All Users\Start Menu\Programs\Startup\**
(did I mention that on my hacked installation, "C:\Documentions and Settings" becomes "C:\Profiles". I really hate Micro$oft habit to put white spaces into file/directory names. Hate it. Actually I have been trying hard to not to touch any M$ product. But at work I have to use Windoze and Word. Luckliy enough I am allowed to customise my windows installation myself.)
folder, or (ii) alternatively you use C:\AutoExec.bat to call your batch file or just embed the batch jobs into autoexec.bat. Make sure your windows box runs C:\Autoexec.bat, though. Nowadays Windows can be configured not to parse autoexec.bat.

For this method I only listed the general procedure but not in details, because I myself prefer the second way and I am reluctant to test it just to write this instruction. I know it will work without any problem. If you prefer to go with this wmthod, there are step-to-step how-tos on the internet, for example here is one:
  [http://www.codejacked.com/automatically-mount-your-linux-partition-in-windows/](http://www.codejacked.com/automatically-mount-your-linux-partition-in-windows/)

2. The registy editing method.
This is the method I am using and prefer. Hence I'll bring you detailed instructions. It may sound scary to edit the bloody registry but it is actually deadly easy, and much more effecient and flexible than the first mount.exe + batch file method.

The trick is to add a registry key to
  **HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\DOS Devices\**
tree, if you have only one ext2/3 partition. What to be added exactly? Let me list mine as an example.

I have two ext2/3 partitions, all in the same hard disk together with NTFS/FAT partitions: the second partition is formated as ext3, holding the root file system for Linux; the 4th partition is ext2 formatted, serving the /home for my linux system. There is a small linux swap partition as well. All rest partitions are in windows native formats, i.e., NTFS/FAT32. I'll mount my linux root partition as "R:" drive and home partition as "H:" on windoze, so I add these two STRING keys:
  **R:**
as the key name, the type would be REG_SZ and the value would be:
  **\Device\Harddisk0\Partition2**
and samely another string key
  **H:**
with value
  **\Device\Harddisk0\Partition4**
Similarly you need more keys of this kind if you have more ext2/ext3 partitions. Windows think the order of hard disks starts from "0", so harddisk0 means the first hard disk; inconsistently it thinks partition starts from "1", so the first partition on the first harddisk would be \Device\Harddisk0\Partition1, which usually would be the "C:" drive. You should know your partition scheme, don't you. If your forgot, the Ext2 partition manager will help you to identify the partition order. Or, you boot your computer to linux and run "sudo /sbin/fdisk -l /dev/[h|s]da" to find out. The unix name convention for a disk volume (partition|slice) is logical and consistent. You can't be confused there. It is nice that ext2/3 partition labels will be displayed in Windows explorer.

You add the registry key(s) by right-clicking in blank area on your right panel, after you open the registry editor, and New -> String Value -> Change the name of the key to the driver letter (Captical, with colon) -> double click the key and assign its value.

Alternatively I prepare this registry template for you. You can edit its content to fit you partition scheme and desired driver letters. Then you put the key into place by double-clicking the registry file.

=====template Ext2FSD.reg file, edit to fit your own setup=======
[B]Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\DOS Devices]
"R:"="\\Device\\Harddisk0\\Partition2"
"H:"="\\Device\\Harddisk0\\Partition4"[/B]
========end of Ext2FSD.reg file==================

The reg file was exported from my windows xp bos but should work for windows 2000 and windows 2003 as well. They all use the same version of registry format. Please note the double backwards slashes. The first line specify the registry version. It can be changed to [REGISTRY5] or something similiar, can't remember now.


Once you've added the registry, reboot your windoze box, and you are done.

I remember This registry editiing was documented in some early versions of Ext2FSD documentation but it was removed from the FAQ. At least I checked v0.31a documentation and it is not there any more.





I said this second method (registry hacking) is better than the first one (mount.exe + batch file) because the first method needs administrator privilge. You have to use a seperate utility (mount.exe) and it is now even a separate download (not included in the default ext2fsd installation file). The second method need an administrator account to setup but after that a power/limited user can also access the ext2/3 partitions without any problem. It will stay even you upgrade Ext2FSD. It even works in safe mode. It is a more native way to mount a dos device than the "mount.exe + batch file method". It doesn't need assistance of mount.exe, or ext2 utility partition manager. The only disadvantage is that registry hacking may scare many people away.

If you use the new ext2 partition manager, you'll always need administartor privilige. But the partition manager brings convenicence to you for some one-off configurations, such as ext2 writing support, turn on/off ext3 force writing support, specify the codepage, etc. In my case, my linux root partition is ext3 and I only enable read access and my home partition is delibrately formatted as ext2 and I enable write access.



By the way, the ext2 partition manager splash screen and the systray icon is invoked by running
 **Ext2Mgr.exe /hide**
command. By default that was turned on via a key in
 **HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run**
tree. Remove the key and the splash screen and systary icon will not appear when your windoze reboots. This was mentioned by impulse1618 in a previous post.

---

### Post by Nightwolf on 2007-08-29
Thank you so much, that's exactly what I was looking for! :)

I use ext2FSD because ext2IFS made my windows crash several times (all programs that were accessing the harddisk in that moment could not be ended and the system got slow, only turning power off helped :(). I have no idea why this seems to happen only on my computer but extFSD works perfectly so I use this instead (and I'm absolutely satisfied with it).

---

### Post by brandonjp on 2007-09-16
> **Nightwolf said:**
> Thank you so much, that's exactly what I was looking for! :)

I use ext2FSD because ext2IFS made my windows crash several times (all programs that were accessing the harddisk in that moment could not be ended and the system got slow, only turning power off helped :(). I have no idea why this seems to happen only on my computer but extFSD works perfectly so I use this instead (and I'm absolutely satisfied with it).

well crap - I've been on these boards praising the ext IFS driver from [www.fs-driver.org](www.fs-driver.org) - yet, I've been having the same 'crash' type problems where my system just hangs and crawls to close everything, so i finally end up powering off instead.  I didn't even think that the ext2 IFS driver might be the problem
thanks for the heads up
--bp

---

### Post by brandonjp on 2007-09-17
tried ext2FSD last night and was not impressed...
First off, the ext3 drive could be part of my hanging problems, but the ext2 IFS driver is not a lone cluprit - after a couple hours of ext2FSD I had rebooted 10 or 12 times, sometimes my system would hang as soon as the drive was mounted...which brings me to my next point...

having to constantly re-mount the ext drive at every boot is for the birds - I know, I know - it's possible to hack your way to auto-mount, but i'm not yet convinced that it's really any better of a driver than running that ext2 IFS piece of cake

oh and the tray icon just annoyed the heck out of me too

BUT!  if we could get a portable / standalone version of ext2FSD, that's money for this guy:  [http://ubuntuforums.org/showpost.php?p=3360321&postcount=6](http://ubuntuforums.org/showpost.php?p=3360321&postcount=6)  --  or maybe that's already possible, i've just not looked very closely
--bp

---

### Post by lewisskinner on 2007-12-20
I used to used ext2FSD, and had real problem with music on on ext3 drive being written incorrectly by Windows Vista.

It also reconfigured my DVD-/+RW as a plain CD-ROM, and I couldn't play DVD's.  I didn't even think it was the FSD driver, but having read around, I suspected it, uninstalled, and bingo!

I'm going to try IFS now...

---

### Post by hazelkid on 2007-12-29
Does ext2fsd has utf8 encoding support? I'm using ext2ifs and I have some problems with non-us characters on windows.

---

### Post by miatawnt2b on 2008-02-03
I have tried both ext2ifs and ext2fsd on my windows box and am having a little problem.  I use an external usb drive with ext3 and switch between windows and ubuntu regularly with it.

The issues I have is that my video encoding program (DVDShrink in this case) will not write an ISO bigger than 1GB to the ext3 drive.  It thinks that the filesystem can't support larger files than 1 GB, so instead of creating an 4.5Gb ISO it creates an MDS file with 4x1Gb chunks.  If I create the iso to an NTFS drive, it creates a 4GB ISO, then I can transfer that 4.5Gb file no problem to the EXT3 disk.

Anyone have experience with programs not recognizing the ext2/3 filesystems as large file capable?

-J

---

