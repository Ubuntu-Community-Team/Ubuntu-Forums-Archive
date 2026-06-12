---
title: "Cannot Finish Ubuntu Install"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Avenue on 2006-05-01
Hello Everyone, 

I have been trying to finish my Ubuntu install for the past three days now but I keep getting held up when it comes time to restart the computer after installing from CD.  I get what looks to be a DOS prompt with with the message:

"**Invalid Boot Diskette  Insert Boot Diskette in A:"**

I have tried re-arranging my boot options in BIOS, but this does not help.  When I put the CD back in, it wants to take me through the installation process all over again (which i've done a few times).  I've also tried hitting the "ESC" key when I get to the point of rebooting and re-installing the bootloader.  Still get the same thing after I start.  

I've also tried using another CD, and all of my CD's have come straight from Canonical.  I'm only using one hard drive and i'm using one big extended partition for this install.  

I've got that certain feeling that the bootloader is not being accessed on my hard drive, but I have absolutely NO IDEA how to get around it.  

Would any of you happen to know???

Thanks!!!

Ave

---

### Post by trent dillman on 2006-05-01
can you 'boot' a live ubuntu cd and then use the 'boot from hard disk' option?

I know Dapper live has this feature, not sure about Breezy...

---

### Post by confused57 on 2006-05-01
Grub installs just before the installation ejects the tray ands tells you to remove the CD. I did a search myself & couldn't find anybody with a similar problem, sure is perplexing.  Hope it isn't a problem with your hd.  You may want to try just disconnecting your floppy drive cable & power connection during the install, worth a shot.  Sounds like for some reason your computer thinks there's a floppy disk in the drive.

---

### Post by harishg on 2006-05-01
Where did you ask the grub booter to be installed ?  Did you have windows xp on another partition ? 
I would think it might be a problem with the boot loader or may be the partition table has been messed up.Best idea would be to check with live cd and see if it boots up.

---

### Post by Avenue on 2006-05-01
I'm not running anything on this particular hard drive in which I am trying to install Ubuntu, there is nothing on it.  

The weird thing about all of this is that I am using swappable hard drives (I only can have one in at a time) - when I put my Windows drive back in and boot up it loads just fine (???).  

I have tried inserting the Ubuntu Live CD and it does work, so that doesn't seem to be a problem except that there is no option to boot to the hard drive from the CD.  

I'm honestly thinking that I need to put the bootloader on a floppy disc and boot from there during my restart.  Anyone know how to create an Ubuntu floppy bootloader?

Thanks!!!

---

### Post by confused57 on 2006-05-01
Try running the live cd with the hd you're trying to install ubuntu on connected.  I'm not sure about the live cd, but you may be able to click on System---Administration---Disks  and see what information it has about the partition table.  You may need to mount the hd first.
I don't know if a boot floppy would be the answer.

How big is the HD you're trying to install Ubuntu on?  I know you want to get Ubuntu installed, but it's sure a  lot of work to switch out drives while you're troubleshooting.  I'd recommend putting your windows drive in and play with the live cd for awhile, it won't affect your hard drive or windows installation.  That way you can get used to Ubuntu and learning how the OS works, using the command line(terminal), etc.  Read relevant posts here in the forum.

---

### Post by Avenue on 2006-05-01
I hear you on reading the forum, i've been doing that since yesterday and I have tried a few things but nothing seems to work.  I did manage to find out how to create boot floppy, couldn't get that to work either.  I'm also using a second computer to read the forum while I troubleshoot on the computer behind me.

The hard drive that I am trying to install Ubuntu on is 5 gigs.  The real kicker here is that I actually DID install Ubuntu on this very same hard drive once before on my second computer.  

I may have to go in and look at the partition tables and see what's up.  

Thanks!!

---

### Post by manicka on 2006-05-01
[QUOTE=Avenue]

"**Invalid Boot Diskette  Insert Boot Diskette in A:"**
[/QUOTE]

Just a wild stab.. you don't have a floppy disc in the floppy drive do you?

---

### Post by confused57 on 2006-05-01
Well I'm back, couldn't sleep trying to come up with a solution to your problem...seriously I don't need much sleep,  need to get a life though.

Great that you have another computer you can use.  Go ahead and try the live cd with the 5 gig hd you want to put Ubuntu on.  You may want to try partitioning & formatting the drive using gparted(or is it qtparted?) from the live cd.  See this thread about using a live cd to rescue:

[http://www.ubuntuforums.org/showthread.php?t=167868&highlight=live+cd](http://www.ubuntuforums.org/showthread.php?t=167868&highlight=live+cd)

---

