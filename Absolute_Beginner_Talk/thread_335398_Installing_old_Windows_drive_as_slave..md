---
title: "Installing old Windows drive as slave."
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by RockinDolphin on 2007-01-10
Hey, all!

    I've been going over older posts and can't seem to figure-out what to do. I'm a beginner, so don't assume I know anything.

    I've recently installed Ubuntu onto a brand-new 120Gig drive. Now that it's up and running, I thought I'd add-on my older Win98SE drive as a slave so I could copy files. Simple thing, right? Well, not so far as I can tell. It *seems[I]*[/I] that the computer sees the slave drive as it shows it on the (In my opinion practically useless 'Device Manager'. I see no way you can manage devices with it like you can with Windows...) However, I cannot see or access files.

    I have been looking into the 'mounting' thing and found a post where someone had an issue almost like mine, but their drive was NTFS, or something like that, and mine is a FAT32. If I put-in fdisk -l, I get this:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14311   114953076   83  Linux
/dev/hda2           14312       14593     2265165    5  Extended
/dev/hda5           14312       14593     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)

    The hdb1 40Gig is the one I want as a slave and is jumpered as such, but I can't seem to read it. Any suggestions? Thanks!

~Kenny

---

### Post by kebes on 2007-01-10
First off, look in the directory "/media/" and see if there is a directory there (maybe called "windows" or maybe called "hdb1") that has your files in it. Often times these partitions are auto-mounted.

However if it's not (probably because it was not connected during the initial install), here's what you do. In a [terminal]("http://psychocats.net/ubuntu/terminal"), (Applications > Accessories > Terminal), type these two commands:

sudo aptitude install disks-admin
gtksu disks-admin

This will install, and then open, a disk administration utility. You should be able to see your second hard drive, and find the partition you want. You can then select a "mountpoint" (like /media/windows) and click enable. (Note: if for some reason disks-admin won't install, you can try installing a program called "gparted" which allows you to format partitions... it will also allow you to do similar things.)


If you can also do these things on the commandline. See the ubuntuguide for details:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by kidders on 2007-01-10
[COLOR="Silver"]Hi there,

A devices position on your IDE bus makes no difference to anything except Windows, which can sometimes get upset about unexpected moves.

If you want access to your files on the FAT partition, you need to mount it, as you would any other filesystem. Something like **mount /dev/hdb1 /mnt/whatever** will get you started. From there, you can look into modifying /etc/fstab to set some default mount options, or have the filesystem mounted automagically.
[/COLOR]
**Edit:** Oops... too slow. :-)

---

### Post by RockinDolphin on 2007-01-10
None of these worked. I also looked in Add/Remove and didn't see anything for Gpart, or whatever it was. On the first recommendation (I can't see the posts at this moment.) the program or whatever that was supposed to come-up didn't, and on the second recommendation it told me access was denied.

---

### Post by confused57 on 2007-01-10
See this guide for mounting either a ntfs or FAT32 partition:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
directions are for using a live cd, but it works with an installed OS, also...

Are you just wanting to access the Win98 drive, or also be able to boot up Windows?

---

### Post by RockinDolphin on 2007-01-10
I'm mainly just wanting to access the files. Copy them over to the Linux drive so I'll have a copy of important things, for one thing, but thought I'd see what all I could run with Linux and maybe using Wine.

---

### Post by migla on 2007-01-10
**gparted** is in the repositories, *if* you want to mess around with partitions.
 In a terminal window you can type:
```
sudo apt-get install gparted
```
or you can find it and install it with **synaptic** (System>Administration>Synaptic Package Manager)

To run it, type in a terminal or in the box that pops up when you press [Alt] and [F2]:```
gksudo gparted
```  (It should also end up in the System>Administration menu) Then you're able to wreak serious havoc on your hard drives.

---

### Post by RockinDolphin on 2007-01-10
It's saying that it already exists, and such, but I still don't see how to access the files.

---

### Post by RockinDolphin on 2007-01-10
Okay. Cool. I've got the app up and running and it sees the Windows slave drive. however, I still don't see the files when I go to Places/computer/file system. I just see the Linux drive.

---

### Post by migla on 2007-01-10
Maybe this howto can help: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) (I'm rather a newbie myself)

---

### Post by RockinDolphin on 2007-01-10
Well, I'm not sure what's going on. At first, I thought I was having *some[I]*[/I] success, but now it looks like I've done something to the boot sector on the slave drive.

I was running Gpart and not having any success with being able to look at my files on the Windows slave drive, so I thought maybe I should try unmounting it and then remount it, but when I clicked on 'unmount', I saw that there was quite a bit of drive activity and I was concerned that my drive was getting formatted. Gpart showed that drive with an empty bar whereas it was almost full, before. I clicked on something else, I don't know what it was. Perhaps remount? And after a small bit it showed that the slave was almost full, which it is.

So I shut down the computer, pulled the Linux master and switched the jumper so the Windows disk was a master again. I booted-up, but got the message that the was a boot error. I shut down, switched the jumper and put in an XP drive that I was using as master before I started trying to get Ubuntu running, fired it up and it showed that the files were still there, but I tried the 98SE disk again and got a boot error. 

I'm still not able to view any files from this slave drive. What gives? I'm getting people trying to be helpful, but I'm getting nowhere. I managed to get that Gpart program downloaded and all of that, and it sees the drive and shows that it is almost full, but that's all. I still haven't been able to access my files.

---

### Post by RockinDolphin on 2007-01-10
Okay. i found it. A good piece of info to tell people is where to look. Someone told me a place to look, but it didn't make sense. However, I got to noticing some things, so I finally tried Computer/File System/Media/and found Windows. I clicked on Windows and saw my files on my slave drive.

I'm going ot have to say that I believe this is retarded. I feel like it should have been listed as 'File System2', or something. For an OS that's supposed to be so great, some people sure have made it a pain to get to learn.

---

### Post by confused57 on 2007-01-11
> **RockinDolphin said:**
> Okay. i found it. A good piece of info to tell people is where to look. Someone told me a place to look, but it didn't make sense. However, I got to noticing some things, so I finally tried Computer/File System/Media/and found Windows. I clicked on Windows and saw my files on my slave drive.

I'm going ot have to say that I believe this is retarded. I feel like it should have been listed as 'File System2', or something. For an OS that's supposed to be so great, some people sure have made it a pain to get to learn.

The first link I gave you:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

mentions navigating to your /media folder:
"6) I went up two levels the top of the filesystem and opened my /media folder. Inside that was my new 'windows' folder.
I opened my /media/windows folder to see my Windows root files. I can navigate from there to the 'My Documents folder and find whatever file I need to copy."

I realize it's difficult for new users, I was totally and completely "befuddled" when I first started using Linux...after using Ubuntu for awhile, it became easier to configure my system, install new programs, etc.

---

### Post by Patrick K on 2007-01-11
Are you able to access the drive and files from XP? That is, boot XP with the W98 drive as slave. If so, I suggest copying all the files you want to keep to the XP drive before messing with the 98 drive anymore. You could lose your data. Do not re-partition or reformat the drive, that will destroy all the data on it

Do you have a W98 boot disk?  If not, generic ones are available on the Internet, do a search. Install the w98 drive as master and boot with the boot disk. It will have some utilities that may help. You may just need to set it active. There are two way I how to do it. Both are run from the boot disk. One, run Fdisk and select make "partition active." The other is, issue the command "sys a: c:". This will transfer the boot files from the boot disk to the hard disk and make it bootable. I'd try that first. Another option is to run "fdisk /mbr". This an undocumented command which rewrites the master boot record. Reportedly, there are some risk involved, although I haven't ran into any. Issue the command and try booting to it. Once it is readable again, then deal with mounting it in Linux. 

It sounds like you are leaving W98 for good. If not, be aware that W98 still used the 8.3 filenames as well as long file names in the registry. Xxcopy ([www.xxcopy.com](www.xxcopy.com)) will preserve this format. The Windows copy utilities don't.

---

### Post by migla on 2007-01-11
> **RockinDolphin said:**
> I'm going ot have to say that I believe this is retarded. I feel like it should have been listed as 'File System2', or something. For an OS that's supposed to be so great, some people sure have made it a pain to get to learn.

From [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows) :
> In Windows, you were probably used to putting your files on a specific 'drive', like the 'C:' drive; your file might be stored in C:\My Documents\Work for example. Ubuntu has a different way of doing things - instead of having individual drives, everything is part of one big 'drive' called '/'. This might seem a little daunting at first - where can you find your CD drive, for instance?

Linux is different, but it makes sense once you understand it. I guess much work could still be done with automation, wizards and stuff to help out people who are used to windows or don't (like me) have the patience to read up on the basics before diving in. I do think it is so great, though.

(edit: fortunately, for me, ubuntu 6.10 automatically placed a shortcut to the windowspartition on my desktop)

---

### Post by RockinDolphin on 2007-01-11
Well, yeah. Someone said "/media", or something to that effect, but at the top of my post I said, "Assume I know nothing." Therefore, I didn't know what "/" referred to. If they had said "Computer/Media/etc..." I would have come a lot closer to understanding that. Folks need to remember that this is ABSOLUTE BEGINNERS FORUM and we need to talk baby-talk here until some of us catch on.

I was able to access my Win98 files with my WinXP drive. I've still got the WIN98 disk, but it wouldn't boot from the disk, for some reason. However, under WinXP everything still seemed to be there. I didn't try to repartition the drive, but when I clicked to unmount it because I thought maybe I need to try un-mounting and then remount, maybe something happened because there was nothing wrong with that drive when I pulled it. This machine was given to me and I forgot to ask for the disks. It's AMD 1GHz Duron and 7** something of RAM, so a better machine than what I had. I started having problems with losing my Ethernet card driver if I completely powered-down the machine. It had XP on it, but I had a 40gig drive on my old machine with all my stuff, plus it was 40gig, so I installed it on this machine. I kept having Linksys driver problems, so wondered if it was a registry problem, so re-installed the XP drive alone, but still had problems, so thought it might be a BIOS issue. I ran it for a while with XP master/Win98 slave until recently. 

'bought a new 120 Gig drive eight months ago and had a couple sources who were supposed to give me the 'hook-up' on legit XP Pro, but neither source came through and I was running out of drive space, so decided to try Ubuntu after reading about it on ZD Net. One of the reviewers was sort of a jerk with his questions and comments to someone who was a big part of Ubuntu and I thought the guy's responses were perfectly sound. I decided to try it and think I like it, it's just a learning curve.

'Wonder if XP did something to my Win98 drive. That's possible, I suppose. Anyway, I'm learning. I intend to get another big drive and put it in here, as well as more RAM. Then, I'll have TWO copies of the things on my Win98 disk and then just reformat that 40 gig disk and start over with it in a different machine, at some point.  

Thanks for the help!

~Kenny

---

### Post by RockinDolphin on 2007-01-11
Oh, I forgot to mention that I updated my BIOS and I think that fixed the problem.  Also, I'm sure it is set-up correctly for boot sequencing. It looks at A: first, then CDROM, then HD, then it has some other boot option. I don't know why it wasn't booting off my 98 disk. Once I duplicate my files and take other steps to protect what I've got, I'll revisit that problem and see what's going on. If I get the 98 disk to boot, again, may just leave it alone and put it in a stand alone machine for windows programs that I may not be able to run with Linux.

Also, someone said to use xcopy or something because directly transfering files from Windows might not work? Could I get more info on that, please? Thanks!

---

### Post by anaconda on 2007-01-11
Amazing that no-one gave you the easy instructions in howto mount your hdb1 -harddisk.
all you would have needed to do is to write in terminal

first create the folder whereto mount your win98 hd:
sudo mkdir /mnt/win98

And then mount it to that folder:
sudo mount /dev/hdb1 /mnt/win98

and you would be able to find your files from /mnt/win98  -folder
(might need "sudo nautilus" to get full admin rights to that hd..)

Well. anyway good that you found them already, and that it was already mounted (by who?).

By the way.. I remember how hard the mounting thing was when I was new to linux. It was the hardest thing to learn.. once you master it you can do about anything..

---

### Post by Patrick K on 2007-01-11
> **RockinDolphin said:**
> 
Also, someone said to use xcopy or something because directly transfering files from Windows might not work? Could I get more info on that, please? Thanks!

Not **xcopy** but **xxcopy.** Xcopy will not preserve the 8.3 filenames W98 uses. Go to [www.xxcopy.com](www.xxcopy.com) for more info.

Here is more specific info:
[http://www.xxcopy.com/xxcopy02.htm](http://www.xxcopy.com/xxcopy02.htm)
[http://www.xxcopy.com/xxcopy03.htm](http://www.xxcopy.com/xxcopy03.htm)

---

### Post by confused57 on 2007-01-11
[Quote=RockinDolphin]Well, yeah. Someone said "/media", or something to that effect, but at the top of my post I said, "Assume I know nothing." Therefore, I didn't know what "/" referred to. If they had said "Computer/Media/etc..." I would have come a lot closer to understanding that. Folks need to remember that this is ABSOLUTE BEGINNERS FORUM and we need to talk baby-talk here until some of us catch on.[/Quote]

Good point, and you're absolutely correct...it was one of my biggest issues when I was just starting out with Ubuntu & Linux.  I would ask a question on the forum and someone would post a code window with several lines of commands, I had no idea what to do with the commands...enter them one at a time or try to enter all at the same time.  Someone would tell me to change to my Home directory and save in such and such a directory, I was  clueless what they were talking about, only mounting I knew of concerned horses.  More experienced users trying to help tend to forget how foreign everything is to an absolute beginner...sometimes we have to be reminded.  From what I've seen, you're picking things up much faster than I did...I was hesitate to ask  someone to explain a little more clearly what I needed to do, my mistake, because people are more than happy to explain things in more detail.

---

### Post by RockinDolphin on 2007-01-11
Okay. I'm still stupid. I looked at the xxcopy website and it seems to be for Windows? Will it run on Linux, or am I supposed to load it on the '98 drive and then transfer files from the '98 drive to the Linux drive? Remember, I'm having problems booting from the '98 disk, now, so would prefer to run things from the Linux end. 

Thanks!

---

### Post by confused57 on 2007-01-11
If you're using Dapper, you might be able to access your other drive from the GUI...someone in this thread was able to do so:
[http://ubuntuforums.org/showthread.php?t=333689](http://ubuntuforums.org/showthread.php?t=333689)

Basically, you'd go System---Administration---Disks, find your Win98 drive & partition,
change the mountpoint to **/mnt**, click on "Enable" ,  then click on "Browse".

Edgy doesn't have the "Disks" option.

---

