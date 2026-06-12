---
title: "How do I format my old WIndows XP drive to ext3?"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by slimfrinky on 2005-11-30
Hi all... I decided to test Ubuntu out for one month, and promised myself that if I was able to catch on to everything that I needed that I would get rid of Windows for good.

It's been a month now. Ubuntu does exactly what I want with only a few minor snags. Time to make good on my promise. The only problem is that I'm having some trouble removing my Windows installation.

Here's the deal:

I have both Windows and Ubuntu installed on my system.
They are on two seperate hard drives.
I want to erase the Windows partition on that hard drive, and then format that disk to the ext3 filesystem. After this I want to mount it somewhere in my filesystem. 
No big deal right? The only problem I have is that when I attempt to delete the partition, fdisk is telling me that the disk doesn't exist...

The command I'm using is "fdisk /dev/hdb".

Any input?

---

### Post by frodon on 2005-11-30
Did you try Gparted or Kparted ? 
It's a graphical tool to format and do all the needed tricks on a partition.

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by slimfrinky on 2005-11-30
Ok, figured it out right after posting... 

I forgot the whole 'sudo' thing... D'OH!!!

Sometimes I'm a moron... Anyway, might as well turn this into a brief tutorial... 

********WARNING************
Only do this if you have some idea of how formating and file systems work. If you just jump in, you have a 95% chance of ruining your system.
********END WARNING*******

First things first, identify what your secondary drive is... This is normally /dev/hdb

Quick tip for you. Devices in Linux are located within the /dev folder. In this case we are dealing with a hard drive so we are looking for something that begins with a 'hd', meaning hard drive. The letter after that is signifying which hard drive it is. In this case we are dealing with hard drive #2, so the letter is 'b'. Simple.

Next, go to terminal and type in the command 'sudo fdisk /dev/hdb'. This will bring up a little menu operated program.  You can hit the 'm' key for more help, but I'll just run you through the options I selected.

Hit 'd' to delete a partition. Select the partition you want to delete.
Hit 'n' to add a new partition. Follow the simple instructions.
Hit 'w' to write the new partition table to the hard disk.

Horay! We have just deleted the old partition and created a new one in it's place! Now lets format this bad boy.

Type in 'sudo mkfs.ext3 -b 4096 /dev/hdb1'. This command formats the chosen partition to the ext3 filesystem. This is good. For all intents and purposes the drive is now usable once we mount it. However I do recomend making some minor changes after mounting is complete.

In my case I chose to mount the drive to a previously created folder. You can make your own folder for this if you want using the 'mkdir' command, but I choose to just keep the existing folder. The command I used was 'sudo mount /dev/hdb1 /media/windows'. Basically this is telling the filesystem, "Hey, make it so that Mike can look at the contents of this device at this folder over here."

Now we run into something a bit hairy. If you use Nautilus to try to copy some files over it will tell you that you don't have permission. If you look at the properties of the folder by doing a 'ls -l /media/windows' you will see that the folder is owned by root. Thats no good, so lets change the ownership of the folder. This is done with the 'chown' command like this: 'sudo chown mike /media/windows'.  COngradulations, your user account now owns that folder, which should by default give him the proper permisions to access it without an issue.

One other thing, if you want the drive to be mounted at boot, you need to modify the '/etc/fstab' file to include the new filesystem. And here is how you do that.

sudo gedit /etc/fstab

This will bring up the happy list of partitions on your computer. Lets modify it a bit, shall we? 

All we do is look at the first column in the file. Browse down looking for the name of the device and partition you want to mount (/dev/hdb1 in my case) and delete the entire line if it is there. If it isn't there, you are good to go. After this is done, put this at the end of the file... "/dev/hdb1       /media/windows  ext3    defaults 	0       0"

This is just like the 'mount' command except that it gives you the option on the last two columns to have the computer check to see if the partition needs to be backed up, and if the filesystems integrity needs to be checked. Save the file and close gedit.

Thats it! At this point you are done, you have deleted windows and turned that disk into file storage space for your wonderous Linux box! Your disk is mounted, and it will now automount on reboot! Ain't life grand?

Anyway, if there are any Linux gurus out there who see any mistakes I've made, feel free to correct me. I've only been playing with Linux for a month total, so I'm not 100% sure that I'm right about everything. And if you want to try this, PLEASE read any responses from more experienced people before you follow my advice. 

Well thats it for my first tutorial. I hope it helps someone understand more about the Linux filesystem.

---

### Post by ed_d on 2005-11-30
Why not make it even easier. First, go to System>Administration>Disks. Select the disk that you want to change. then change/format to what you want. You may have to use fdisk first to add anew disk, but if it was already there, this tool should make it easier for the noob as far as command line. My 2 cents

---

### Post by slimfrinky on 2005-12-01
The reason why I'm doing it through the command line is to learn as much as I can about the operating system, since after all, the skills I learn on Ubuntu can be ported over to other distros of Linux. Not that I'm planning on switching, but it's entirely possible that I could get a job managing Red hat Servers in the future, in which case I would want to know as much as possible about the command line for my job.

Thats why I do things the hard way... *grin*

---

### Post by FaceLeg on 2007-03-03
Thanks, I have found this to be the most easy to follow walkthrough yet!  

:)

---

