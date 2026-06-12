---
title: "Issues Uninstalling Ubuntu"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Djinn Effer on 2007-07-10
Alright... I'll give a little background info first: A month or so ago I decided I'd try Ubuntu out, which that was all good and fine... It's not a serious option right now though since 99% of what I do on the computer is done with programs that aren't even working on Wine (or the paid equivalents) yet. So, I figure having a safer OS but not being able to do anything I need to do doesn't get me anywhere.

So, I decided I'd uninstall to use the drive for something else for the time being so I could just use XP which I'm familiar with and all of my programs work on, and everything would be fine. Which, that last part's kind of funny and ironic if you keep reading.

Alright so, this is what I started with **before** putting Ubuntu on my computer:

A C:/ drive which Windows XP Pro is installed on which has it's own drive. Then there was D:/ which was used for Backup, E:/ which was all of my programs and other things of that nature, and F:/ which is all of my movies, music, etc. D & E are both on the same drive, it's just partitioned, F is it's own drive. (One 120 GB master hd then two 250 GB slaves.)

Right, so... I moved everything off of my D: Backup drive, which there was only a couple MB on it, not too important and that's where I installed Ubuntu. Made a /, SWAP and /home/ on it.

Anyways, so today I went to uninstall Unbuntu and read all about it so I wouldn't mess anything up. (haha?) Since I'm not particularly the queen of computers over here. So, from reading I find out that if I'm going to uninstall a Linux distro it loads in GRUB, which I've seen GRUB load every time my computer starts, with the Stage 1.5, Stage 2, blah blah pick what you want to run, etc. I even understood that it was just a little file that pointed to something on a bigger hd which told it what to use to boot. So, I found the easiest way to change my MBR (since I've lost my XP cd) would be to download [Super GRUB](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) and put it on a CD and get that all sorted out. I did, and that all went smoothly. Rebooted the computer after that and it went into XP no problem, everything was fine up until that point.

So,  that was Step 1 of the guide, the "hard part" - now I'm at the "easy part" of the guide, Step 2, so it says. Ahem: "Deletion of the Linux partition is really the easy part. You can use any partitioning software for that.  Just delete the partition." Alright, so this is going to be easy! I jump into the XP Disk Manager and go to delete the Ubuntu partitions, and I'm really paranoid when I'm doing this to make damn sure I clicked on the right ones. So, I click on one of them, the one that was the root partition for Ubuntu and right click, delete partition. I get some error, says I need to close Disk Manager and open it again or restart my computer. So, alright... That's weird, I close the Disk Manager and when I get back to it something looks different, that partition seems to be gone though, so I guess it worked. So I then go to delete the /home/ partition on there, right click, delete logical drive. I get the same error **again!** So, I close out of Disk Manager and open it back up, right click on the same partition that's still there and try again. Close Disk Manager, cause at this point all I need to do is delete the SWAP then I can partition all the free space.

Well, damn if I'm going to do that. When I get Disk Manager opened back up, not only do I not see what happened to / and /home/, but **the entire disk** no longer shows up. Like it just up and vanished, as if I unplugged it from my computer or something. Which, I obviously didn't. So, I'm a bit worried at this point. My E: drive was really important, so the entire disk disappearing is **really** bad. So, I close the Disk Manager and open it back up and see if I can see it. I try to go to Action -> Rescan disks to see if that'll pick it up, and no that doesn't work.

So at this point I'm wondering what the hell happened, how does a disk just up and disappear? I go looking around E: and see "okay, everything's still there... Thank god." checked a couple of files, a couple of programs, everything was fine, just the entire disk wasn't showing up in the Disk Management, so I decide I'll just reboot and maybe that'll fix it. Uh, well no... No, not quite.

When I reboot the E: drive pulls a Houdini on me and just vanishes. Nowhere to be found, the drive isn't even detected in the Disk Management now. So... The only thing I can think to do is look in the error logs to see if I can see those errors again. Well, there's about 100 of these lil things:

The driver detected a controller error on \Device\Harddisk1\D.

For more information, see Help and Support Center at [http://go.microsoft.com/fwlink/events.asp](http://go.microsoft.com/fwlink/events.asp).

0000: 03 04 68 00 01 00 b6 00   ..h...¶.
0008: 00 00 00 00 0b 00 04 c0   .......À
0010: 03 01 00 00 85 01 00 c0   ....&#133;..À
0018: 00 00 00 00 00 00 00 00   ........
0020: 00 00 00 00 00 00 00 00   ........
0028: 15 a9 00 00 00 00 00 00   .©......
0030: ff ff ff ff 04 00 00 00   ÿÿÿÿ....
0038: 40 00 00 00 00 00 00 00   @.......
0040: ff 20 0a 12 4c 03 20 00   ÿ ..L. .
0048: 00 02 00 00 0a 00 00 00   ........
0050: 00 90 20 85 70 7b 22 85   . &#133;p{"&#133;
0058: 00 00 00 00 b0 1a 08 86   ....°..&#134;
0060: 00 00 00 00 c2 a7 09 6f   ....Â§.o
0068: 28 00 6f 09 a7 c2 00 00   (.o.§Â..
0070: 01 00 00 00 00 00 00 00   ........
0078: 00 00 00 00 00 00 00 00   ........
0080: 00 00 00 00 00 00 00 00   ........
0088: 00 00 00 00 00 00 00 00   ........

So, that leads to this: [http://support.microsoft.com/?kbid=245725](http://support.microsoft.com/?kbid=245725)

"How To Recover an Accidentally Deleted NTFS or FAT32 Dynamic Volume" WHAT THE ****?

Right so, looking at the instructions on that page, I can see that it wasn't exactly made very user friendly:


To Recover a Deleted NTFS Volume
1.	Re-create the exact same volume but choose not to format it. This may be difficult if you do not remember the exact size you had created originally, especially because the Disk Management snap-in tends to round partition sizes.
2.	Using Dskprobe.exe, recover the backup boot sector for the NTFS volume from the end of the volume. Because it is a dynamic volume you may need to use Dmdiag.exe to help find the backup boot sector, or search for it by using Dskprobe.exe (on the Tools menu, click Search Sectors).
3.	After rewriting the NTFS boot sector, quit Dskprobe.
4.	In Disk Management, click Rescan Disks on the Action menu. This should mount the volume for immediate use.


Yeaaaah... Can't even do step one, I have no idea how big my E: drive was, and it's kind of hard to recreate a volume when it doesn't show the free space, since the entire disk disappeared.

Sorry for such a long winded thing... Anyone have any idea what on earth happened and/or how to fix it?

---

### Post by wolfen69 on 2007-07-10
i used hirens boot cd, and a program called "getdataback-ntfs" or something similar. worked like a charm. (strictly for evaluation purposes only)

---

### Post by anewguy on 2007-07-10
If you still have an Ubuntu LiveCD (assuming that's what you installed from), trying booting up with it and see if you can find the drive.  I'm just a beginner myself, so I would have to just "play" with it in Ubuntu until I could see the drive, but I think you could do it with parted or qtparted.  I think when you boot from the LiveCD you can just open a terminal window and type "parted" and go from there.  QTparted uses a graphical interface but I don't know if it comes on the LiveCD.

Good luck!:)

---

### Post by Djinn Effer on 2007-07-10
> **wolfen69 said:**
> i used hirens boot cd, and a program called "getdataback-ntfs" or something similar. worked like a charm. (strictly for evaluation purposes only)

Any more info about that...? I googled hirens boot cd and found their site: [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) but there's apparently no download link there, but in [wikipedia](http://en.wikipedia.org/wiki/Hiren's_boot_CD) it says that they removed the iso because it contained warez or something.

**Edit:** Ahem... I found out where to download it, but LOL... How funny. I download it then realize that it's kind of hard to use Nero to burn it when Nero was on the drive that disappeared. Oops.

**Edit2:** Downloaded some freeware ISO burning software til I can get my disk back, running GetDataBack-NTFS right now from Hiren's.

---

### Post by wolfen69 on 2007-07-10
burn it in ubuntu.

---

### Post by Djinn Effer on 2007-07-10
So um.. With GetDataBack, you can't actually recover the disk itself, just copy the files to another drive..?

**Edit:** Right now I'm copying my files from the "deleted" disk with GetDataBack for NTFS. It looks like I'll be able to get the files, but I'm still a bit unsure what happened to the disk itself and how to get it operational again.

---

### Post by Djinn Effer on 2007-07-10
Hmm... Ok. Apparently I can get all of the files but none of them work.

---

### Post by Djinn Effer on 2007-07-10
Alright so, question... When I used Super GRUB could that have somehow messed up the boot sector for the other drive, and when I went to remove partitions from it that's why errors occurred and why it disappeared after the restart?

Speaking of which, anyone have any ideas on how to fix it? Every file I managed to "save" with GetDataBack is apparently bad - jpgs come up as No File Preview, programs don't run, movie files fail to render, etc. So, that approach apparently doesn't work.

At this point, if it is something in the boot sector causing the problem, is it even possible for the data to still be recovered since the recovery tool could only get them as non-working files?

I figured I might be able to fix my problem with something like Partition Magic, but I get errors when I run it. :/.. (Init Error: 11117)

---

### Post by Djinn Effer on 2007-07-10
Alright, just an update: I ended up booting from Hiren and using Active Partition Recovery 3.0 to fix it, got everything back. ^_^

---

### Post by Herman on 2007-07-11
Hello Djinn Effer,
I'm sorry to read that you had trouble but I'm happy that you recovered all your files. Well done!

I think the problem came from mixing different partitioning softwares. Windows Disk Manager is probably okay if you only use it and not any other partitioning software. 

I tried it out myself a few times a long time ago when  I decided to go try our all the different kinds of partitioning softwares and install some different Linux distros just for fun and to try out lots of different ways of doing things. I gave myself the same problems as you had, a 'borked' partition table! I cannot say for sure which partitioner was to blame because I had tried out a whole coctail of different ones.

What I think happened is maybe different brands of disk partitioners do pretty much the same job but maybe they have slightly different ways of doing some of the finer details. 99.999% of the time they get along with each other okay, but sometimes the disc partitioning software you are using now finds something your previous disk partitioning software wrote in the partition table that it doesn't quite understand, or it doesn't quite agree with. If the partitioning software isn't smart enough to realize it's trying to do something it doesn't understand it might try anyway, and that's how the partiton table gets 'hosed'. The Linux (Parted based) disc partitioners will just refuse to show the partitions or they will refuse to do anything if they 'see' something they don't like, so they are safer.
I'm only guessing all this, there is still lots I don't know yet about partitioners and partition tables, but that's the way it seems to me. Ever since I decided never again to mix different brands of partitioning software, I have never had anymore trouble ever again. I always stick with the 'Parted family of partitioners now, Partman, GParted, Parted, QTParted, and Gnome Partition Editor.

There is always a slight risk whenever we run any disk partitioning software anyway. There are no brands of disk partitioning software whose webpage doesn't say 'Please make a backup before you use this disc partitioning software.'

Once again, I'm sorry this happened to you. It sounds like it might have been my web page you were reading about how to uninstall Ubuntu. I need to edit that web page so as to reduce the likelihood of that happening to anyone else.
I think maybe I should change it to read 'delete the partition with the same software you created it with', and, 'make a backup before using disk partitioning software'. What do you think?
Thanks for posting this thread, at least now I know I need to fix that page, and once again. I apologize for all the inconvenience you had to go through.

Regards, Herman

---

### Post by Djinn Effer on 2007-07-11
That makes sense, since I made the partitions with the Linux install software, whatever that uses. I have to say, I was completely lost as to why it happened. I really never dreamed of it happening :P It possibly has something to do with Windows not knowing how to deal with ext3 and swap file systems perhaps? *unsure*

> Once again, I'm sorry this happened to you. It sounds like it might have been my web page you were reading about how to uninstall Ubuntu. I need to edit that web page so as to reduce the likelihood of that happening to anyone else.
I think maybe I should change it to read 'delete the partition with the same software you created it with', and, 'make a backup before using disk partitioning software'. What do you think?

Ah no hard feelings. Yep, it was your site's guide that I found, pretty great guide minus the whole disk disappearing fiasco -- which I don't hold you responsible for at all.

I'd definitely recommend making a backup, but most people will ignore that, like myself, thinking "Ohh that won't happen to meeee..." xD... But yes, that's definitely good advice, though I would be a bit more clear on using the same software part. Probably explain if they created it with the Ubuntu install that it really used whatever software (Whatever software the install software uses, I have no idea.) and possibly a mini guide on how to do it for the less advanced folk. Though, I wouldn't particularly go into detail with any other partition managers, just the default, since it's probably the most common.

I do have some more info you could add though! After I got the errors and the disk disappeared from Disk Management, I could still access the disk itself via My Computer, the browser, etc. just fine, along with all the files, *until* I restarted my computer. So, make it clear that if they do risk doing it that way that if these things do happen to them they should stop immediately and make sure they back up their data on the drive before restarting.

Maybe include a really small mini guide for how to run Active Partition Recovery 3.0, as I kind of stumbled upon it cause Partition Magic gave me a critical error and I was at last resorts at that point. Basically, you just boot into the software then click the disk that the "lost" data is on, then click whatever it says on the screen to do an extended search, I believe it was ctrl+enter. After that, it takes an hour or two to finish searching, probably depending on how much is on the drive. Then let them know that they can browse around and such... But I'd probably add a little bit about the "Esc" key's function. I had **no idea** what I was doing, and when I was completely giving up and just hitting Esc out to try anything else it came up asking if I was happy with the results of the discovered data and would I like to write them to the disk. So then it does that then reboots and it's fixed. Though, if you were deleting a Linux partition, I think it might possibly recover that as well, so you might want to empthesize how to do it the right way after you've gone through that. Actually, I have absolutely no idea if the Linux partitions are still there, but the partition I originally formatted to install Linux (D) is back, although it says it isn't formatted. I'm a bit skeptical over formatting it though, as you might imagine. ^^

---

### Post by Herman on 2007-07-11
Thanks for replying, Djinn Effer.  I think probably it will be relatively safe to do whatever it is you want with your hard disk and partitions now. :)

I don't imagine it would be possible to reproduce the same error again if you spent all your time repartitioning your hard disks for the next several years, if it was an error that was easy to reproduce you could find out the exact details of it and alert partition editing software developers, (submit a bug report), and they would look into it. If it is a problem with free software partitioners, (Parted), they will probably fix it right away.  

I already tried that when it happenedtome, but I couldn't get the same thing to happen again, no matter how many times I tried, so I still don't know exactly what the problems was.

Something I will try to do later as soon as I get time is make a forum search and a google search for similar types of problems and try to collect some data that way that I might be able to make some crude statistics from. I doubt even then if it would be possible to pick any pattern to hard disk partition tables getting corrupted.
That's something you or anyone could help with if you have time.

Think about it this way, it's a little bit like driving a car, everyone knows driving a car is dangerous. Lots of people get injured driving a car but most people still do it because they want to get somewhere and they are in a hurry. If you just had a car accident you would be a bit scarred for a while but most people still drive a car again sooner or later. Parttitioning hard disks is a lot safer than driving a car. Not very many people report a corrupted partition table, but there are car accidents all the time. I think it's okay to just remind people to back up their data before using disk partitioners, )and most of the time people get away without needing to do that). :)

I will look into Active Partition Recovery 3.0 too, thanks for that info. 

...I'm late! Gotta go --> bye!

---

### Post by Herman on 2007-07-12
Hello, I'm back,
> That makes sense, since I made the partitions with the Linux install software, whatever that uses. Ubuntu uses either Partman in the 'Alternate' CD, or Gnome  Partition Editor, which is a special version of GParted. 
Those are based on [GNU libparted]("http://www.gnu.org/software/parted/"). Also based on [GNU libparted]("http://www.gnu.org/software/parted/") is the KDE partitioner, QTParted, and the text based Parted. All of those are very good partitioners that I use all the time and should be compatible with both Linux and Windows operating systems, and most other operating systems too, probably. Any of those should be okay.

I just started googling to try to find out how rare or common this type of problem could be but before I got very far I found this interesting site, which I have read before, but now re-read with more interest,  [Partition types Andries Brouwer, aeb@cwi.nl 2007-01-01]("http://www.win.tue.nl/%7Eaeb/partitions/partition_types.html#toc1")
Here are a couple of interesting bits,
> The Windows NT Disk Administrator will corrupt your disk when it writes a signature on a disk with two or more logical partitions. See [Disk Administrator Corrupts Partitions]("http://support.microsoft.com/support/kb/articles/Q135/3/08.asp").( I don't really think that directly applies to your situation though),
and,
> Software or firmware that implements the above minimal specification will be able to handle all DOS-type partition tables written by a single version of the fdisk-type software of the common operating systems. (Using fdisk-type software from several operating systems on the same disk may create a terrible mess.)I still think it's rare these days for anyone to run into this much trouble though, but I'm looking into it.
Regards, Herman :)

---

### Post by TaoWanderer on 2007-11-20
I had an XP home and Ubuntu dual boot installation and I tried to uninstall Ubuntu by following this guide:  [http://users.bigpond.net.au/hermanzone/p18.htm]("http://users.bigpond.net.au/hermanzone/p18.htm"). 

I did the first step successfully and restored the windows boot loader with FIXMBR.

The second step however didn’t go so well.  I used gparted on the Ubuntu Live CD to delete the Linux partitions but when to tried to resized the Windows NTFS partition from 37 GB to 75 GB it came up with an error.  However when I rebooted and when back into gparted it appered as though it worked and showed the NTFS partition as being 75 GB.  Though when I restarted into windows and checked the c: drive in My Computer it still showed the size as 37 GB.  Though when I check the size in windows Diskpart it shows the size as 75 GB.

What am I doing wrong?

I don’t have to reformat after resizing, do I?

---

### Post by Herman on 2007-11-20
HelloTaoWanderer,
You aren't doing anything wrong, 
It seems as if there is a problem there somewhere in your NTFS file system probably. 

The best thing to do is make a backup of your data right away if you haven't already done so.

What's wrong exactly, I don't know, I will only be guessing, but I'm guessing that your partition was resized but the file system inside the partition did not get resized.

The size of the partition is determined by the code in your partition table in the MBR. So if a program looks there and reads that, it will tell you your partition is now 75 GB, and that would be correct.

The size of the file system inside the partition is determined by 'metadata' in the file system blocks at the start of the partition. So if a program looks at the file system block (in Linux it's called a 'superblock'), and reads the information there and reports the file system size as 37 GB it is probably correct.

I'm guessing the GParted is reporting the information it's reading from the partition table, but DiskPart is reporting the information it's reading from your file system superblock.

Normally the partition editing programs quietly resize the partiiton and resize the file system for us right afterwards if the partition was enlarged, or before-hand if the partition is to be made smaller.
This time it looks like GParted tried to do it but saw something in there it wasn't sure was right and didn't take the risk, it failed on the safe side and left your file system as it was to avoid risking your data.

How to fix it?
Well, this depends on exactly what the problem is. You should back up your data to be on the safe side.
Then first, we gather all the information we can.
I will start for you, GParted uses a program called nyfsresize to resize NTFS partitions and file systems, here's the Wikipedia page about ntfs resize, [http://en.wikipedia.org/wiki/Ntfsresize](http://en.wikipedia.org/wiki/Ntfsresize), and from there I have found ntfsresizes' home page, [http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php).
Here is ntfsresize's web forums, we can do some research there first and if we don't see anyone else with the same problem and an expert solutuion which was reported to have been successful we could sign up to that forum and ask for expert help there.

Here is GParted's home page, [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/), we can read their FAQ here,[ http://gparted.sourceforge.net/faq.php]("http://gparted.sourceforge.net/faq.php"),  and their documentation here, [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php).
GParted's web forum is here, [http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/).

I don't know how much of a hurry you are in. If you want to be safe and you can wait some time I will do some reading for you and check to see if the answer I want to give you will agree with the answers given by the experts and if they  solved the same problem successfully already for someone else, or you can find out for yourself from the links I have just provided.

The answer I want to give you is to try a file system check first and then try resizing the file system again. 
A file system check should fix the problem and then the file system resizer should be able to proceed safely. However I think NTFS would already have run the file system check automatically for you before and maybe again after the resize operation. You might run a deliberate file system check or chkdisk to make sure and then try resizing again and hope you'll be lucky this time.
With luck that should solve your problem. Just make sure you do make a back-up first because sometimes these problems get worse the more we try to fix them. It depends on exactly what's wrong, which we don't know for sure.

I'll be back in around twelve hours to see if anything has happened, and I'll have more time to help you more then.

Regards, Herman :)

---

### Post by TaoWanderer on 2007-11-20
Thank you so much for the reply.  I ran the check disk and played around with gparted and resizing the partition and found that if I made it 1 MB less than the max it worked and reconginzed everything correctly.  Strange problem, but thanks again for the help.

---

### Post by Herman on 2007-11-21
Okay, I'm glad you got it fixed. Thanks for posting in this thread. It might help someone else.
That is a strange problem. :confused:
Anyway, I'm glad you were able to fix it easily.

All the best,
Regards, Herman :)

---

### Post by mozetti on 2007-11-21
In regards to both people that encountered problems:

1) Djinn Effer - The Disk Manager utility in Windows isn't a proper partitioning utility (IMO). In my experience, the way it works assumes that you're going to be using Windows FAT32 or NTFS filesystems only. So, as a partitioning tool for a strictly-windows environment, it's satisfactory. IMO, that's where your problems came from.

2) Tao - Similar to my above comment, because MS has locked down the NTFS filesystem other OS's have trouble working with NTFS. For the most part, Gparted can do simple tasks related to NTFS drives but re-sizing a partition isn't a "simple" operation, even though it may seem so.

My advice to both of you, and others attempting to do the same things is:

Use the tools appropriate to the filesystem/OS you want to manipulate. To format/delete/work with Linux filesystems, use linux-based partition tools. To format/delete/resize/work with Windows filesystems, use Windows-based partition tools. This mean that you'll need to use two different partition tools when working with a dual-boot system, but it's the safest way to avoid problems.

Glad you both got sorted, and hopefully **Herman's** great advice (in my experience, he gives the best help) and my little addition can save future users your headaches. :)

---

### Post by deadw8 on 2008-07-22
my friend (moved away) installed Ubuntu for me, praising its worth and ive always been fascinated by Linux. 
Anyhow, there are some errors in my feisty fawn and paradoxically im not able to go online because of these errors to download an automatic update which would fix them. 
So i want to uninstall and use XP to write my scripts. I have an XP cd rom but thats all. No floppy and dont want to burn any CDs. is there a while, all i know how to do is press ESC before the GRUB (???) counts down. I dont even know if anyone can help someone as hopeless as me...

---

### Post by Herman on 2008-07-22
:) Hello
Here is a link to my 'Uninstall Page', [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"), there's a explanation there about how to uninstall Ubuntu. I hope you'll find everything there simple to understand.
The main thing it to change the MBR back so it will boot Windows, the page I just linked you to gives a whole list of different ways you might be able to do that. Hopefully at least one of those methods will be easy for you.
Regards, Herman :)

---

