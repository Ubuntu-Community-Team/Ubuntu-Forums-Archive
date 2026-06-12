---
title: "HELP! I think Ubuntu murdered my new PC"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-09-12
OK - so I got my new PC, with windows XP on it, and decided to make the switch to Umbutu.

The installation seemed to go fine - repartitioned disk, when I booted I could choose my OS - but I couldn't get online in ubuntu, only in windows.


I came here for help in [this thread]("http://ubuntuforums.org/showthread.php?t=548924&highlight=waste301").

I was following the instructions being given.  When I rebooted and suddenly it just said

**Grubb error 22**

I'm assuming that grubb is a bootloader for linux that lets you pick your OS on startup.

So I boot with the installation CD.  It gives me my startup options.  If I try the first run/install option it usually gives me anotherstrange error message.  I just tried it again, and it was slow, but I'm at the umbutu install desktop.

I'm posting this on my old PC.  Someone please help!  I was so excited to get my new box, and now I can't get to do anything.

---

### Post by CaptainInsaneO on 2007-09-12
First of all, breathe and relax. This is a minor error, trust me.

Try running fixmbr on your Windows disc, and check to make sure you don't have any external hdd's, thumb drives, etc. plugged in and running when you boot.

---

### Post by waste301 on 2007-09-12
I'd been using a thumb drive to move some files - I'll unplug it and reboot.

---

### Post by waste301 on 2007-09-12
It says:

Boot from CD :
FRB Loading stage1.5


GRUB loading, please wait....
Error 22

---

### Post by CaptainInsaneO on 2007-09-12
Take the CD out of the drive and reboot again. :popcorn:

---

### Post by LaRoza on 2007-09-12
You can try restoring the XP boot loader. This will allow XP to boot. Use the fixmbr method if you have the install disk, or use the Super Grub Disk.

Or you can use the Ubuntu disk to reinstall grub.

---

### Post by waste301 on 2007-09-12
> **CaptainInsaneO said:**
> Take the CD out of the drive and reboot again. :popcorn:

there was no CD in the drive.  I'm running my windows disk.  Should I open the recovery console?

---

### Post by waste301 on 2007-09-12
> **LaRoza said:**
> You can try restoring the XP boot loader. This will allow XP to boot. Use the fixmbr method if you have the install disk, or use the Super Grub Disk.

Or you can use the Ubuntu disk to reinstall grub.

I'd rather reinstall GRUB.  How do you use the disk to reinstall GRUB?

---

### Post by CaptainInsaneO on 2007-09-12
Oh, the output you posted said there was. Yep, go ahead and run recovery console and do a fixmbr on your Windows drive. That should fix it and grub should load. (I've personally used this solution.)

---

### Post by waste301 on 2007-09-12
Do you know the default administrator password for the recovery console?

---

### Post by CaptainInsaneO on 2007-09-12
No I don't. I think it might just be blank.

Anyway, it took me awhile to find it but here's a guide on reinstalling grub if you're still interested: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

By the way, welcome to Ubuntu! :)

---

### Post by Gremlinzzz on 2007-09-12
> **waste301 said:**
> Do you know the default administrator password for the recovery console?

:lolflag:some people in the forums suggest super grub i never used it 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by waste301 on 2007-09-12
> **CaptainInsaneO said:**
> No I don't. I think it might just be blank.

Anyway, it took me awhile to find it but here's a guide on reinstalling grub if you're still interested: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

By the way, welcome to Ubuntu! :)

Thanks for taking the time.  I hope I can get it to work!  Ill try leaving it blank.  If that doesn't work I'll try your link.  I'll post am update in a few.

---

### Post by CaptainInsaneO on 2007-09-12
Are you getting a password prompt for the Ubuntu livecd? Old versions used to use ubuntu for the username and a blank password, that doesn't work now though.

If you're talking about the Windows install disc (the one you should be using for fixmbr), I don't believe that has a password on it. I've never encountered one.

No worries, we'll get you fixed up one way or another. :)

---

### Post by waste301 on 2007-09-12
OK - no luck on finding the admin password for windows - it looks like its unique to the OS.

I tried using the ubuntu live cd.  The first time, it gave me an error message, and when I type I get double letters (I type help, I get hheellpp)

The second time, it loaded forever, the load bar went crazy and flickered all over the screen.

I've verified the CD, and it says that its fine.  

Any other suggestions?

---

### Post by CaptainInsaneO on 2007-09-12
Hmmm...

As far as your keyboard, that might be a BIOS issue. Try rebooting and going into your bios and finding something about typematic delay. If it's set, disable it, if it doesn't exist, I don't really know. Maybe someone else around here can put in their two cents?

You could try reinstalling Ubuntu. I really wish I was sitting at your computer, it would make this a lot easier. :(

Out of curiousity, who made your new computer and what are the specs? Maybe we can work from there.

---

### Post by waste301 on 2007-09-12
> **CaptainInsaneO said:**
> Hmmm...

As far as your keyboard, that might be a BIOS issue. Try rebooting and going into your bios and finding something about typematic delay. If it's set, disable it, if it doesn't exist, I don't really know. Maybe someone else around here can put in their two cents?

You could try reinstalling Ubuntu. I really wish I was sitting at your computer, it would make this a lot easier. :(

Out of curiousity, who made your new computer and what are the specs? Maybe we can work from there.


Update:  It took FOREVER, but ubuntu loaded off the CD.  I've opened the command console and would like to follo this advice from the thread you linked:

<i>1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"</i>
<b>4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).</b>
<i>5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.</i>


I am stopped at step 4, because I don't know how to determine the "root (hd*.*) for my PC - is it also 0,6?

The machine is a brand new Dell

Specs

1 223-1769 Vostro 400, Intel Core2 Duo CPU E6550 (2.33GHz, 1333FSB 4MB L2)
1 311-7366 2GB DDR2 SDRAM 800MHz, Dual Channel DT
1 310-9322 Dell USB Keyboard
1 320-5667 Dell 22 inch Wide E228WFP Analog Flat Panel Monitor
1 320-5760 256MB NVIDIA GeForce 8600GT 2DVI
1 341-4988 80GB Serial ATA Hard Drive 7200RPM, 8MB Cache
1 341-4742 No Floppy Drive Requested
1 420-7369 Genuine Windows XP Home
1 420-7243 CyberLink PowerDVD 7.0 DVD Playback
1 310-9440 Windows XP Home backup CD
1 420-7180 Dell Support 3.4
1 420-7286 GOOGLE SEARCH PORTAL ON
1 313-5798 Dell Resource CD, Vostro 400
1 310-9326 Dell Scroll Mouse
1 430-2501 Integrated 10/100 Ethernet
1 313-5469 No Modem Requested
1 420-7275 Adobe Acrobat Reader
1 313-5456 16X DVD+/-RW Drive
1 420-7241 Roxio Creator
1 313-5672 Integrated 7.1 Channel Audio
1 313-5461 No speakers
1 420-7189 DellNetwork Assistant 1.7
1 420-7262 No Pre-installed Security Software
1 420-7280 No Internet Service Provider Requested
1 420-7281 No Pre-installed Productivity Software
1 412-0359 Soft Contracts - Qualxserve
1 983-4250 Warranty Support,Initial Year
1 987-6849 No Warranty, Year 2 and 3
1 983-8540 Type 3 Contract - Next Business Day Parts and Labor On-Site Response, Initial Year
1 988-0387 Dell Hardware Warranty PlusOnsite Service, Initial Year
1 987-7479 VOSTRO,Datasafe 10GB,1YR(Incl w/price)
1 420-7368 Dell DataSafe 2.0 Online, 10GBfor 1 Year Free (for ABU only)
1 960-8851 1YR AUT. PC TUNE UP,VOSTRO, Included in Price
1 420-7367 PC Tune-up, 1 Year (For English OS only)
1 462-4506 Purchase is NOT intended for resell
1 310-8591 You have chosen a Windows XP System
1 310-8977 S and P Drop-in-Box Marcom forBSD Systems Box

---

### Post by Baby Boy on 2007-09-12
I was in a similar situation once - **GAG, the Graphical Boot Manager**, is bound to help. It's a miniature Linux OS you can use to boot your *screwed up* OSs.

[Link]("http://gag.sourceforge.net/")

---

### Post by CaptainInsaneO on 2007-09-12
I'm at work on a Windows machine right now so I'm not 100% sure of it's location but there is a hard disk monitor in Ubuntu. I believe it's under System>Preferences but poke around in the system menu and see if you can find it. Once you do it will come up with something that looks like Disk Management in windows. You can probably figure it out from there.

---

### Post by slira on 2007-09-12
Hi
before messing up with windows...

have you tried to reinstall ubuntu from the live cd? if it worked once, it should work again...

I had a similar problem, when (during an installation of ubuntu in a laptop) something went wrong; grub was not working... it seemed that no OS was there... the solution was to install ubuntu from scratch, using the live CD. after that all was fine...

you have another possibility; download DSL (dam small linux) and put it in a usb pen; then boot from there; you can gain access to all your disks and try to solve the problem, or, at least, understand what happened!

good luck!
slira

---

### Post by hessiess on 2007-09-12
did grub work perfectily untill you booted windows, then screw itself up? this is what hapnesed the furst time i used ubuntu, the supa grub disk was a real lifesaver ;)

---

### Post by waste301 on 2007-09-12
> **CaptainInsaneO said:**
> I'm at work on a Windows machine right now so I'm not 100% sure of it's location but there is a hard disk monitor in Ubuntu. I believe it's under System>Preferences but poke around in the system menu and see if you can find it. Once you do it will come up with something that looks like Disk Management in windows. You can probably figure it out from there.

I can't find it.

Ok - I've been learning about mounting drives.  I mounted my windows partition.  Under system volume information, th there is a file labeled restore.  I don't think that helps any but I'm putting it out there.

What I really need is a way to locate by boot sector so I can try that suggestion - Anyone who knows how to do this please respond.

> I had a similar problem, when (during an installation of ubuntu in a laptop) something went wrong; grub was not working... it seemed that no OS was there... the solution was to install ubuntu from scratch, using the live CD. after that all was fine...

you have another possibility; download DSL (dam small linux) and put it in a usb pen; then boot from there; you can gain access to all your disks and try to solve the problem, or, at least, understand what happened!

good luck!
slira


I am afraid to simply reinstall, because I've already repartitioned this drive once.  Is it safe to do it again?

> did grub work perfectily untill you booted windows, then screw itself up? this is what hapnesed the furst time i used ubuntu, the supa grub disk was a real lifesaver 

What is this supa grub and how do I get it?  No - I booted several timwes into both OS's before this happened.

---

### Post by hessiess on 2007-09-12
> 
What is this supa grub and how do I get it? No - I booted several timwes into both OS's before this happened.


here

[http://sgd.howto-linux.de/download/binaries/sgd/cdrom/sgd_current.iso]("http://sgd.howto-linux.de/download/binaries/sgd/cdrom/sgd_current.iso")

> I am afraid to simply reinstall, because I've already repartitioned this drive once. Is it safe to do it again?

you dont haft to repartition it, just install on the existing partition.

---

### Post by CaptainInsaneO on 2007-09-12
Try using the first method to reinstall grub in that link I sent you. That seems like it would be way easier than using the command line and/or reinstalling the whole OS.

---

### Post by slira on 2007-09-12
I am afraid to simply reinstall, because I've already repartitioned this drive once. Is it safe to do it again?

OK, but the live cd boots? if yes, you are safe! if not, we'll have to think...

with me it worked fine; you will have to do the partition work "by hand" and not use the automatic; be careful to avoid damaging windows when it arrives to the mounting points section

I'm at a windows machine now, I'm at work.... if you get in touch latter I could simulate the process in my own machine and give you step by step...

I'll check post this evening, ok?

(do not worry, you will manage!)
best luck
slira

---

### Post by CaptainInsaneO on 2007-09-12
> **slira said:**
> I'm at a windows machine now, I'm at work.... if you get in touch latter I could simulate the process in my own machine and give you step by step...

I'll check post this evening, ok?

I'm having the same problem, no Ubuntu in sight here. The U.S. Government, whom I work for, has not figured out yet that a FREE operating system is more stable and a better choice overall.

Sigh... someday. I'll check back later tonight too and try to help you out more!

---

### Post by waste301 on 2007-09-12
PROGRESS!

Made a Super Grub boot disk and successfully uninstalled GRUB and restored access to XP.  I can now get to my windiws desktop.

Next Step: Get back to Ubuntu

Should I reinstall GRUB?  Or should I use another boot loader like GAG that was suggested earlier?

---

### Post by CaptainInsaneO on 2007-09-12
If you really know what you're doing with Windows you can actually edit your boot.ini file to boot Ubuntu. If you prefer, of course.

---

### Post by waste301 on 2007-09-12
> **CaptainInsaneO said:**
> If you really know what you're doing with Windows you can actually edit your boot.ini file to boot Ubuntu. If you prefer, of course.

No thanks, lets not slap the monkey when its already angry.  I think I'll try the GAG bootloader, it looks solid.  I'm going to use my flash drive to put it on the new PC and install it from windows.

---

### Post by waste301 on 2007-09-12
OK - sorry for the long delay, but I've been trying various things.  Windows is running fine, but when I try to run the ubuntu installation disk this is what I get

BusyBox v1.1.3 (Debian 1|1.1.3-3ubuntu3) Built in shell (ash)
Enter 'help' for a list of built in commands.

[B]/bin/sh: can't access tty; job control turned off
(initramfss) [   33.434886] ata1.00: failed to set xfernode  (err_mask=0x40)

(repeats attempts with different numbers) ata2.00...err_mask=0x4[/B]


when I type I get double letters "help" becomes "hheellpp"

I burned a brand new installation CD and it still does this.

In windows there is a 20 GB partition listed as unallocated space.  I can't figure out how to install or uninstall umbutu on this partition, or why this is happening.

---

### Post by waste301 on 2007-09-12
Since the nature of my problem has changed, I'm going to start a new thread about it.  Thanks to evryone who helped me out here guys.  It was much appreciated.

---

### Post by CaptainInsaneO on 2007-09-12
Sorry I couldn't help more. Don't give up! Ubuntu really is an awesome OS once you get it all worked out (and your situation is NOT the norm, it usually installs without a hitch, so don't be discouraged.)

---

