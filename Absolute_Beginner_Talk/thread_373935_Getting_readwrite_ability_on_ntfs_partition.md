---
title: "Getting read/write ability on ntfs partition"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-03-01
Hey all, I need some help. I'm a newbie to Linux and I'm trying to setup Ubuntu so it will be able to read/write to a ntfs partition.  I'm trying to follow the steps [here]("http://fuse.sourceforge.net/") but I have to admit I don't know what I'm doing.  Actually I first need to figure out how to even see the partition as it's not showing up automatically in Ubuntu.  I've been searching through the help that's available from the desktop for a way to see the drive and mount it but I've had no luck yet.  Anyway, here is what I get in the terminal window after trying to do the "make" and "make install" operations. Any guidance would be greatly appreciated.

bubba@ubuntu:~$ gksu gedit /etc/apt/sources.list
(gedit:5566): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
./configure
make
make install
.
./
'/home/bubba/Desktop/fuse-2.6.3/configure'
make
make install
/home
/bubba
/home/bubba/Desktop/fuse-2.6.3/configure
/home/bubba/Desktop/fuse-2.6.3/make
/home/bubba/Desktop/fuse-2.6.3/make install
bubba@ubuntu:~$ ./configure
bash: ./configure: No such file or directory
bubba@ubuntu:~$ make
make: *** No targets specified and no makefile found. Stop.
bubba@ubuntu:~$ make install
make: *** No rule to make target `install'. Stop.
bubba@ubuntu:~$ .
bash: .: filename argument required
.: usage: . filename [arguments]
bubba@ubuntu:~$ ./
bash: ./: is a directory
bubba@ubuntu:~$ '/home/bubba/Desktop/fuse-2.6.3/configure'
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
bubba@ubuntu:~$ make
make: *** No targets specified and no makefile found. Stop.
bubba@ubuntu:~$ make install
make: *** No rule to make target `install'. Stop.
bubba@ubuntu:~$ /home
bash: /home: is a directory
bubba@ubuntu:~$ /bubba
bash: /bubba: No such file or directory
bubba@ubuntu:~$ /home/bubba/Desktop/fuse-2.6.3/configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
bubba@ubuntu:~$ /home/bubba/Desktop/fuse-2.6.3/make
bash: /home/bubba/Desktop/fuse-2.6.3/make: No such file or directory
bubba@ubuntu:~$ /home/bubba/Desktop/fuse-2.6.3/make install
bash: /home/bubba/Desktop/fuse-2.6.3/make: No such file or directory
bubba@ubuntu:~$

---

### Post by Michaelt74 on 2007-03-01
First you have to mount the Windows partition, after that it's quite easy. I'm using Edgy 6.10, check out this link

[http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/](http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/)

Hope that helps

---

### Post by Thrasonic on 2007-03-01
Hmmm... it's very hard.  When I go to the link you provided I get stuck on the first item in the list - Enable the universe repository and install the ntfs-config package.  What is the universe repository and how do I enable it and use it?

---

### Post by Fitzy_oz on 2007-03-01
> **Thrasonic said:**
> Hmmm... it's very hard.  When I go to the link you provided I get stuck on the first item in the list - Enable the universe repository and install the ntfs-config package.  What is the universe repository and how do I enable it and use it?

I used this guide when I first came across to Ubuntu, try it if you have any troubles just ask.
[URL="http://ubuntuforums.org/showpost.php?p=1263001&postcount=1"]
http://ubuntuforums.org/showpost.php?p=1263001&postcount=1[/URL]

The universe repository is located in the packages or preferences section of the synaptic package manager.

Menu: System---> Administration ------> Synaptic Package Manager

Synaptic Package Manager ------> Preferences or Packages (I can't remember of the top of my head as im not in front of my linux box) and you should get a dialog box like the one in the picture i've attached.  Just enable all of them.

---

### Post by Thrasonic on 2007-03-01
Man, this is the one I started out with and it's confusing to me.  I have an AMD64 system, too, and his talk about "universe" confuses me concerning my AMD64 system.  I don't know what universe is?

---

### Post by spoot on 2007-03-01
> **Thrasonic said:**
> Man, this is the one I started out with and it's confusing to me.  I have an AMD64 system, too, and his talk about "universe" confuses me concerning my AMD64 system.  I don't know what universe is?
Universe has nothing to do with your system. It is just another place Ubuntu software is located in and what you can download after you enable the repository. It is not supported however, and therefore (I think) not enabled by default.

> Adding this repository will mean that the majority of the Free Software universe will be available to install on your system. This software is supported by a carefully selected group of volunteers within the Ubuntu Community, but is not supported by the core Ubuntu development team and may not include security updates.
(from [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html))

---

### Post by Thrasonic on 2007-03-01
I'm still unclear about exactly where to start.  I'm a true blue newbie and am totally clueless.  Since I'm an AMD64 user do I need to go through all the steps as if I'm not?

---

### Post by Fitzy_oz on 2007-03-01
> **Thrasonic said:**
> Man, this is the one I started out with and it's confusing to me.  I have an AMD64 system, too, and his talk about "universe" confuses me concerning my AMD64 system.  I don't know what universe is?

The universe is just the name of a package repository or software source for Ubunut to obtain packages for installation - I've booted into a live cd at work to find the exact way to enable them.

Go through the menu System ---> Administration ----> Synaptic Package Manager

You should get the screen displayed in my first attachment

after that goto settings ----> Repositories 
You will get a screen like the one in Attachment 2


Enable all of these repositories not just the universe or community maintained.

That should take care of your universe trouble.

---

### Post by Thrasonic on 2007-03-01
Thanks.  I did it, I think, but mine looked different than your second image and I'm thinking it's because I'm using 6.10 versus 6.06?  Anyway, I found ntfs-3g in the list and am installing it now.  I'm off to bed, though, so I'll pick this up tomorrow or Saturday.  Thanks for all the help tonight.

---

### Post by Fitzy_oz on 2007-03-02
> **Thrasonic said:**
> Thanks.  I did it, I think, but mine looked different than your second image and I'm thinking it's because I'm using 6.10 versus 6.06?  Anyway, I found ntfs-3g in the list and am installing it now.  I'm off to bed, though, so I'll pick this up tomorrow or Saturday.  Thanks for all the help tonight.

Yes that would be why - I was using a live cd 6.06 which is all I had at work.  Good luck with it.

---

### Post by Michaelt74 on 2007-03-02
Hope you get it sorted out. I use an Intel laptop not AMD, so I can't help with AMD configuration, but keep trying.

---

### Post by Thrasonic on 2007-03-10
Hey all.  Okay, how do I check to see if the ntfs-3g thing was installed and is working or available or whatever?  Here is what my fstab looks like after having edited it according to the main setup thread for this authored by givre.  Basically, what I've done so far still hasn't allowed me to see the ntfs drive.  Help please?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f399eb01-3139-42e4-964e-7ad82525a0e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3f712018-b00e-4e24-8475-fe93d8fdfec9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5	/media/sda5	ntfs	nls=utf8,umask=0222	0	0

---

### Post by Thrasonic on 2007-03-10
bump

---

### Post by igknighted on 2007-03-10
Make the fstab line for you ntfs partition look like this.  To edit it you will need to open it with:
```
gksudo gedit /etc/fstab
```

The find the line about ntfs and delete it and copy/paste this one in there in its place:
```
/dev/sda5 /media/sda5 ntfs-3g rw,nls=utf8,umask=0222 0 0
```

Then save and exit, on your next restart you should have read/write rights to it

---

### Post by Thrasonic on 2007-03-10
Thanks.  I did that, rebooted, and I still don't see it in Places >> Computer.  Any thoughts on how to fix this?  Let me know what you need to me post (copy and paste or such).  Thanks.

---

### Post by igknighted on 2007-03-10
What happens if you go to /media/sda5 in nautilus?

---

### Post by Thrasonic on 2007-03-10
Uh oh... what's nautilus?  I'm a complete newbie...

When I go to Computer I see my CDRW/DVDRW drive and my Filesystem drive, where Ubuntu is installed.  I see no other drives.

---

### Post by igknighted on 2007-03-10
Nautilus is the file browser (like explorer in windows).  I would go into the file system file, then there should be a folder /media there, go into that, then look for a folder /sda5, go into that.  All your windows files should be there.  Linux does not mount your drives at the top level like windows (C:, D: etc.) but rather all as branches under a tree, and it all starts at / (the filesystem).  Your windows drive was mounted at /media/sda5.  Ubuntu usually puts an icon on the desktop though, so you should see that too.

---

### Post by Thrasonic on 2007-03-10
Thanks for the explanation and help.  I went into that folder and all I see are cdrom and cdrom0.  I went into each just to see what might be there and they were both empty.  Any thoughts?

---

### Post by Thrasonic on 2007-03-10
bump

---

### Post by Thrasonic on 2007-03-10
bump

---

### Post by Thrasonic on 2007-03-10
bump

---

### Post by enopepsoo on 2007-03-10
it sounds like your drive doesn't mount.  what is the output when you type 
```
sudo mount -a
```
if there is no error, you should be able to open the mount point.

---

### Post by Thrasonic on 2007-03-12
I do get an error message.  Here it is:

fusermount: failed to access mountpoint /media/sda5: No such file or directory Retrying mount...
fusermount: failed to access mountpoint /media/sda5: No such file or directory Failed to mount NTFSUnmounting /dev/sda5 (DATA)

Let me know where you think I should go from here.

---

### Post by Thrasonic on 2007-03-12
bump

---

### Post by Thrasonic on 2007-03-12
bump

---

### Post by buuntuu! on 2007-03-12
ouch, i read your thread from beginning to end and even MY head began aching from your continuous bumps ;)
unfortunately i can't really help with your problem, being quite new to linux myself, but maybe some brainstorming will help:
your problem, i think, is not too difficultult to solve for someone with a little experience (which might be you in next to no time). in the meantime why not try a little workaround? like a fat32 partition to swap files between linux and micro$oft (both OS have read/write access to fat32) or a [driver]("http://www.fs-driver.org/") which lets window$ read/write ext3 which probably is the fileformat of your linux-partition. (it's easy to install,  did it myself and am happy with it)
have fun and keep trying!

---

### Post by David_UK on 2007-03-12
Hi Thrasonic

> **Thrasonic said:**
> Hey all, I need some help. I'm a newbie to Linux and I'm trying to setup Ubuntu so it will be able to read/write to a ntfs partition.  

I was in a similar situation myself a few days ago.  Maybe my experince can help.  My thread was: [http://www.ubuntuforums.org/showthread.php?t=379564](http://www.ubuntuforums.org/showthread.php?t=379564).  Post 2 was an excellent link.  I wanted to make a FAT32 partition visible to both Windows and Ubuntu 6.06.  The link also describes how to make an NTFS partition visible from linux.

It does not involve downloading anything, simply to add a folder to your directory (to mount the partition on) and then to edit your fstab configuration to enable linux to see it.

I'm very new myself but was able to follow the instructions fairly easily.

Good luck!

---

### Post by Thrasonic on 2007-03-12
> **buuntuu! said:**
> ouch, i read your thread from beginning to end and even MY head began aching from your continuous bumps ;)
unfortunately i can't really help with your problem, being quite new to linux myself, but maybe some brainstorming will help:
your problem, i think, is not too difficultult to solve for someone with a little experience (which might be you in next to no time). in the meantime why not try a little workaround? like a fat32 partition to swap files between linux and micro$oft (both OS have read/write access to fat32) or a [driver]("http://www.fs-driver.org/") which lets window$ read/write ext3 which probably is the fileformat of your linux-partition. (it's easy to install,  did it myself and am happy with it)
have fun and keep trying!

I'm sorry for making your head hurt...  =)

Thanks for the idea.  I suppose that if nothing else I could create an additional partition, make it FAT32, and use it as you suggest.  At least it's an idea.

---

### Post by Thrasonic on 2007-03-12
> **David_UK said:**
> Hi Thrasonic



I was in a similar situation myself a few days ago.  Maybe my experince can help.  My thread was: [http://www.ubuntuforums.org/showthread.php?t=379564](http://www.ubuntuforums.org/showthread.php?t=379564).  Post 2 was an excellent link.  I wanted to make a FAT32 partition visible to both Windows and Ubuntu 6.06.  The link also describes how to make an NTFS partition visible from linux.

It does not involve downloading anything, simply to add a folder to your directory (to mount the partition on) and then to edit your fstab configuration to enable linux to see it.

I'm very new myself but was able to follow the instructions fairly easily.

Good luck!

Hey David_UK, thanks for the reply.  I'll give your thread a read and see what I can do.

---

### Post by Thrasonic on 2007-03-12
> **David_UK said:**
> Hi Thrasonic



I was in a similar situation myself a few days ago.  Maybe my experince can help.  My thread was: [http://www.ubuntuforums.org/showthread.php?t=379564](http://www.ubuntuforums.org/showthread.php?t=379564).  Post 2 was an excellent link.  I wanted to make a FAT32 partition visible to both Windows and Ubuntu 6.06.  The link also describes how to make an NTFS partition visible from linux.

It does not involve downloading anything, simply to add a folder to your directory (to mount the partition on) and then to edit your fstab configuration to enable linux to see it.

I'm very new myself but was able to follow the instructions fairly easily.

Good luck!

Okay, so I followed the link from your thread, the one to psychocats.com, and was able to finally mount my darn NTFS data volume.  Jeesh that took forever.  Anyway, I went into a folder there and right-clicked on a file to see if I could rename it (assuming that the rename option would be on the context menu like in Windows) and I couldn't rename it using that context menu.  It wasn't an option for me to click.  Does that mean that I only have read access and not read/write access?  If so how do I remedy this?  And lastly, because this entry is now in my fstab file does that mean that the data drive will now mount automatically each time I reboot Ubuntu?

---

### Post by Thrasonic on 2007-03-12
bump

---

### Post by Michaelt74 on 2007-03-12
You have the Windows drive mounted, now try these instructions, I posted them earlier, but maybe that was before you got the mounting sorted out. With ntfs-3g you have full write access and it works great.

[http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/](http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/)

Good luck!

---

### Post by Thrasonic on 2007-03-13
Thanks.  You're correct.  I just now sorted out getting to the NTFS drive.  Now I'll try this and report back.

---

### Post by David_UK on 2007-03-13
Thrasonic

Well done on getting it mounted.  Reading a bit more around the subject, as you have found, linux can read NTFS but can't write to it without the extra application.

> **Thrasonic said:**
> And lastly, because this entry is now in my fstab file does that mean that the data drive will now mount automatically each time I reboot Ubuntu?
Yes.  It will be there every time.

Should you wish to make a shortcut to your NTFS mount folder: right-click on it>create link, then drag it to the desktop or wherever you wish.

BTW that psycocats site is an interesting read for first-timers.  I feel I understand a few things better by randomly flicking through the topics.

---

### Post by Thrasonic on 2007-03-13
> **Michaelt74 said:**
> You have the Windows drive mounted, now try these instructions, I posted them earlier, but maybe that was before you got the mounting sorted out. With ntfs-3g you have full write access and it works great.

[http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/](http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/)

Good luck!

Okay, I did what was recommended at the link you provided.  That was easy.  However, I'm not at home so I can't reboot it right now.  Is there a way to see if the change I made to the fstab file so that I can read/write to the ntfs partition has worked?  Does unmounting and remounting the drive work?  If so, how do I do that?  If not, any other suggestions besides waiting until I get home in 3 hours?

---

### Post by Michaelt74 on 2007-03-13
I think the only way to check is to test it - i.e. copy a file from Ubuntu and paste it into a directory in Windows. 

Good luck

---

