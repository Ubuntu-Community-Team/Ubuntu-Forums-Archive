---
title: "Ubuntu install questions"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Trustem on 2007-04-07
My current OS is XP Pro. My HD has two partitions with 5.49 GB free space on partition C and 11.3 GB free space on D. My intention is to install Ubuntu 6.10 from a CD. Several questions: 1) Does it make a difference on which partition I install Ubuntu--in other words--is the 5.49 GB free space on the C partition plenty adequate? 2) When I come to the section of the install about where to install Ubuntu, which of the three options should I select. (I am very concerned about the "warning" as this is my work computer with many critical files installed. I cannot lose them!). If  I remember correctly, one option was something about erasing everything (sounds scary); a second option was install on available free space, and another was install manually. Which choice do you recommend for a novice? Finally, 3) Is there a straightforward way to install my files currently on XP Pro on Ubuntu as well, enabling me to choose either OS? TIA!

---

### Post by siciliancasanova on 2007-04-07
1) Have you thought about Xubuntu in your situation?  

If you want a beginners guide on how to partition, I would go [here]("http://www.psychocats.net/ubuntu/partitioning").

---

### Post by az on 2007-04-07
If you have the free space as *unpartitioned* space, then pick the USE FREE SPACE option.  If it is just that you have some space left on your windows partition, you will have to shrink the partition down to create some free space, and the installer will then use that free space to make two new partitions on that.

The partitioning is very safe, but no partitioner on the market is 100 percent safe.  If you cannot back up your critical data, you should not mess around with your computer in any way.

5 gigs is enough to install and try Ubuntu -  the base install will require just less than two gigs of hard drive space for the filesystem, plus another swap partition for virtual memory (usually 1.5 to 2 times your ram, depending on how much room you have).  You will run out of room fast if you download lots of stuff, though.  I would use the drive with the more room (11 gigs).  It makes no difference on which drive you install Ubuntu.  It's not like windows which traditionally likes to live on C:

There are a number of ways to access your files.  There are ntfs drivers for linux and there are ext3 drivers for windows.

---

### Post by bapoumba on 2007-04-07
Hello Trustem, and welcome to these forums. I've moved your thread to a more appropriate section ie "Absolute Beginner Talk" support forum.

---

### Post by gnoel on 2007-04-07
If you're working with a desktop computer and you have an open drive bay, then I'd strongly recommend a second hard drive.  You can format it as FAT32 which means that any modern Linux as well as Windoze will be able to Read/Write.  You can share all your data between the two (or more) OS's, just boot into the OS suitable for the task.  That would be XP for games, Ubuntu for everything else ;) 

I felt very relieved once I got all my data and media files off my OS disk.

---

### Post by phr0ze on 2007-04-10
'a second option was install on available free space'

Use this option. This is a very easy way to install, it will make the partition for you and typically leave windows untouched. You will be able to choose windows or ubuntu at boot time. The other nice thing about Ubuntu install is none of the choices you make are final until the last confirmation screen. Kinda like placing an order online. You make several choices, then it shows you a summary and asks you if this is what you really want. Very cool.

Now some other help. You said you have critical files on the drive which you can not loose. Please back them up now. I've seen far too many hard drives fail at the worse possible time. Please Please Please back it up now.

5 GB left on C Drive? I wouldn't put ubuntu there. Simply because you will want to leave half of that free space to windows. This only leaves Ubuntu with 2.5 GB.  I'm sure Ubuntu can run in less space, but with swap partitions, patches and everything else, you may find that you quickly regret the choice.

Finally, If you are letting ubuntu share with windows, before you even install ubuntu, please boot into windows and defrag the drive which Ubuntu will be using.

---

### Post by The Duke of Ted on 2007-04-10
Hi, I'm a ubuntu convert - I recently downloaded version 6.10 and want to create a separate partition to dual-boot ubuntu with Windows XP, but I keep running into problems - for some reason, it seems my PC is incapable of resizing my Data partition...

My hard drive is partitioned into three sections - the first one is a backup partition, the second is my Windows XP / programs partition, and the last is for data.

Partition One: FAT - 7.81 GiB
Partition Two: NTFS - 30.00 GiB - boot
Partition Three: NTFS - 111.24 GiB

The Third Partition is the one I want to resize.  I have tried to do so using Paragon Partition Manager in XP, and it restarts the computer, but doesn't do anything.
Doing so when going through the installation procedure in ubuntu, and it results in the following error:
> The following operation could not be applied to the disk

*Resize /dev/sda3 from 111.24 GiB to 69.19 GiB*

See the details for more information

I'm completely stuck on what to do, and I desperately want this to work, as I'm already amazed at the quality of ubuntu - please come up with a solution for me :)

---

### Post by JayQueue on 2007-04-14
I'm having my own problems.  I have my partitions, 1 gig for swap and 10 for the program, and I'm on step 5 of 6 in the installer.  I come to the screen where it shows my hard drives and my partitions with the drop down boxes for what you want to mount into each drive.  I select "swap" for my one gig spot and "/" for my 10 gig spot.  I clock "forward" and an exclamation pops up saying "No root file system"  What's going on?

---

### Post by lynx.jc on 2007-11-03
Same problem here... and also a newbie on linux

Partition One: FAT - 3 GiB
Partition Two: Fat32 - 54 GiB - boot Windows XP
Partition Three: swap - 1.97 GiB (for ubuntu, created on ubuntu from the boot cd)
Partition four: FAT32 - 52 GiB (to install ubuntu)

I'm stuck on step 4 of 7 it doesn't allow me to select the FAt32 or tells me "No root file system" but also is not giving me the option to specify the mountin partition, i read somewhere that FAT 32 was ideal for ubuntu, i dont really know if thats true so i formatted the Fat32 to xfs, then the [format?] box was check but i still couldn't go further and the message still appears, what am i missing here.... ?

---

