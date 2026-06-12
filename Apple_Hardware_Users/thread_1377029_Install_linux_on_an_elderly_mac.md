---
title: "Install linux on an elderly mac"
date: 2010-01-09
forum: Apple Hardware Users
---

### Post by Rexhunt on 2010-01-09
Hi first of all, if there is already a thread that coveres this could someone please direct me to it. I currently have an old powermac 7220/200 with all ehe origanl stuff except for the hard drive which is now a slightly larger one.
 
I was wondering if it was possible to set up a ubuntu installation on it using a 20g hard drive (I have got one of these going on a 486 running win98, just) and be able to run mac os as a dual boot system, possibly with 9.1 and the origanal mac os that come with it?
 
Unfortunantly I cannot connect this computer to any internet even if I had a card that was compatible with mac os.
 
I am happy to consider any os however I would prefer ubuntu, and if I am going to be picky, 8.04 as I am currently setting up a server sort of thing that is running this operating system.
 
Thanks in advance.

---

### Post by linuxopjemac on 2010-01-10
this is going to be a nightmare. If you are not afraid read on...
[https://help.ubuntu.com/community/OldWorld](https://help.ubuntu.com/community/OldWorld)

I did it and it's absolute horror to do it (PowerMac 7600 and PowerMac 7500 with Mandrake 8.2 and Debian/Lenny)

---

### Post by Rexhunt on 2010-01-10
Do you have any idea what the maximum size hard drive is?
 
Can I add a slave drive? I have half heartedly tryed this before but there is probably something that I would need to do apart from just plugging them in.
 
Sounds like an exciting challenge. Seeing as mum made me throw out a couple of my computers which I was playing around with this should take up my time nicley.

---

### Post by linuxopjemac on 2010-01-11
I added a slave in all the PowerMac machines, I don't know of a size limit though.

---

### Post by linuxopjemac on 2010-01-11
You need classic MacOS, otherwise you will never be able to boot. You need tools like Shrinkwrap in MAcOS, you will need a good browser in MacOS (iCab is the best). You will need a lot of patience and the will to learn...

---

### Post by linuxopjemac on 2010-01-11
By the way, this is the most recent thread on this subject:
[http://ubuntuforums.org/showthread.php?t=1330343&highlight=oldworld](http://ubuntuforums.org/showthread.php?t=1330343&highlight=oldworld)

---

### Post by Rexhunt on 2010-01-11
Ok thanks.
 
Is there anything special about putting a slave in? As I would like to have the origanal hard drive as well as the 20g one that I have in and working corrently.

---

### Post by linuxopjemac on 2010-01-11
yes there is, if it's a non-Apple drive, you will not have it recognised in the MacOS. I recommend installing everything on the smaller Apple drive and to mount the other one as ext4, maybe even as a /home from the installer. Beware also that this machine is excrutiatingly slow.

---

### Post by tiresia on 2010-01-11
> **Rexhunt said:**
> Is there anything special about putting a slave in? As I would like to have the origanal hard drive as well as the 20g one that I have in and working corrently.
1. The HD in those PPC are 50-pin SCSI HD. Be sure to configure correctly the jumpers and that you can see it in Mac OS 9

2. The processor should be a 200 MHz 604 Processor. It is quite slow, but it should work. It would be better if you find an Upgrade (I had a Sonnett Upgrade with 400 MHz and it made a big difference). Do you know how much RAM you got?

3. About GNU/Linux on Apple Old World Computers
Compared to GNU/Linux on Apple New World Computers the main difference is the booting process.
On an Apple NewWorld Computer the Installer creates an Apple_Bootstrap_partition (actually a hidden hfs partition) where **Yaboot**, the (Linux) Kernel Bootloader for NewWorld Computers is located. 
On an Apple Old World Computer **BootX**, the (Linux) Kernel Bootloader for OldWorld Computers, does not have an independent partition, but needs to start in Mac0S9 (or MacOS8/MacOS7).
_This means that you must make and keep a copy of the Kernel and of the boot ramdisk_ (initr.gz) on the Mac OS 9 Partition. Therefore during the Installation and each time you update the Kernel you must mount the Mac OS 9 partition and make a copy of the Kernel and of the initr.img

---

### Post by Rexhunt on 2010-01-11
Ok thanks again.
 
Can I mount the origanal drive through linux? It is just that there may be some files that I havent found time to look through and find.
 
Also I do realize that it is a slow machine. This is half of the reson for installing ubuntu, once this is installed I can use a similar method to install a less intensive operating system.
 
If you know of any that would be suitable for a complete newbie to use and set up could you please speak up. I haven't had much experiance with linux, at the most 6 months.

---

### Post by linuxopjemac on 2010-01-11
Linux is able to mount HFS and HFS+ files, so yes. beware that you need to make a partition on that drive to put Linux on. So you will have to format that hard drive. I would make a backup of your files first.

---

### Post by Rexhunt on 2010-01-11
Thanks for all the help you have given me.
 
I will probably try installing mac os 8 tomorrow afternoon as my os 9 discs won't install on this computer.
 
The hard drive and cd drive in this partiular powermac are ATA or IDE depending which way you want to look at it. Rather than scsi which as I understand is the more common interface.
 
I should be able to get around the problem of completly erasing the hard drive by putting it in a windows machine and using a cd that is in transit from an uncle adjust the size of the partition. There is not a minimum size for the linux partition is there?
 
Unfortunatly as I do not have a job just yet I cannot afford an upgrade of any description.:(
 
I think that it is only 128 or so ram and I cannot upgrad however my uncle said that he is sending some ram some of which hopefully will work in this machine.
 
And I understand about the need for bootx or similar as only apple has access to the neccacery code. *sorry for the bad spelling, school is out till the ned of the month*

---

### Post by lubod on 2010-01-13
If you have the 7220/200, here are teh specs:

[http://www.everymac.com/systems/apple/powermac/stats/powermac_7220_200.html](http://www.everymac.com/systems/apple/powermac/stats/powermac_7220_200.html)

I've never worked on a 7220, but it is mostly the same as the 4400, so they say on that page.

The HD is indeed IDE/ATA and the CD probably is too. It should be capable of using Mac OS 9 (at least 9.0 maybe not 9.1, I seem to recall 9.1 orphaned and left behind some Powermacs that had been supported in 9.0). Not positive, but I suspect a second drive is unlikely, the ATA controller in, for example the Beige G3 (also Old World, but newer than the 7220) can only handle one drive, no slave. Unconfirmed, but I suspect yours may have similar limitations. Maybe a PCI ATA card when you have the chance? I also suspect that like other later models (G4 even) it can only handle 128Gb drives or less (no LBA).

RAM should be EDO or FPM type, absolutely ancient by todays standards :-) Before PC100, I think it is even referred to as PC66! More specs on the page for that.

This is one of the so called "Old World" Powermacs (the beige, non colorful ones). I see tiresia covered this very succintly (misspelled initrd.gz as initr.gz, here's the longer explanation :-) The boot sequence is like this:

Hardware ROM (on the motherboard) loads any available "blessed" System folder, and runs the Mac OS inside. The Mac OS install CD blesses any Mac OS it installs, but it is actually documented well enough that one can do it inside a Mac OS X terminal to fix a dual boot Mac OS 9/X configuration so 9 will run again. And Linux first stage booters fool the Mac into thinking the Linux second stage booter is a blessed system folder, and the linux kernel is the Mac OS, and it boots. (Not sure if I got every detail exactly, but in a general sense pretty close)

On colorful "New World" Macs, there is no hardware ROM it is a file in the filesystem called "Mac OS ROM" inside the System folder.

Both Old and New World have Open Firmware (kind of like a BIOS, but more capable/configurable, it can actually be programmed in a language called Forth)

There are several bootloaders for Linux, and other OSes (OpenBSD, etc.) use their own or port from NetBSD or elsewhere. Mac OS X also has a bootloader, confusingly called BootX, just like one of the Linux ones.

Linux for PowerPC:
BootX - requires a HFS partition with working Mac OS install, kernel and ramdisk must be copied to this partition during install and after every update - Old World only
miboot - BootX without the GUI, all settings are stored in a text file or hard coded into booter's resource fork - Old World only
yaboot - creates its own HFS partition, no Mac OS required - New World only
quik - uses kernel on HFS partition even if no Mac OS present, settings stored in OpenFirmware (think BIOS) - Old World only (I think)

I'm making a custom CD for this, but it's going in its own thread, not going to threadjack yours. :-)

---

### Post by tiresia on 2010-01-13
> **lubod said:**
> I've never worked on a 7220, but it is mostly the same as the 4400, so they say on that page.
The HD is indeed IDE/ATA and the CD probably is too.
Not sure but those motherboards should have also a SCSI connection. In my beige G3 I installed this way a second HD


> I'm making a custom CD for this
I would be very interested in

---

### Post by Rexhunt on 2010-01-13
The hard drive and cd drive are indeed both ide.
 
I origanlly got this computer from my uncle. He had mac os 9.1. The os that I am using is 8.0 because none of my mac os 9 discs will work, unfortunatlly.
 
The ram is indeed ancient, as I belive even by the standards of my computers (all sdram except for 128 mb on the test rig which is ddr but not 2 possibly one?).
 
I have a couple of small sticks of sd that fit in the slots, is there a way that I can use them? The slots are labled as dimm.
 
Is it possible to have any additional mac os's installed and selectable? Just because I like being able to do things like that.
 
I currently have bootx installed and is running the ubuntu 8.04? alternate install disk. This afternoon I should get a chance to run the setup again and use a different method to copy the kernel.
 
There is an external scsi connector, however I don't have anything to use with it and I cannot afford to buy anything
 
I would also be interested in the cd.
 
Thanks for the interest you have shown in this thread

---

### Post by linuxopjemac on 2010-01-14
I would certainly put as much RAM in it as you can find, 256 is minimum I'd say. If you make more partitions for MAcOS, you can have more than one MacOS. From within MacOS you can select the Startup Disk. There you can point to the other MacOS. Keep in mind though, that if you want to boot another MacOS and then Ubuntu, that you either have to boot in MacOS with BootX installed or to also include the whole setup in the other MacOS.

In which CD are you interested ?

---

### Post by Rexhunt on 2010-01-14
I agree that as much ram as is possible is best. However I don't currently have any that is compatible with this particular computer.
 
The CD that I am interested in is the one that lubod mentioned.

---

### Post by lubod on 2010-01-26
My custom "Old World" CD is ready, after several days (or was it nights?) of burning the candle at both ends as they say. :-)

I set up a Google-site for it. In the "Files" section you can find CD images in toast and dmg format, so a Mac booting Classic Mac and Toast or Mac OS X (10.4 verified, 10.3 or 10.2 should/may work) and Disk Utility is required to burn the image at present. The link goes to an external host, namely dropbox, because the google site only offers 100Mb vs 2Gb for dropbox, which is why it says view, but that link actually triggers a download.

I know others have done this kind of thing with other Linux distros in ISO format, but I do not know all the ins and outs of making ISOs that are bootable on a Mac. As it is the mastering process was quite, uhm 'challenging' yeah that's the word I'm looking for...

But being a Mac-head even longer than a Linux fan, I got it working to boot directly from the CD, and also included BootX for those that can't/don't want to wipe the Mac OS partition.

Two flavors both based on the net install Mini-CD (these boot from the CD, load it into RAM and download the rest of whatever you choose to install from any available network interface): 

Pico (barely bigger than the 'New World only' official mini-CD)
Nano (about twice the size, but with the kernel and ramdisk you would otherwise have to copy into your Mac OS partition already included, plus lots of Mac OS goodies to make everything smoother/more painless)

Please report success/failure so I can expand the compatibility table. And of course if the download works :-) MD5 sums included in text file.

Enjoy and pass on to any Mac person who thinks throwing a working Mac away because Apple wants them to buy a new one is a waste:

[http://oldworldpowermacs.homeip.net/](http://oldworldpowermacs.homeip.net/)

P.S. Hopefully a forum moderator will sticky this or at least link to it from the threads like "where to download Ubuntu PowerPC".

P.P.S. I see in my haste to reply I unintentionally broke my promise not to threadjack. If you'd like me to start a new thread about the CD, please reply. Otherwise I'll leave the thread as it is.

---

### Post by linuxopjemac on 2010-01-26
Fantastic initiative!! I will post a link on my site!! I have a friend with a 7600 on which I installed Lenny. Maybe he can try to test it. I will ask him.

---

### Post by lubod on 2010-01-26
Thanks for the compliment, I should mention I ran across your site in my research and it was one of the more informative and updated ones on the subject of Linux PPC. A bit too "New World" oriented for my tastes, but not because I dislike newer Macs just that I think I like the older ones better :-) I still regret parting with my old Quadra 650, it was a very modded beast in a PC case, clocked up to 40Mhz, it beat Powermac 6100/60 at some tasks. I once played Marathon on an Appletalk network and the Powermacs lagged the game more than the Quadra did. And did I mention it could run A/UX? Yes, OS X is Apple's third foray into Unix! A/UX was the first, the Apple Network Server with AIX was the second.

I suspect it is that way mostly because "Old World" information is harder to get without actually having the increasingly rare hardware to try it with.

P.S. Already been tested with the 7600, it works, the built in video is a bit quirky (dark low contrast text on black background) but with the shift key or video=ofonly it behaves mostly, and PCI video cards also help. But your friend is welcome to try in any case, that is why I put it together. :-)

Lenny is Debian 5.0, from Sep. 2009 right? Karmic is about the same from Oct. 2009, maybe a few unstable type package newer but not much else I imagine.

---

### Post by linuxopjemac on 2010-01-26
> Lenny is Debian 5.0, from Sep. 2009 right? Karmic is about the same from Oct. 2009, maybe a few unstable type package newer but not much else I imagine.

Karmic Koala was issued 2009-10-29 and Lenny 2009-02-15, so, Karmic is a bit newer.... :)

---

### Post by linuxopjemac on 2010-01-27
To come back to the issue of converting .dmg to .iso, you can try the following in OSX:

```
hdiutil convert /path/to/filename.dmg -format UDTO -o /path/to/savefile.iso

```
Replace /path/to/filename.dmg with the path and name of the existing .DMG
file, and replace /path/to/savefile.iso with the desired path and name
for the converted image.

This then creates an ISO image burnable in Nero on Windows, or pretty
much anything on Windows that will burn ISOs and same with Linux.

---

### Post by lubod on 2010-01-27
Nice, I'll try that! I'm apprehensive that while the files will be intact, the .iso image as a whole might not be bootable like the .toast and .dmg are. 

I say that because the original image was .toast, and converting it to .dmg in the Disk Utility GUI made it unbootable, only converting in Toast to .dmg (they call it compressed, it's a little checkbox in the save as disc image dialog) worked so far. Hence I suspect any conversion in Disk Utility (GUI or CLI) might mess up the bootable aspect of the image.

But hey, it's worth a shot, as you say .iso is easier to burn without having a Mac to burn CDs with.

---

### Post by Rexhunt on 2010-01-29
Does anyone know if there is a kernel argument (I think that's what they are called) for the video on a slotloading iMac?

---

### Post by linuxopjemac on 2010-01-29
> Does anyone know if there is a kernel argument (I think that's what they are called) for the video on a slotloading iMac? 

Your machine is NewWorld. You need a NewWorld installer (basically any of the distributions) leading to a bootloader with yaboot, but certainly not the OldWorld installer using BootX.

---

### Post by Rexhunt on 2010-01-29
I thought that the CRT slot loadiing iMacs that came with only a 6 GB hard drive were old world? And don't new world machines need to run mac osx?
 
Also on the 7220/200. I am using the 8.04 alternate installer and when I go into a terminal window, when the installer comes up with the screen saying that it can't install a boot loader, I then type "df" (without the quotes) to show the partitions on the hard drive. However it will only recognise the new linux partitions, not the mac os ones that showed up in the partitioner?
 
I will try the cd mentioned above as soon as I can  get it burned as I need to convert it on a windows computer.
 
I will let you all know what happens once I have tryed this.

---

### Post by Rexhunt on 2010-01-29
Sorry my bad the iMac is indeed a new world computer. Just ran the installer from the cd holding down "c".
 
Thanks for pointing me there.

---

### Post by Rexhunt on 2010-02-01
Ok all of my ppc downloads are a little flakey.
 
However I can boot into Ubuntu 8.04. Is there a way to install a bootable system with a slightly dodgy set of base system installers? Unfortunatly I cannot have internet in the room with the iMac in it however I am campaigning to get something set up.

---

### Post by linuxopjemac on 2010-02-01
Rexhunt: please try Debian Lenny, it saves you a lot of time.

---

### Post by Rexhunt on 2010-02-01
Ok thanks, will give that a go when I get a chance to download it.
 
Is there a way to check the integrity of an iso image on a windows machine?

---

### Post by Rexhunt on 2010-02-06
I just got the powermac 7220/200 going with linux on it, however I haven't been able to fix the problem with the contrast?
 
And just to make sure that I haven't stuffed up majorly, do alternate installers come with a GUI, because I don't have one?
 
Thanks for all your help, you have made it possible for a high school student to acheive what many would baulk at, so thank you, all who have contributed in some way, even just helping the people who have posted here.

---

### Post by linuxopjemac on 2010-05-02
Did the website disappear ??

---

### Post by lubod on 2010-08-19
Sorry, hadn't checked this thread in months.

Old address was redirected via dyndns, needs to be relinked to work properly.

Directly accessible at:

[https://sites.google.com/site/oldworldpowermacs/home](https://sites.google.com/site/oldworldpowermacs/home)

P.S. Still haven't gotten around to making similar mini-CD for Lucid, but plan to, since it is an LTS release and therefore should be relevant for about 3 years (desktop) and 5 years (server).

---

### Post by linuxopjemac on 2010-08-19
Lubod: thanks. I adapted all links on my website, it works now.

---

### Post by Rexhunt on 2011-12-22
Unfortunatly due to space and parental requirements the powermac had to be thrown out, negating this conversation...

---

