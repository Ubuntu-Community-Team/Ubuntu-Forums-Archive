---
title: "Dual boot Dual hard drives"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Bigbluecat on 2006-09-17
Hi all,

Before I get into this long tale a big thanks to Herman. His Super Grub Disk guide saved me (plus the many other helpful posts).

I'm new to Linux and have just got Ubunutu dual booting with WinXP on two separate hard drives. I know there are lots of other threads about this (believe me I have read them) but it was still not a straight forward task. So, I thought it may be worth sharing my tale and solution (not especially pretty).

PC is custom built. Primary drive has WinXP (160Gb). Second drive is 250Gb WD. Both are Sata. I have an external Maxtor 160Gb drive that mirrors the primary.

First attempt was like a bull in a China shop. I did create a disaster recovery CD using Retrospect express (came with the maxtor drive)

Did the install on my second drive and expected to get a menu at boot to let me choose between OS's. Of course, it just booted to WinXP. I tired GAG as a boot manager which booted WinXP OK but Linux would not boot. Read some forum threads and realised that the bootloader did not seem to know anything about linux. Read about a method of re-installing grub using the Live CD. Tried it and fried it. Nothihng would boot (wife very unhappy). What's more the disaster recovery CD didn't work (nothing on the restrospect forums about how to test) so be very wary. We had belt and braces with the Maxtor HD backup anyway.This was my fault though. Not enough preparation and understanding.

Fixed windows boot with the recovery mode in the original CD. FIXMBR was not enough. Had to run FIXBOOT, then FIXMBR then BOOTCFG /rebuild.

Thought I would try a different approach that did not involve messing with windows MBR. This method is also listed here on the forums. So I took out the windows primary drive and made the 250Gb Seagate the primary and only drive. Installed Ubuntu and booted up like a charm. Then re-installed the windows drive as the secondary thinking I could now edit menu.lst to just point to it and use the map hd trick to fool windows it was in fact on the primary. However, after re-connecting the second drive the PC would not boot (dumped to a shell prompt with alerts). Still not sure what happened here - I think the drive numbering changed even though all we did was add a secondary drive.](*,) 

Swappped the drives back so Windows primary, Linux secondary.

At this point my wife thought she could fix things with the BIOS. She knows more about windows than I do. Anyway needed a new FIXMBR. No idea why and]( not going into that.](*,) 

So. What to do? Well after more research I decided that I quite liked grub and Super Grub Disk looked very interesting. Get it here [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) 

Also the following from Herman is invaluable [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Installed Ubuntu on secondary drive OK.
Booted with Super Grub Disk and began interrogating the system with the command line interface to make sure I knew where everything was.

Used null (hd and then hit Tab to get a list of drives.

Grub saw four drives hd0, hd1, hd2, hd3. I assume primary, secondary, CDROM and external.

Then did went searching for the Kernel.

find /vmlinuz gave the result (hd2,0). Good. this is what I would expect.

find /sbin/init also gave (hd2,0).

Also got confirmation that this was /dev/sda1.

I confirmed grub existed. 

So I did a manual install of grub IPL from (hd2,0) to MBR (windows drive).

Next I thought I would look at menu.lst.

What I found here was that all linux boot options were (hd0,0). Also Windows was stated as (hd1,0) not (hd0,0):rolleyes: I think this is one of the main reasons that dual boot with 2 drives is not straight forward. With this menu.lst the system would still not boot as it would be looking in the wrong place for the Kernel. It had to be changed but how?

So I did a manual boot from the grub command line - Thanks Herman =D> 

Once in Ubuntu I edited menu.lst to have linux root pointed at (hd2,0) and windows as (hd0,0). Made a few other adjustments and got out. 

Re-booted et voila =D> 

Booted WinXp as defualt.

Booted Ubuntu by choice (using now).

Now a very happy new Ubuntu user :biggrin:

---

### Post by Bigbluecat on 2006-09-17
One point I forgot to mention and this is really for Herman.

in SGD CLI I tried find /boot.ini to check where grub though windows was but it returned file not found.

So did find /ntldr

Not sure what why they could not be found as I can clearly now boot windows.

---

### Post by Herman on 2006-09-18
Congratulations, Bigbluecat, 
And thanks for sharing that great success story! You overcame quite a few hurdles to finally achieve success. Great work ! It's always nice to read that someone has benefitted from something I've helped with too. I must remind everyone now, though, it is adrian15 who is the developer of Super Grub Disk, and others who develop Grub itself, and of course Mr Shuttleworth and the Ubuntu developers too, who really deserve all the credit. I'm just someone helping users with some extra documentation. :D

I think it's much more fun to make documentation and see if it helps people than to play computer games or have some other hobby. When someone reports a success story like this, it's kind of like winning a game for me, or maybe, somewhat analgous to a fisherman catching a big fish. I imagine the software developers who might chance to read this thread will also be pleased. It's nice to read that someone is happy with the software. :D
>  in SGD CLI I tried find /boot.ini to check where grub though windows was but it returned file not found.
So did find /ntldr Do you have Windows with the FAT32, or with the NTFS filesystem, Bigbluecat? 
I suspect the failure of Grub to find the files has something to do with Windows having the NTFS filesystem.
I test all the commands myself before I add then to the website.  I tested again right after I read your post and I found that this works for my Windows XP FAT32 filesystem installation, but not my NTFS installation. So I'm trying to remember now if I did test this command for NTFS and it worked when I tested it, ...or not.... 

Can anyone else help me by confirming whether or not Grub can normally detect /boot.ini and NTLDR in an NTFS filesystem? Or if it does under certian circumstances or for some computers and not for others? 

Thank you very much for your feedback, Bigbluecat, because it is very helpful to me for making corrections to the site. That makes it better for other users in the future. I'll edit the site right away with a note that those commands might not work with NTFS. Thanks again. :D

All the best, and enjoy your Ubuntuing!
Regards, Herman :D

---

### Post by Bigbluecat on 2006-09-18
Hi Herman,

Thanks for the reminder. A big thankyou to Adrian15. Super Grub Disk is a superb boot utility and diagnostic tool. One that I will keep handy.

My WinXP file system is NTFS. 

I also noticed while using Grub CLI and interogating the disks with null (hd and tab that grub could not recognise the file system of the windows partitions.

Seems logical that grub cannot read NTFS disks.

I don't get much time to play and learn Linux and Ubuntu with work comittments so it will be a slow process for me. I'll post anything I think may be useful to the community and try to contribute what I can.

Regards

Bigbluecat

---

### Post by adrian15 on 2006-09-22
> **Herman said:**
> 
Can anyone else help me by confirming whether or not Grub can normally detect /boot.ini and NTLDR in an NTFS filesystem? Or if it does under certian circumstances or for some computers and not for others? 

Normal grub cannot read ntfs filesystems. There's a win32 grub that has the ntfs support although I think it has been removed from lastest versions.
Super Grub Disk has neither Grub filesystem support.

I could go to the win32 grub source code or try to search the ntfs patch for allowing Super Grub to be able to read NTFS.

But would it be useful? Maybe for booting this winxp installations that are installed on hda5? Or should it enough with a command that recognises that a given partition is a ntfs one?

Adding more functionalities to the grub core of Super Grub Disk (stage2) (not adding more menu.lst s) makes grub bigger and sometimes it implies that some kernels cannot be loaded or that the splashimage cannot be loaded. This is why I add features carefully.

For all that ones that tell me: Thank you for SGD: You're welcome.

adrian15

---

### Post by Herman on 2006-09-23
> Normal grub cannot read ntfs filesystems. There's a win32 grub that has the ntfs support although I think it has been removed from lastest versions.Super Grub Disk has neither Grub filesystem support. I could go to the win32 grub source code or try to search the ntfs patch for allowing Super Grub to be able to read NTFS. But would it be useful? Maybe for booting this winxp installations that are installed on hda5? Or should it enough with a command that recognises that a given partition is a ntfs one?
Adding more functionalities to the grub core of Super Grub Disk (stage2) (not adding more menu.lst s) makes grub bigger and sometimes it implies that some kernels cannot be loaded or that the splashimage cannot be loaded. This is why I add features carefully. Thanks, adrian15, it's nice to know. I think it's okay to leave things the way they are now unless the patch is really easy, and I doubt that. Editing the page was easy to do, now people should know if the 'find /ntldr' command doesn't work and their Windows has NTFS, that it isn't supposed to work anyway. Usually, people should be getting the right partition information from partitioning software anyway. The partitioning software and Grub disagree on how to name and number devices occasionally, and it can make booting quite difficult.  It is really neat that Grub can find out all those things though, for most filesystems at least. :D
Regards, Herman :D

---

### Post by videocheez on 2007-06-09
> **Bigbluecat said:**
> 

So I did a manual install of grub IPL from (hd2,0) to MBR (windows drive).

Next I thought I would look at menu.lst.

What I found here was that all linux boot options were (hd0,0). Also Windows was stated as (hd1,0) not (hd0,0):rolleyes: I think this is one of the main reasons that dual boot with 2 drives is not straight forward. With this menu.lst the system would still not boot as it would be looking in the wrong place for the Kernel. It had to be changed but how?

So I did a manual boot from the grub command line - Thanks Herman =D> 

Once in Ubuntu I edited menu.lst to have linux root pointed at (hd2,0) and windows as (hd0,0). Made a few other adjustments and got out. 

Re-booted et voila =D> 

Booted WinXp as defualt.

Booted Ubuntu by choice (using now).

Now a very happy new Ubuntu user :biggrin:

I have been reading your guide since I'm interested in doing the same thing.  I'm sure that by now you're an old Linux pro.  When i first started reading your post, I thougth that you were able to get dual boot without touching the Windows MBR butbased whats written at the start of your quote up above, you did alter the windows MBR.

Let me tell you what I've done so far to see if you have any advice:

Drive 0 and Drive 1 are SATA RAID 0 74GB WD Raptors
Drive 2 is an eSATA Non-RAID 74 GB Raptor (The drive I installed Ubunto onto)
Drive 3 is a SATA 250 GB Samsung Drive

I disconnected drives 0/1 and drive 3 and installed Ubuntu from Live CD to Drive 2 and made drive 2 the primary and made drive 0/1( the windows drive) the secondary. I reconnected the windows drive and when drive2 is powered on, I start my computer and it automatically boots Ubuntu. If I power off drive 2, the secondary Windows drive 0/1 boots. I think this is a dual boot setup but c'mon, I wanna  see grub give me the option of which OS to choose.  I'm fortunate to have an eSATA drive to play with linux on because it's convenient to just switch this drive off and boot to windows when I want to but I'm gonna wear out my hardrive switch with this kinda set up.;)

Any help, clarification or advice will be appreciated,

Thanks in advance ,
VC

---

