---
title: "Help needed setting up Dual boot XP/Ubuntu"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by Alexandrian on 2006-04-08
I've been following the install guide at [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

When I get to the stage of manually editing my partition table, I see that I have Windows XP taking up 80 GB with 8.2 GB of free space.

I tried to resize my Windows partition to 65.0 GB (the step at 12th ntfs) it does not go to the next screen of resizing the partition, rather it goes to a blank blue screen and then kicks me out to the main partition menu. Any ideas what could be wrong here

I also tried creating a partition out of the extra 8.2 GB of free space, but when I tried to format it to Fat32 I get a message saying it failed.

Thanks

---

### Post by garner_nc on 2006-04-08
Looks like you're trying to resize an NTFS file system. I don't think this is possible with the tools you're using. Linux support for NTFS is not stable.

All the Best,
Doug White

---

### Post by Alexandrian on 2006-04-08
[QUOTE=garner_nc]Looks like you're trying to resize an NTFS file system. I don't think this is possible with the tools you're using. Linux support for NTFS is not stable.

All the Best,
Doug White[/QUOTE]

In the FAQ I linked to, it says you can resize the Windows NTFS partition just by putting in the Ubuntu Install CD. If it indeed isn't possible to re-size the Windows partition, and I can't install Ubuntu with the CD on the 8.2 GB free space, is there anything else I can do get the dual boot set up?

---

### Post by aysiu on 2006-04-08
[QUOTE=garner_nc]Looks like you're trying to resize an NTFS file system. I don't think this is possible with the tools you're using. Linux support for NTFS is not stable.[/QUOTE] No, Ubuntu's installer can resize NTFS.

The only thing that's not stable is writing to (i.e., modifying, deleting, and creating files on) an NTFS partition.

---

### Post by Herman on 2006-04-08
Hello, Alexandrian, 
 The partitioning software that comes with the Ubuntu installer has been used by thousands of people by now to resize NTFS partitions quite successfully. However, it does occasionally fail on the side of safety if there is something it detects that is is not sure about.
The oldest Ubuntu version, 'Warty' could not handle NTFS so well, but that is almost ancient history by now.

Commonly there is a block of Windows data in the way and Windows just needs more defragging to consolidate the Windows data to the beginning of the disk. 

Other than that some sata drives have problems that I don't know anything about, but it does not seem to be related to NTFS. I'm only another user trying to be helpful, not a developer or engineer, so I can't offer you any insights into that.

You could try defragging Windows more, or, try using the latest GParted livecd to do the partitioning as it has the cutting edge technology and can defrag Windows and resize it for you in one operation. (Click my right-hand sig link).

I believe it is a good idea to stick with the 'Parted based family of partitioners as the installer's partitioner is 'Parted based. QTParted is okay too. The 'Parted based partioners are more likely to be compatible with each other and not cause a conflict in your partition table. Partititon Magic is not recommended for mixing with Linux partitioners, but lots of people get away with it, some others don't.

edit: Or Disk Drake might be good too,it's Linux. (Hi aysiu!)_

---

### Post by Alexandrian on 2006-04-08
OK, I tried defragging, still no good. I might need to use GParted.

But even still, shouldn't 8.2 GB of free space be enough to set up a new partition for Ubuntu? Whenenver I try to form the 8.2 GB of free space into a Fat32 system, it says the operation failed and it won't give me a reason why. Any ideas on why I am unable to install linux?

---

### Post by Herman on 2006-04-09
Yes, you are right, it seems to me that something funny is going on there. A small  glitch in your partition table or a problem with your BIOS or something maybe, who knows? 
When the partitioners behave strangely like that it's a sign definitley to double up on your safety precautions, that's for sure. **Make sure you have everything backed up that you want to keep!**

Is there anything unusual about your hard disk that you know of? Such as it is particularly new or old, or particularly large? Or your computer is particularly special? Or has had a virus of some kind at some stage in the past? Used a partitiioner that might be uncompatible with Linux? Has it had the latest BIOS flash available for that motherboard? Really it could be anything...
GParted livecd might give you an error message that might shed some light on the situation.
The best I can do is tell you to be careful and wish you good luck.  :-k (Herman)

---

### Post by Alexandrian on 2006-04-09
Ok, I looked through the setup menu and didn't see anything out of the ordinary, and I also defragged Windows.

As far as anything about my computer which might cause this... Well, being a Windows user, I have of course battled viruses many times in the past, including one time where it was necessary to reinstall Windows. When I did that, I downgraded from Professional to Home since I was off at college at the time and did not have a Professional CD with me. I was under the impression that software problems such as viruses could not affect hardware..

Also, shortly after I got the computer, I ran into a problem where suddenly the computer was unable to show color(everything was Black and White), and I was unable to launch Warcraft 3. It took 3 computer experts to figure out what was going on, after stumping the first 2(computer scientists), the third one (a computer engineer) figured out that my computer did not have enough interrupts. The problem was solved by freeing up some interrupts by removing the Modem, which was unused since I have a broadband connection. 

Anyone have any ideas on why it is not allowing me to format that 8.2 GB on free space as a FAT32 partition?

---

### Post by Alexandrian on 2006-04-09
And oh yeah, I have been able to run off the Live CD so I now Ubuntu can work on my computer.

---

### Post by Alexandrian on 2006-04-09
OK, I went into GParted using the LiveCD. I think I see why I couldn't install Ubuntu before- GParted says the free space is only 8 MB, I don't know why the install CD says I have 8 GB.

However, I still can't seem to resize my Windows partition. I go into GParted, click on the ntfs partition, resize it, create a fat32 and a swap partition out of the free space, and click apply. But after GParted is done, my new partitions are gone, and the ntfs partition has all of it's original space with only 8 MB of free space left over.

Windows isn't letting me take any space away from it.

---

### Post by cls1chuck on 2006-04-09
[this is my first post to 'help' instead of 'be helped', so take with caution!]:
Alexandrian,
I had the same problem with Gparted on the Live CD. What I did was (from a suggestion), use another Linux partitioning program -Qtparted. You can read the thread where I got this (and my exerience) at [URL="http://ubuntuforums.org/showthread.php?p=872484#post872484"]this thread 
[/URL]  
The relevant part starts around post 11, on page 2 of this thread.

Good luck!

---

### Post by Ric95 on 2006-04-09
I'm still new too, but then again, that helps me remember the problems I had. 
My install would always hang at that point untill I ran checkdisk (from windoze) 
Command console, Chkdsk C:/f 
Try that.

---

### Post by Alexandrian on 2006-04-09
nm...

---

### Post by valde on 2006-04-10
> Whenenver I try to form the 8.2 GB of free space into a Fat32 system, it says the operation failed and it won't give me a reason why. Any ideas on why I am unable to install linux?

Planning the layout of your partitions is an essential pre-requirement before installing a dual boot (or else you may have a lot of corrections to be done later). Please read some guides on partitioning:

[http://builder.com.com/5100-6372_14-5982893.html](http://builder.com.com/5100-6372_14-5982893.html)
[http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/)

If I know this correctly, Ubuntu installs as ext3 (may also use ext2 or RaiserFS). At the end of installation you should also install Grub (or Lilo) to be able to boot to Windows or Linux.

In a typical layout you might have your WinXP on the first (primary, active) partition (like hda1) and the linux partitions (and shared partition if desired) should be created as logical partitions (in extended partition container).
The 8GB space is not to much - you may try to resize your windows partition and get about 20GB of space to be safe. It is best to resize your windows partition with a quality partition manager as Acronis Disk Manager (free 30 days trial), but you may also try QTParted (may use rescue CD, [http://www.sysresccd.org/)](http://www.sysresccd.org/)).

I actually have Win XP and Ubuntu Breezy Badger in a dual boot set up.
Good lack.

---

### Post by Herman on 2006-04-10
> I was under the impression that software problems such as viruses could not affect hardware.. I agree with you, but there are certian places where virii can do damage that people often overlook when doing a re-install. 
Some viruses can cause corruption in the [MBR]("http://www.users.bigpond.net.au/hermanzone/p6.htm") and / or the partititon table, and some might cause different kinds of corruption in the programmable part of the BIOS. If it's only a little bit of corruption maybe your computer still works okay for the time being, but the 'Parted based partitioners can detect that something is wrong, so they won't do anything rather than risk a bad job.
Sometimes the partition table is okay "in the opinion of certain partitioning software", but does not conform with the rules of other partitioners. Maybe you just need to try a different partitioner, maybe that will fix it for you. Maybe a different partitioner will make it worse though, and really wreck the partition table, and you'll lose access to all your data. ( So do a good back-up first).
At least then you'll be able to start fresh again.
If you think there might be something corrupted in your BIOS maybe, I don't think it will do any harm to remove the battery for the BIOS for a minute and let the BIOS loose it's memory, then replace the battery and flash your BIOS with the latest BIOS flash available for it from your motherboard manufacturer. That might help. If you had any special settings in your BIOS you would have to set it up again, but for my old computer I just set it to 'Load Optomized Defaults' and just set the boot sequence and it works fine. There are special websites to help you set up your BIOS. [Click here ]("http://webpages.charter.net/netw_1/bios.htm")and [here]("http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm")
Take this advice with a grain of salt, and get a second opinion or two. I'm not a computer scientist or engineer, just a home handyman. I have fixed a few old computers though, that had nothing much wrong with them really, just needed some of this type of thing done. Often you don't really need to know what you are doing to get something working again. The ones I worked on were not working at all though, and the owners had given up on them. Yours is still working. You really are missing out on a lot of fun by not being able to get Ubuntu in, but on the other hand you should also ask yourself whether or not it is better to leave well enough alone. (Herman) :-k
Edit: Maybe try aysiu's [how-to for DiskDrake ]("http://ubuntuforums.org/showthread.php?t=114142")at least DiskDrake is another Linux partitioner, and it's enough different from the 'Parted based ones. Maybe it can tolerate whatever it is that's different about your computer better. Some partitioner should work.

---

### Post by cls1chuck on 2006-04-10
Alexandra,
Have you tried installing qtparted?  As I mentioned, I did that (even while bootin from the live CD), and it allowed me to shrink my NTFS part.  BTW, 8GB is more than enough, but you should leave some extra disk space for XP (swap file, etc.) unless you plan on doing cleanup.

---

### Post by Alexandrian on 2006-04-10
Ok, I've been researching QTParted online. According to wikipedia, it's a KDE program, and I didn't see any specific QTParted CDs, so I guess I can trying ordering a Knoppix CD and using that resize NTFS. I also saw this program that is supposed to resize NTFS on Windows, anybody know if this is any good? [http://gnuwin32.sourceforge.net/packages/ntfsprogs.htm](http://gnuwin32.sourceforge.net/packages/ntfsprogs.htm)

---

### Post by bigken on 2006-04-11
Hi the way I have resized ntfs partions is using the rescue disc download it from here [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

defrag win xp 1st then boot from cd and run qtparted down size your ntfs partion
I have done this several times without any problems   hope this helps ;)

---

### Post by cls1chuck on 2006-04-11
Alexandrian,
I downloaded and ran it while booted from the Gnome Ubuntu Live CD. It is NOT just a KDE program from my understanding or experience.
From the Synaptic Package Manager, select ALL, then QTParted.  You will also need ntfsprogs.
another site you may find useful is:
[http://qtparted.sourceforge.net/download.en.html]("http://qtparted.sourceforge.net/download.en.html")

---

### Post by cotcot on 2006-04-11
Alexandrian,

Try as said in previous posts "disk drake". There is also since a short while the "GParted live CD" that works too. 
These GUI unfortunately do not tell you what the problem is if something does not work or if the GUI does not allow you an operation you want to do. 

If you do not get what you want with the GUI I suggest to take a little bit more time to read the manual of "parted". This is the program on which Gparted and QTParted is based. It has a very good manual (google for "GNU Parted manual). You might be afraid to use  "parted" in command line, but after reading the manual I am sure you will conclude that this is nothing to be afraid of. The manual has clear examples for each instruction. Resizing NTFS is also included.

8 GB is enough for Ubuntu unless you have too much data (more than some 4 GB) in your home. Consider an ext2 formatted partition to share data between XP and Ubuntu. Install therefore the ext2 driver ([www.fs-driver.org](www.fs-driver.org)) in XP.

Good luck

---

