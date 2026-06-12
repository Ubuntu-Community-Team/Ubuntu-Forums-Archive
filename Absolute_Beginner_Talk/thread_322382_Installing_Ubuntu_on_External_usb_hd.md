---
title: "Installing Ubuntu on External usb hd"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by mikaveli on 2006-12-20
Hi, 
I would like to start by saying I'm a pretty much a linux virgin, besides using ubuntu lightly at school.  

Alright my problem is this: 
            I have a 160g Western Digital usb external hd. I would like to install ubuntu to the usb hd drive then have grub boot ubuntu only when the external is connected.  My first attempt installed alright but when i unplugged the drive and restarted the computer grub started then froze.  I have XP loaded on my internal hard drive and i dont want to play with the mbr of it or partition the internal drive. 

Now i need help all the way at the begining: from partitioning the hard drive to installing a mbr on the external drive if necessary? I have read through most of the posts on this site and none of them seemed to make sense or help.

I would appriciate any help, thanks.

---

### Post by ingo on 2006-12-21
To be honest, I don't quite get your problem. 

You have XP on the internal, Ubuntu on the external drive. Also, I take it you have told your bios to boot off the external hard drive.

All else is conjecture. Can you please take us through exactly what you did and what problems you are experiencing/error messages you are getting?

---

### Post by 454redhawk on 2006-12-21
[http://www.ubuntuforums.org/showthread.php?t=80811]("http://www.ubuntuforums.org/showthread.php?t=80811")




> **mikaveli said:**
> Hi, 
I would like to start by saying I'm a pretty much a linux virgin, besides using ubuntu lightly at school.  

Alright my problem is this: 
            I have a 160g Western Digital usb external hd. I would like to install ubuntu to the usb hd drive then have grub boot ubuntu only when the external is connected.  My first attempt installed alright but when i unplugged the drive and restarted the computer grub started then froze.  I have XP loaded on my internal hard drive and i dont want to play with the mbr of it or partition the internal drive. 

Now i need help all the way at the begining: from partitioning the hard drive to installing a mbr on the external drive if necessary? I have read through most of the posts on this site and none of them seemed to make sense or help.

I would appriciate any help, thanks.

---

### Post by mickbw on 2006-12-21
Hi,

Being the paranoid type about the contents of my Windows partition, I disconnected the internal hard drive to ensure that Ubuntu was installed on the External drive.  

You may find that your bios will not accept booting off the external drive if it is too large of a partition.  I had to install /root to a small partition on the external.  Then I was able to run the gparted live CD to expand the size of that partition once I got everything running correctly.   I also installed a large Fat32 section in the External Drive so I could use it easily from either OS.  

Now that everything is installed on the External Drive, I go into Bios to set which drive I wish to boot from when I want to go into Windows.  

It ain't pretty but it works.  

Good Luck,

Michael

---

### Post by ingo on 2006-12-21
Great thread, but what does it have to do with you (or do you seriously expect everyone to plough through all that)? As you did not post in it I cannot see what parts of it are relevant to you.

Anyway, it looks like Grub is already in your mbr if that is the first thing you see when switching on the computer. Please provide us with the info we asked for, otherwise we cannot help you.

> Can you please take us through exactly what you did and what problems you are experiencing/error messages you are getting?
 		 	 		 		 		 		 		 	 		[RIGHT] 			 			 				[IMG]http://ubuntuforums.org/images/uf/misc/progress.gif[/IMG] 				[/RIGHT]
[RIGHT][URL="http://ubuntuforums.org/editpost.php?do=editpost&p=1916012"]
[/URL][/RIGHT]

---

### Post by ucsdrake on 2006-12-31
hey, I'm in a very similar situation to mikaveli, I'm very new at linux in general and I'd like to install Ubuntu (6.10 I believe) on my external Hard Drive USB 2.0.  I don't want to have any linux files on my internal HDD because it is mainly for work.  My goal is to start playing around with linux (specifically ubuntu) for now until I become more comfortable with the OS.

Now I've read several guides and the problem is, well, I just dont understand most of them (like the one that 454redhawk pointed out I tried to read it but ended up just getting lost). Here's what I have planned and set up.

I have a Kaser 250gb USB 2.0 External Drive (about 230gb to use)

What I've planned out is as follows;

180gb - Windows NTFS (primary)
2gb - Windows VM (primary)
2gb - Linux Swap (primary)
10gb - Linux Root (primary)

In an Extended Partition
31gb - Sharded linux/Windows Fat32
15gb - Linux/Home EXT3
5gb - Linux/tmp EXT3
5gb - Linux/var EXT3

I got the guide to do this at [http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html)

Now here comes my problem.  Like I said I don't want to touch my Internal HDD so when I go to manually partition the HDD's im not totally sure what partitions to delete and what to keep

and even more-so I cannot Unmount my External HDD everytime I try it gives me the error (I read that you have to unmount in another thread)

Could not unmount /dev/sda1
umount: /media/External Hard\040Drive: not found

Now please remember I'm very very new at Linux overall so just giving lines of code to me won't help because quite honestly I have no idea what to do with them so please be more specific.

Thanks for any help in advance, and if you have any questions about my setup, goal, etc. I'd be happy to give more information

PS.   I've also been looking at links such as [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
and [http://www.ubuntuforums.org/showthread.php?t=282018&highlight=Fat32+Size+Limitations](http://www.ubuntuforums.org/showthread.php?t=282018&highlight=Fat32+Size+Limitations)

but I'm still lost at this point on what to do.

---

### Post by gn2 on 2006-12-31
My advice is use PCLinuxOS, it has install to USB as part of it's normal install process and will take care of it for you automatically.

---

### Post by macogw on 2006-12-31
ucsdrake: When we give you lines of code you copy and paste them into the Terminal (Applications > Accessories > Terminal).  We won't be doing that for install stuff though, I don't think...

To the OP: put in your Windows disc without the external attached.  Run fixmbr.  That'll put the Windows mbr back on your internal drive. To choose which drive to boot, just put the external drive as first in the boot sequence so when it's plugged in it'll boot, and when it's unplugged, Windows will boot.

To ucsdrake: If you're not touching the internal drive, then don't.  There should be a drop down in the top right to choose which hard drive you are installing to.  Choose the external one.  That one has Windows on it already right?  Make sure you defragmented it a few times so that there's not crap scattered all over the disk.  Don't delete any partitions.  Resize your Windows one so it's only 180 instead of the whole disk.  Now add partitions as necessary to make the partition table you outlined in your post.  There's a calculator in Applications > Accessories, so you can convert your GB to KB (or is it bytes that the thing uses?).  I don't know why it won't unmount though.  I have noticed that you have to unmount it to install to an external drive.  Are you using a command to unmount (I ask because it shows 040 in there)?  Try just right-clicking the one that's on the desktop.  If it's not showing up on the desktop, then it didn't auto-mount to begin with, so you can't unmount a not-mounted drive.

---

### Post by ucsdrake on 2007-01-02
thanks for the help, i was able to install Ubuntu onto my external hard drive!
i had to unmount it from the desktop just like you said lol

---

