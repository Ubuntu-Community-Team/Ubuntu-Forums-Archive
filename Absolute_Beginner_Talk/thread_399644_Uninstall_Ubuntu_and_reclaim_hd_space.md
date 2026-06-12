---
title: "Uninstall Ubuntu and reclaim hd space"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-04-02
I am currently dual booting with XP.
I want to uninstall Ubuntu and use the partition for XP.

i have an 80 gb hdd divided into two equally sized partitions for XP and Ubuntu.

How do i uninstall Ubuntu and use the space for xp?

---

### Post by oilchangeguy on 2007-04-02
boot into windows, go to the control panel. click on admin services, computer mgt., disk mgt. locate the partition that has ubuntu, right click on it (not sure of the exact option list) and delete/format it. then make it an active partition and assign it a drive letter. i don't think you can reclaim it as part of c: without having to reinstall windows.
also you'll probably have to fix the master boot record. and this can only be done with a windows disc, not a factory restore disc.

---

### Post by dannyboy79 on 2007-04-02
gparted on the live cd can grow your NTFS partition just like it shrunk it! Simply boot your live cd, gksudo gnome partition manager. THen just right click on your ubuntu install and click delete. Then right click on your windows partition and say grow or make larger or whatever it is and then hit apply at the top and it should do it's job!! gparted is an open source copy of Partition Magic. Obviously it's up to you whether or not you want to back up your critical info but according to the documentation it is possible!!!!!

check it out here: [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

if you're scared, you can always use part-image to first back up your windows partition but before you do that make sure you defrag your windows partition and make sure you're not using compressed system files. From part-image website:

The NTFS (Windows NT File System) is currently not fully supported: this means you will be able to save an NTFS partition if system files are not very fragmented, and if system files are not compressed. In this case, you will be able to save the partition into an image file, and you will be able to restore it after.

Most people don't even know what that is, it's for people with small hard drive, you can chose to compress your system files which makes your OS run alittle slower due to having to uncompress them when they need to be accessed but most likely you don't have compressed system files. You can find out by right clicking on your C drive within windows and going to the properties dialog, you should see a check box at the bottom that ISN'T checked. This means that your c drive is not compressed. Then double check the same thing on your Windows folder within Windows Explorer, right click, go to properties and do under advanced and make sure "compress contents to save disk space" isn't checked. Then you're safe to create an image of your windows partition and backit up onto dvd or cd to be on the safe side. don't forget to split the image if you're going to be burning it to discs!!!
screenshots of partimage to netowrk location into smaller files.
[http://www.partimage.org/Screenshots](http://www.partimage.org/Screenshots)

let us know how it went.

---

### Post by panti19 on 2007-04-02
i deleted the ubuntu partition from the disk management utility and made a quick format (ntfs)

When i restarted win will not load, giving me a "Grub error 17" or something like that, it seems i have to get rid of GRUB as well.

i tried using the recovery console on the winxp cd : fixboot and bootcfg and still i get the same error 17.

i am now in ubuntu (live cd) and using GPARTED i deleted the newly made partition and resized the C partition to fill the entire HDD, however, i got an error saying that one operation did not complete successfully because hda1 couldn't be resized to 74.53 GB, but after hitting ok, the drivers appear as i want them. One partition to fill the entire HDD.

rebooting to see how it goes..

---

### Post by ajgreeny on 2007-04-02
Try using fixmbr in the windows recovery console, not fixboot.  You need the mbr restored not the boot sector, if my understanding is correct.

---

### Post by dannyboy79 on 2007-04-02
it's not going to work!! you have to obviously remove grub and restore the mbr so that it has NTLDR in it. Here are the instructions for that:

Put your CD of Windows XP and run the installation from it. In the first screen choose the option Repair from the console command. It may ask which Windows install you want to repair, just enter 1 (or is it zero?), if it asks for the admin password, hit enter without entering anything (unless you do have one)  You will arrive to the typical MS-DOS console, then use the command FIXMBR and you'll start your windows normally again. This is only if you have 1 hard drive, careful if you have more. U can use the map command to find out the different drives in your computer

---

### Post by freebird54 on 2007-04-02
Even a Win95/98 "system" disk will do the job on your mbr.  Somewhere a friend has one lying around, I'm sure.   Just boot from the system disk and:

```
fdisk /mbr
```

and it'll pick up XP from there..

---

### Post by oilchangeguy on 2007-04-02
if you can't find/don't have a 98 boot floppy go to [www.bootdisk.com](www.bootdisk.com) and create one.

---

### Post by panti19 on 2007-04-02
i used fixmbr and i now can boot into windows but i get a stupid thing in disk management , take a look
(i named the drives: 15GB-local disk and 80GB-media, previously, don't be fooled by that) :D

[http://imghost.evonet.ro/show.php/778_wha.JPG.html](http://imghost.evonet.ro/show.php/778_wha.JPG.html)

i obviously don't get the extra space (74 - 15)GB.. 
i should be able to see it as unallocated, but it shows in the bottom window as part of C and in the top view ,it says C is only 15 gb

---

### Post by oilchangeguy on 2007-04-02
assign it a different drive letter. something that's not normally a cd drive etc. and re-assign D: to your cd drive.

---

### Post by panti19 on 2007-04-02
i can't assign the C drive another letter

---

### Post by oilchangeguy on 2007-04-02
i was talking about the 80gb D: media drive.

---

### Post by panti19 on 2007-04-02
nope. didn't help.
still my 60 GB are nowhere to be seen.

---

### Post by WelshChris on 2007-04-02
I'm going off on a tangent here, but someone suggested using a Win98 disk and fdisk /mbr.  If this guy has ntfs disks, would that still work?  I thought using fixmbr in the recovery console was the way to go.

---

### Post by panti19 on 2007-04-02
i don't have a floppy drive..:confused:

---

### Post by panti19 on 2007-04-03
i entered gparted using the live cd and the C drive is shown filling the entire drive, while windows shows a different story.:confused:

---

### Post by dannyboy79 on 2007-04-03
what is the question here? you have an 80 gb hard drive and another 15 gb hard drive. you can't combine the 2!!!!! you're never going to get 80gb within XP. due to NTFS overhead. I have a 120gb hard drive and it only formats to 111 NTFS so everything is fine. It appears as though you don't even know you have an extra drive OR you're not telling us something. (i am not saying that you're not telling us something on purpose I am just saying this is NOT adding up!) If they were the same disk, they wouldn't say DISK0 and DISK1, right?!?!?!?!?

and your quote, "i obviously don't get the extra space (74 - 15)GB.." Think about what you're saying, you want an 80gb hard drive to equal 89gb, well that will never work! :-)

So it clearly shows you have 2 disks!

---

### Post by panti19 on 2007-04-03
I have a hard drive with 80 GB capacity.
i used to dual boot with Ubuntu. Back then, i had 15 gb reserved for XP and the other for Ubuntu.
Now, after deleting the Linux partition and reformatting it NTFS, using fixmbr and then resizing the 15 GB partition to fill the drive with Gparted to fill the drive. and now , in XP i am forced to use only 15 gb of space  instead of 80gb. that's my problem.
The extra space doesn't even show up in Disk Management under Windows, instead it showing a contradiction in the sense that in the bottom view, the C drive is shown with an 80gb capacity and in the top view, the drive is shown having only 15 gb.
The extra space doesn't show as unallocated and not even as another partition.

It's true, i also have another 80 GB hard drive which i use for media storage, but it's not the case with it right now. I can access it now ( and could before deleting Ubuntu) via XP and i could via Ubuntu.

---

### Post by mikeyphi on 2007-04-03
I suggest you get access to a windows type disk management program, something like partition magic, which will interact with your windows setup and tell windows to use the whole space.

---

### Post by panti19 on 2007-04-03
partition magic is not free :(  is there a free alternative?

---

### Post by Terl on 2007-04-03
Put in the ubuntu disk and start to install.  When you get to the disk partition part selct the one that lets you decide how to partition.  This will open gparted.  Select the portion of the drive that used to have ubuntu.  Format it as ntfs.  When it is done, cancel the install.  Shutdown ubuntu and restart the pc.  Since you did not install anything, just reformatted a drive, you will boot back into windows.  The extra space should now show up as a NEW drive.  You can't just merge it back into the C without reformatting the entire drive.

---

### Post by dannyboy79 on 2007-04-03
yes you can, the problem is that the partition table isn't getting updated by gparted. here's what to do. hang on, I have already helped some1 with this. buit I need to find the thread. what we had to do was use a tool to recreate your partition table and it does NOT overwrite your data, it merely creates a new partition table then it'll show up. don't worry. i'll be right back!

---

### Post by freebird54 on 2007-04-03
Just answering the tangent here - the mbr is only 512 bytes, and is filesystem agnostic.  Using old mbr restores works up through XP problem-free - I have no experience with Vista - but it would probably do there too.  All the mbr holds is a partition table and code to point to a loader (which then loads the filesystem - such as NTLDR)


Back to the main point - it appears that the resize did not work fully.  One solution would be to shrink again to where it was, and create a NEW partition (and drive letter) that Windows DOES recognize and use the space that way.  Another would be to try again - making sure that everything completed.  Another would be to return it to 15 Gb and try one of the alternative 'resizers' out there - Partition Logic comes to mind, or the Super Boot DIsk CD.  These, and others, can be found by searching such places as the ZDNet and TechRepublic dlownloads for Windows - or by Googling them.  Hope that helps!

---

### Post by dannyboy79 on 2007-04-03
did you maybe mean the **Ultimate** Boot CD, it's got every tool you could ever want, all for free!!! [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

---

### Post by 2windermere on 2007-04-03
Sorry to hi-jack the thread, but didn't want to start a new one.

I'm selling my laptop so need to get rid of dual boot. It has windows installed on C: and has ubuntu installed on D: partion along with a 30GB partition with all my music and stuff. Would it just be a simple case of formatting the Ubuntu partition and using partition magic or something else involved?

---

### Post by freebird54 on 2007-04-03
That SHOULD be all that it is involved - but this thread seems to be about an exception to that rule!  (those darn exceptions).

And, yes dannyboy - I meant the Ultimate Boot CD - didn't work for me (failed to start up) , but has a good rep out there.  Certainly has all the tools you'd ever need!

---

### Post by dannyboy79 on 2007-04-03
> **2windermere said:**
> Sorry to hi-jack the thread, but didn't want to start a new one.

I'm selling my laptop so need to get rid of dual boot. It has windows installed on C: and has ubuntu installed on D: partion along with a 30GB partition with all my music and stuff. Would it just be a simple case of formatting the Ubuntu partition and using partition magic or something else involved?

untill the main person who posted this solves his issue trying the various tools I have suggested to rewrite his partition table which should solve this since windows disk management is readin the partition table. you are probably best off just booting into windows, then delete the ubuntu partition thru disk management, then reformatting it to ntfs or fat32 and telling the preson you're selling it to that you created a seperate partition for backup purposes or for critical data in case the main c drive goes haywire. otherwise, if you are going to try to resize you ntfs parition, use the latest gparted live cd you can find, don't use an ubuntu live cd since I am not sure what version of gparted is on there. it should work. or you could always just reinstall window xp and reformat the entire drive since you are getting rid of it. or is this going to some1 who wants all the software and stuff you ahve installed on it? good luck with what you decide and if you do use the latest gparted live cd, use this one ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) and let us know how it went. PLEASE. you would be a guinne pug for many people and i'd give you the full credit if you try this. i am going to try it myself but I have to setup the test drive first.
heck, to be on the safe side you could use the GParted-Clonezilla LiveCD they just released also. which would back up your entire disk first. AWESOME.

---

