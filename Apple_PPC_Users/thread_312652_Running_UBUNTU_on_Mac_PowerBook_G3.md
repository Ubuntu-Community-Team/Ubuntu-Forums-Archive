---
title: "Running UBUNTU on Mac PowerBook G3"
date: 2006-12-04
forum: Apple PPC Users
---

### Post by Windows_Apple_Linux on 2006-12-04
Hi all,

One day I was going to fix someone computer, then this lady gave me her laptop a Mac Os power book G3, Now, I want to install Linux on it... I tryed the cd's on it but it doesnt work, I don't have the original OS cd....I tryed the following combos


CMD-OPT-SHIFT-DELETE 



from [http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.shtml](http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.shtml)

But it only show a floppy disk on the screen with a " ? " sign on the middle...  so how can I install Linux on it?? 

please, please, please I really need help 


I had already download/burned the lastest Ubuntu PPC
which is: [http://mirror.cc.columbia.edu/pub/linux/ub...top-powerpc.iso](http://mirror.cc.columbia.edu/pub/linux/ub...top-powerpc.iso) 

this is the way I had burned the cd:
with Nero

Select Copy and Backup. Click Burn Image to Disc 
Choose Recorder 
Select the ISO to burn. 
Click Burn 


How what do I have to do to install UBUNTU on my Powerbook G3
[IMG]http://www.oldmac.jp/image/pbg3-01.jpg[/IMG]

P.S: yeah it is a really old pc.... But I want to use it. 


Thanks
MSN: [email]hugovalenca@hotmail.com[/email]

---

### Post by stream303 on 2006-12-04
I'd try burning at the very lowest speed possible.  Also try using various brands of CD.  Does the cd actually work with OS/9?  (did you burn it on this machine?)

---

### Post by Windows_Apple_Linux on 2006-12-04
Nope, I had burned the ubuntu ISO CD on my home computer (Windows) not on the powerbook G3, I don't have the original OS/9 CD :-| And I had tryed with a couple of others linux, but they didnt have PPC, I tryed Windows but no luck. Now I had tested the CD-ROM with a couple of CD musics and it worked

---

### Post by matt_risi on 2006-12-04
The floppy disk question mark deal means either it's unable to locate the file system, or your hard drive is fubar. I'd probably go with the latter. 

If I'm correct, your computer either has a 400 or 500 mHz processor, and 64 or 128 megs of RAM. ..this won't do for ubuntu buddy.

Best case scenerio is that you get a working server install of ubuntu (using a ppc alternate iso), then installing something like Xubuntu-desktop or icewm. Even then I'd recommend a RAM upgrade.

So if you REALLY wanna run Ubuntu, I as well as this whole awesome community will help you out, but I personally recommend you find out what the native version of Mac OS is for that model and throw that in.

Best of luck.

---

### Post by Windows_Apple_Linux on 2006-12-04
So you mean that I should get Xubuntu & IceWM instead of ubuntu?

---

### Post by dpny on 2006-12-04
> **Windows_Apple_Linux said:**
> So you mean that I should get Xubuntu & IceWM instead of ubuntu?

I run Ubuntu on a 500 MHz Powerbook G3 with Gnome. I would upgrade the RAM, though. You can get a 512 stick for not much from macsales.com.

---

### Post by matt_risi on 2006-12-05
Sorry, I think I was a little unclear.

What you do:

Download PowerPC release of Ubuntu 6.06.1 ALTERNATE (Very important) and burn on a low speed setting as a bootable ISO.

When prompted on bootup of your beloved Powerbook, install Ubuntu Server Edition. (Very easy, just follow the prompts.)

It'll reboot and you'll be greeted by a lovely bash prompt.

Type: "sudo apt-get install xubuntu-desktop" .

That's it.

---

### Post by samden on 2006-12-05
You may find that the Xubuntu live cd runs on the computer, depending how much ram it has. The Xubuntu live cd runs on my G3iMac (just!) but the Ubuntu one will not. Might be nice to try, to see what it looks like. To actually install though you will be better off with the alternative cd.

I have been gradually installing Ubuntu 6.06.1 on my iMac over the past 3 weeks and hitting more problems than I expected - so expect to run into unexpected difficulties, but I gather that is what Linux is like! Best wishes, and there are lots of threads here to search if you run into any specific problems, I may have run into quite a few you may hit!

By the way, have you been unable to get any Linux cd to do anything on the computer? Do you know to hold down the c key while booting to get it to boot from the cd rather than the hard drive? This should get rid of the flashing question mark and let you run the cd. If the question mark is flashing simply because Mac OS isn't working, that's ok, you should be able to do a clean install of Ubuntu only on the hard drive. If it is flashing because the hard drive is gone you'll have a few more problems...

---

### Post by Funk Soul Brother on 2006-12-05
Well - I installed Xubuntu on virtually the identical laptop and have enjoyed every success. The one major drawback for me, however, was that Adobe/Macromedia has not released a Flash Player for Linux on the PPC architecture. This is a solid BUMMER as I'm a web-head and Flash is still the de-facto vector and rich media platform for web delivery. Oh well.

---

### Post by matt_risi on 2006-12-05
Mother of God I didn't know that. How unfortunate! I remember what it was like to have to use the older version of flash when I first started using dapper back in august. Yikes, I hope Adobe or better yet someone from the community can do something about that.

---

### Post by Windows_Apple_Linux on 2006-12-05
When I turn on the pc, I hold down the " C " but nothing happens, I'm downloading Ubuntu 6.06.1 ALTERNATE.,  I will burn it using Nero with the lowerst speed, then what key should I press so It boots from the CD?

---

### Post by Windows_Apple_Linux on 2006-12-05
No, luck, I had tryed the same combo up top (on my first post), hold down c, but still didnt work, I had corrently burn the Ubuntu 6.06.1 ALTERNATE, but it doesn't work on the MAC, when ever I put the cd on the cd-rom, it just loads normaly, then i get a message if I want to eject the disk or Clean the disk ( which mean format it) I will try to download Xubutu and see if what happends, I had tryed a couple of other Linux such as Kurumin, Freespire, and some others, but no luck

---

### Post by Windows_Apple_Linux on 2006-12-05
and what about BootX?? how can I use it, will it help me install Linux on it?

---

### Post by stream303 on 2006-12-05
I'm wondering if the program used to burn the iso's (Nero?) is doing it properly. How old is that Nero?  Are you burning in the iso9660 format?

---

### Post by samden on 2006-12-06
> **Windows_Apple_Linux said:**
> No, luck, I had tryed the same combo up top (on my first post), hold down c, but still didnt work, I had corrently burn the Ubuntu 6.06.1 ALTERNATE, but it doesn't work on the MAC, when ever I put the cd on the cd-rom, it just loads normaly, then i get a message if I want to eject the disk or Clean the disk ( which mean format it) I will try to download Xubutu and see if what happends, I had tryed a couple of other Linux such as Kurumin, Freespire, and some others, but no luck
I might be nit-picking, and I could be completely wrong, but I am not entirely certain you are following the correct procedure to boot from cd. If nothing is booting at all from cd, whatever distro you use, it does cast some doubt on the procedure you are using to boot from cd - you would expect something to work.

Don't worry about the cmd-option-shift-delete for a change (I assume this is what you mean by "the same combo up top"). Just insert the cd, let it load or do whatever it likes, as long as the cd is in the drive. Then reboot with the cd in the drive - you may have to hold down the power button to reboot, or push the reset button if the powerbook has one. As you reboot, hold down the c the entire time. Technically it only needs to be down for a shorter time, but to make sure you are doing it right hold it down from the time you press reset till the computer finishes booting and ideally you get some writing on the screen about Ubuntu.

I get the feeling you are turning on the computer, THEN inserting the cd, holding down c and expecting it to boot from the cd. This probably WILL NOT work, the computer must start up with the cd in the drive.

If your computer is older than I realise, you may have to use cmd-option-shift-delete instead of c. (Note that I have never used this combination before, only c). But if so, this will again need to be held down while the computer is booting with the cd already in the drive. Try c first - your computer isn't really that old!

If this sounds very obvious, and you know all this, sorry. I have no idea how much experience you have with Macs so am stating the basics.

---

### Post by Windows_Apple_Linux on 2006-12-06
i know that i had correctly burn the iso file, because my others Linux cd's work on my home pc (Windows), I also have the cd on the machine while pressing " c ", but nothing works, Now when I try with Freespire, the pc locates the cd, and it allows me to open up on the mac

Lindows
[IMG]http://img114.imageshack.us/img114/1162/picture001dh7.jpg[/IMG]


Ubuntu Altimante
[IMG]http://img237.imageshack.us/img237/6914/picture002hs8.jpg[/IMG]


Holding down " C " with frespire/ubuntu on the cd-rom
[IMG]http://img237.imageshack.us/img237/3087/picture003cw9.jpg[/IMG]
MAC starting up


still holding the c bottom down
[IMG]http://img237.imageshack.us/img237/8947/picture004iq4.jpg[/IMG]
Mac happy computer face apperes and start loading


power button on and holding CMD + OPTION + SHIFT + DELETE
[IMG]http://img237.imageshack.us/img237/8599/picture005vx2.jpg[/IMG]
with the Ubuntu/freespire cd on the pc


CMD + OPTION + SHIFT + DELETE
[IMG]http://img237.imageshack.us/img237/6298/picture006cy1.jpg[/IMG]
happy mac computer faces shows up - with the Ubuntu/freespire cd on it

---

### Post by Windows_Apple_Linux on 2006-12-06
ok update, Now my mac is finding the cd-rom, it allows me to open the cd on the machine, I see, the file ' Install ' folder but I tryed everything but no luck

Now I had tryed the combo 
CMD + OPTION + SHIFT + DELETE 

and the floppy disk with the '?' on the middle...that's all

---

### Post by jaradronald on 2006-12-06
Are there any USB Ports on the Laptop? If not, it's true old world, and you'll need to put BootX under OS 9.2 & use that to boot a Linux Kernel & Init_Ramdrive. See the following for the details:
 
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)
 
Oh, and definately install Ubuntu 6.10 - Alternate Installation CD, Do a base install (no gui), then add the base desktop using the following commands:
 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
 
You can use the following to reset your root password without the gui:
 
sudo su
password: ******
passwd
New password: ******
Confirm: ******
 
Something like that...
 
Go ahead and go with the Ubuntu Install (Xubuntu isn't much faster as it uses the same gnome libraries). Kubuntu is pretier, but if you can don't install any packages with KDE dependencies (if you load these "Dynamic Linked Library Sets" then the Desktop will slow WAY down). And don't forget to max out your system RAM.

---

### Post by Windows_Apple_Linux on 2006-12-06
their is no USB connections on the PB G3, also my operating system is MAC OS 8.1, I tryed to install OS 9.2 but it didnt let me, I'm updating the ram from 32MB to 128 MB

---

### Post by jaradronald on 2006-12-06
> **Windows_Apple_Linux said:**
> their is no USB connections on the PB G3, also my operating system is MAC OS 8.1, I tryed to install OS 9.2 but it didnt let me, I'm updating the ram from 32MB to 128 MB
 
What disk did you have for OS 9?  I have an iMac Install, & it loads on my PB G3 just fine.
 
I don't think you'll be able to run a GUI in Ubuntu with 32 MBs of RAM.  You can do a base system install no problem though.  Do you have BootX Loaded under OS 8?

---

### Post by StanObuX on 2006-12-06
I'm typing this from the exact computer you are trying to install.  Now I'm going to be honest. . .  When I first tried to install I got all these error messages on live boot.  Bunch of crap about Gnome and some applet and nautilus or something.  Then I gave up for a little while, came back decided to type 'live-powerpc' to install from live cd.  Install worked.  Ran for a day till I screwed up installation trying to do various things (I like things clean and optimal).  Then I reinstalled from live cd, but tried regular install.  Works like a charm.  The problem I am having is on the rev2 Powermac G3 Blue & White. Gives me the same issues as with the laptop, but niether live cd or alternate installation cd works.  After I installed on B&W from alt cd, rebooted and then the Ubuntu screen (like at beginning of live cd) but nothing happens.  One notch on the load bar.  I walked away and came back an I was at some weird comman prompt (I assume Apple's or something)  Didn't know what to do so now I'm searching just like you.  But no worries, WILL WORK ON YOUR LAPTOP!!  (-;  Edgy runs pretty darn well too!

Hotep



"The light shines within.  Let it shine brightly for all to see"

---

### Post by StanObuX on 2006-12-06
Dude, the PPC in the first picture is NOT the same as the PPC in the second picture. . .  the one in the second picture looks much older.  I have the one that looks like the one in the first picture.  Doesn't look like it'll run on the second one though. . .


Hotep



"The light shines within.  Let it shine brightly for all to see."

---

### Post by jaradronald on 2006-12-07
Ubuntu 6.10 will run on the pictured G3 just fine. I'm running the same Old World G3 with 128 MBs of RAMs. I used the PPC 6.10 Ubuntu Alternate Install (for systems with less than 192 MBs of RAM). I never used the "Live Boot" CD as my "Old World" Mac (pre Openfirmware System) has to boot using the BootX Plug-in which is run in the first stage of OS9 boot. It's all outlined in the link I sent before:
 
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs) 
 
You have to copy the kernel & init_ramdrive to the OS 9 Partition and then boot them using BootX & point the root to the linux ext2/3 partition (/dev/hda12 on my Powerbook G3).
 
I do have to say that Ubuntu 6.06 never installed with the correct driver set for me on my Powerbook G3.  The 5.10 distribution of Ubuntu worked well, but 6.10 is actually working out the best for me.  I've tried all three flavors on this system at one point in time (XFCE, KDE & Gnome) and I prefer Gnome (Ubuntu) on this system.

---

### Post by Windows_Apple_Linux on 2006-12-07
> **jaradronald said:**
> What disk did you have for OS 9?  I have an iMac Install, & it loads on my PB G3 just fine.
 
I don't think you'll be able to run a GUI in Ubuntu with 32 MBs of RAM.  You can do a base system install no problem though.  Do you have BootX Loaded under OS 8?

Nope, I don't have OS 9, well I got the cd for Mac OS 9.2 but it doenst allow me to install. 

Another question, will ubuntu format my HDD?? because I only have 1.4 GB left..

---

### Post by handylinux on 2006-12-07
Just to clarify for those not familiar with Macintosh history: There were three PowerBook G3 models, released in 1998, 1999, and 2000. Superficially they look quite similar, but there were important differences between the models.

The 1998 model, officially "PowerBook G3 Series" (there were some six variants released during the year), commonly called "Wallstreet" (the Apple internal "code name" of the late-1998 series during development), was a classic Macintosh, with ADB and serial ports (no USB ports), and SCSI port (no FireWire). It was also thicker and heavier than the subsequent models, and offered low-cost versions with small (12" and 13") displays. These models ran at from 233MHz to 300MHz, came originally with Mac OS 8.0 or 8.1, and can run up to 9.2 (?), or OS X 10.2.x.

The 1999 model, officially "PowerBook G3 (Bronze Keyboard)", commonly called "Lombard", was thinner and lighter than the 1998 model, and replaced the traditional Mac ADB and serial ports with USB ports, but still had a SCSI port rather than FireWire. Another change is that it was no longer bootable from the PCMCIA slot. There were two 1999 models, at 333MHz (with a CD-ROM drive) and 400MHz (with a DVD-ROM drive); they came originally with Mac OS 8.6, can run up to 9.2 or OS X 10.3.x (which requires USB).

The 2000 model, officially "PowerBook G3 (FireWire)", commonly called "Pismo", was identical in size, shape and weight to the 1999 model, but replaced the SCSI port with two FireWire ports. There were two models, 400MHz and 500MHz; they came originally with Mac OS 9.0.2, can run up to 9.2.x or OS X 10.4.x (which requires FireWire), though most users feel 10.3.9 runs best. This was the culmination of the PB G3 series, the one where Apple finally "got everything right", and is widely considered one of the best computers Apple has made.

(There was a fourth, original PowerBook G3 in 1997, a.k.a. "Kanga", which was basically an upgraded PB 3400, different otherwise from the 1998-2000 series.)

From the photo in the first post, this is a 1998 model PowerBook G3 -- as later confirmed by the info that it has no USB ports. The later photos are not inconsistent; this is one of the cheapo models with a small display. I was going to say that this model won't take Mac OS 9.2.x, which was a late update to OS 9 mostly for use as the Classic environment in OS X; but according to [Low End Mac]("http://www.lowendmac.com/pb2/g3series.shtml") it will, so I'm not sure why 9.2 won't install on this computer. I would usually put 9.1 on it, unless OS X was desired and the owner was willing to live with its limitations on this machine (very slow, can't run any version later than 10.2.8 without hacks, small display really inadequate).

And holding down the C key during startup should start from a CD, unless there's something wrong with the CD (or the optical drive). If C doesn't work, CMD-OPT-SHIFT-DELETE is not likely to help. And yes, it is an "Old World" G3 Mac, similar to the "beige" (actually platinum) desktop models, and thus requires different Linux installation procedures than the later models. jaradronald's post above links to the, unfortunately, rather complicated instructions. As the instructions note, a 9.2 installation CD that came with a later model Mac might not work with this earlier model; what you'd need would be a generic (i.e. retail) 9.x CD, not tied to any particular model.

---

### Post by Windows_Apple_Linux on 2006-12-07
UPDATE: now my PD G3 wallstreet, doesnt want to open the iso files, I had tryed the MAc os 9.2 cd and it worked, also a couple of music cd's and it worked, but when I put the ubuntu Altima. it asks me if I want to eject disk or format disk :(

---

### Post by Windows_Apple_Linux on 2006-12-07
UPDATE: Now I only get the floppy disk with the question mark on the screen...it doesnt load the OS....and it still doesn't boot from the CD :(

---

### Post by samden on 2006-12-08
Handylinux, that is a great summary. Thanks - I didn't quite understand what people were calling a Pismo or Wallstreet - you have clarified the whole situation up a lot.

I remember when the iMac first came out and I was frustrated it didn't have any ADB or serial ports and I couldn't use the old hardware I had accumulated over the years... funny how things change. I've got a big pile of old Macs (a powermac, LCII, Performa, Powerbook 150) etc back at home, and now I am unlikely to ever really use them, unless I eventually get one going for my kids to play with before they are old enough to realise that their flash computer is actually 15 years old and their friends are laughing at them... It is still hard to beat a Performa with At Ease for an easy-to-use childs computer.

---

### Post by gurnemanz on 2007-01-03
[SIZE="3"][SIZE="4"][COLOR="Green"][SIZE="4"]On a G3 500 mhz Pismo, with 500 meg and the HD partitioned per the recent MacAddict article by Strohmeyer, with OSX on 2nd partition - no joy.

I downloaded and burned a cd to an outboard Sony DRX-820UL-T DVD/CD. The 'hold down c at startup' sequence never launched anything from the cd.

Has anyone successfully booted a Pismo Powerbook from the cd or a disk image on an outboard drive? Or on an empty partition on the internal HD? It will be two or three more weeks before I can replace the internal CD/DVD drive in the Pismo, which may have shot craps . . .

Thanks, folks -

gurnemanz[/SIZE][FONT="Georgia"][/FONT][/COLOR][/SIZE]

> **handylinux said:**
> Just to clarify for those not familiar with Macintosh history: The 2000 model, officially "PowerBook G3 (FireWire)", commonly called "Pismo", was identical in size, shape and weight to the 1999 model, but replaced the SCSI port with two FireWire ports. There were two models, 400MHz and 500MHz; they came originally with Mac OS 9.0.2, can run up to 9.2.x or OS X 10.4.x (which requires FireWire), though most users feel 10.3.9 runs best. This was the culmination of the PB G3 series, the one where Apple finally "got everything right", and is widely considered one of the best computers Apple has made.[SIZE="4"][/SIZE][/SIZE]

---

### Post by jaradronald on 2007-01-04
[COLOR=#666666][SIZE=2]How much space do you have on your hard drive? You could run a Virtual Machine with the new VMWare Mac beta:[/SIZE][/COLOR]
[COLOR=#666666][SIZE=2] [/SIZE][/COLOR]
[COLOR=#666666][_[SIZE=2][COLOR=#800080]http://www.vmware.com/mac[/COLOR][/SIZE]_]("http://www.vmware.com/mac")[SIZE=2] [/SIZE][/COLOR]
[COLOR=#666666][SIZE=2] [/SIZE][/COLOR]
[COLOR=#666666][SIZE=2]With VMWare you can just point to the ISO Linear file for your Install CD Image and run it as a "CD-ROM'. Linux would then boot a "Virtual Machine" under a "Virtual Partition" ; the partition for linux would be kept in a single file on your Mac OS X Partition, and additionally you would allocate some of your RAM (256 MB probably) to your virtual machine. You can pre-allocate these partitions when you create the Virtual Machine, or leave them as small files that grow as you add files to your "virtual partition." The later method leads to fragmentation across two file-systems, so if you have plenty of space under your OS X partition you will want to pre-allocate a full 4 GBs of space to your VM Partition.[/SIZE][/COLOR]
[COLOR=#666666][SIZE=2] [/SIZE][/COLOR]
[COLOR=#666666][SIZE=2](BTW, VMWare has a bunch of pre-built &#8220;virtual appliances&#8221; so you might not even have to install your own kernel.  Or at the least you can play with several distributions without having to install each from scratch.)[/SIZE][/COLOR]
[COLOR=#666666][SIZE=2] [/SIZE][/COLOR]
[COLOR=#666666][SIZE=2]You could just as easily put a copy of the kernel image and the init ramdrive files to your OS X partition and then use "BootX" or another X Boot Loader to launch the Ubuntu Debian Kernel. This method would be a "native" kernel boot in that you wouldn't be running the kernel within an emulated sub-session; this means it will be faster than a "Virtual Machine", but you also have to be careful you don't format your Mac OS Partitions... *doh* You'll probably need to pass the root=/dev/hda## argument to the kernel, along with some possible "display parameters". I've used this method under OS 9.2 and it works well (though I've not done it under OS X, so don't expect me to know the specifics).[/SIZE][/COLOR]
[FONT=Times New Roman][SIZE=3][COLOR=#000000] [/COLOR][/SIZE][/FONT]

---

### Post by dpny on 2007-01-04
> **gurnemanz said:**
> Has anyone successfully booted a Pismo Powerbook from the cd or a disk image on an outboard drive? Or on an empty partition on the internal HD? It will be two or three more weeks before I can replace the internal CD/DVD drive in the Pismo, which may have shot craps . . .

Thanks, folks -

I have booted my Pismo from CD many times, but never from an external drive. I'm not sure what you mean by "on an empty partition on the internal HD". I know there is a way to just boot Linux from an internal drive without having done a full Linux install, but the partition needs to be formatted in HFS and not HFS+. This method is meant for people having trouble installing or who want to do a net install.

---

### Post by jaradronald on 2007-01-04
> **dpny said:**
> I have booted my Pismo from CD many times, but never from an external drive. I'm not sure what you mean by "on an empty partition on the internal HD". I know there is a way to just boot Linux from an internal drive without having done a full Linux install, but the partition needs to be formatted in HFS and not HFS+. This method is meant for people having trouble installing or who want to do a net install.
 
I think the method your referring to would involve resizing your hfsplus partition, and creating an ext3 partition & a swap partition with the space that is reclaimed during the primary partition resizing.  Ubuntu 6.10 would probably create a /boot partition (type ext2).  My OS 9.2 Partitions are as follows:

hda1 - 8  (Mac OS 9 Boot Loader Partitions)
hda9 - hfsplus partition [2 GB] (/media/MACOS9)
hda10 - ext2 partition [32 MB] (/boot)
hda11 - ext3 partition [7 GB] (/ {aka "root"})
hda12 - swap partition [256 MB] (/swap)
 
I think his real issue was he doesn't have a cd-rom on the mac, and wants to install the kernel by copying the files to his computer (either dumping from a CD-ROM ISO Image or loading the kernel off of the hfs partition and then mounting a network share at say /install that would link to the software repository on the cd-rom on another machine)...

---

### Post by dpny on 2007-01-04
> **jaradronald said:**
> I think his real issue was he doesn't have a cd-rom on the mac, and wants to install the kernel by copying the files to his computer (either dumping from a CD-ROM ISO Image or loading the kernel off of the hfs partition and then mounting a network share at say /install that would link to the software repository on the cd-rom on another machine)...

Actually, [this page](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html) is what I was thinking of. You copy vmlinux, initrd.gz, yaboot, yaboot.conf onto an HFS partition and boot from open firmware. Don't know if it will help, but it might be worth a shot. It's a pure network install. The only issue is that the partition needs to be HFS, not HFS+.

---

### Post by gurnemanz on 2007-01-06
I should explain better.

Yes, the worst problem is my internal CD-R/DVD is spastic at best. So good I should spin when I so old am. We will not compare colons.

I'm trying to follow Robert Strohmeyer's instructions in his article in the Jan. 2007 MacAddict. He partitioned his older Mac's hd for dual boot, OS X and Ubuntu. My Mac is much older, a Pismo with an 80 gig hd, which I have split into three HFS+ journaled partitions, with free space for the Ubuntu/Xubuntu installation and free space for a Swap.

I have, perhaps, been greedy. I set up and installed the 80 gig drive for OS X and for OS 9.2, with one HFS+ partition left to spare. I want to have a triple-boot system.

I created an Xubuntu Alternate cd this morning. Over the weekend I'll see if I can get it to install. 

My goal is to make this machine a kind of Swiss Army knife; my employer won't give me the graphic tools I need to create good documentation on their damned vanilla pc systems, so I want to use my Pismo with my Mac doc and design tools, then export as pdfs and so forth. Less energy spent on bad tools and useless requests, more time spent productively, and a chance to see what graphics design apps are available under Xubuntu.

Thank you both for your thoughts and consideration. Your skills and understanding are at this point beyond me, but I'll learn.

---

### Post by dpny on 2007-01-06
> **gurnemanz said:**
> I should explain better.

Yes, the worst problem is my internal CD-R/DVD is spastic at best. So good I should spin when I so old am. We will not compare colons.

I'm trying to follow Robert Strohmeyer's instructions in his article in the Jan. 2007 MacAddict. He partitioned his older Mac's hd for dual boot, OS X and Ubuntu. My Mac is much older, a Pismo with an 80 gig hd, which I have split into three HFS+ journaled partitions, with free space for the Ubuntu/Xubuntu installation and free space for a Swap.

I have, perhaps, been greedy. I set up and installed the 80 gig drive for OS X and for OS 9.2, with one HFS+ partition left to spare. I want to have a triple-boot system.

I created an Xubuntu Alternate cd this morning. Over the weekend I'll see if I can get it to install. 

My goal is to make this machine a kind of Swiss Army knife; my employer won't give me the graphic tools I need to create good documentation on their damned vanilla pc systems, so I want to use my Pismo with my Mac doc and design tools, then export as pdfs and so forth. Less energy spent on bad tools and useless requests, more time spent productively, and a chance to see what graphics design apps are available under Xubuntu.

Thank you both for your thoughts and consideration. Your skills and understanding are at this point beyond me, but I'll learn.

If you can get the CD to work, it should work. FWIW, I installed 6.06 off the normal install on my Pismo. You will have to tweak some settings to get Ubuntu to make good use of the machine's built-in video (it involves editing /etc/modules and /etc/X11/xorg.conf), but that's not a big deal in Linux land. The installer will also need to reformat one of the HFS+ partitions you've made, because Linux can't use HFS+. The installer will nuke the partition and make it's own bootstrap, swap and root partitions.

---

### Post by handylinux on 2007-01-06
> You will have to tweak some settings to get Ubuntu to make good use of the machine's built-in video (it involves editing /etc/modules and /etc/X11/xorg.conf), but that's not a big deal in Linux land.
I plan to put Ubuntu on a Pismo when I get it running; what's the problem with the video? Ubuntu doesn't support the ATI Rage 128 card? The Pismo display's native resolution is 1024x768, same as the two iBooks I've tried Ubuntu on, which didn't seem to need any tweaking.

---

### Post by handylinux on 2007-01-06
> **gurnemanz said:**
> I set up and installed the 80 gig drive for OS X and for OS 9.2, with one HFS+ partition left to spare. I want to have a triple-boot system.
I plan probably to do the same with my Pismo when I get it running. For ease in switching Systems, you might want to put Ubuntu on the first partition, which will allow you to boot into it by simply pressing the D key during startup. For details of how this works, see [How to switch OS on dual-boot Mac]("http://www.ubuntuforums.org/showthread.php?t=318682") and [OSX and ubuntu dual boot on an 80GB HD mac mini 1.42]("http://www.ubuntuforums.org/showthread.php?p=1951103").

---

### Post by dpny on 2007-01-06
> **handylinux said:**
> I plan to put Ubuntu on a Pismo when I get it running; what's the problem with the video? Ubuntu doesn't support the ATI Rage 128 card? The Pismo display's native resolution is 1024x768, same as the two iBooks I've tried Ubuntu on, which didn't seem to need any tweaking.

It's nothing serious. Ubuntu will support it out of the box. The issue is that Ubuntu doesn't make the most efficient use of it out of the box, so if you want screen redraw to be as fast as possible you need to tweak things a little. It's not a critical issue, but more of an efficiency issue.

---

### Post by gurnemanz on 2007-01-06
> **dpny said:**
> The installer will also need to reformat one of the HFS+ partitions you've made, because Linux can't use HFS+. The installer will nuke the partition and make it's own bootstrap, swap and root partitions.

Thank you for your information. We'll get this working yet, somehow.

According to Strohmeyer/MacAddict, the free spaces were to be left to the installer for that purpose. Was the article incorrect?

Now I'm off to find a 1-gig compact flash card, to see if I can make Ye Pismo boot from the installer on a CF card, the way I could run Mac OS and boot from an adapter in the pc card slot in the OS 7 - OS 9 days. I'll let you know what I find.

Again, thank you all for your ideas and knowledge. Please keep 'em coming.

---

### Post by handylinux on 2007-01-06
> **dpny said:**
> It's nothing serious. Ubuntu will support it out of the box. The issue is that Ubuntu doesn't make the most efficient use of it out of the box, so if you want screen redraw to be as fast as possible you need to tweak things a little. It's not a critical issue, but more of an efficiency issue.
Are there instructions for this somewhere that I can bookmark?

---

### Post by dpny on 2007-01-06
> **handylinux said:**
> Are there instructions for this somewhere that I can bookmark?

I can tell you what to do. The problem is two-fold. One, the proper AGP modules aren't loaded in /etc/modules. Second, the stock xorg.conf tries to take more video memory than the Rage 128 can give, resulting in a lack of direct rendering. In other words, rendering has to be done in software, which is much slower. So, the first thing to do is edit /etc/modules. Open it in your favorite text editor. I use pico, because I'm familiar with it from OS X. Open a terminal/shell and type:

```
suco pico /etc/modules
```

You want to add the following lines:

```
r128
agpgart
uninorth_agp
```

Under the line:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
```

If some of them are there, add the ones which aren't. If they're all there no changes are necessary. Press control-X and "y" or "n" to save or not.

Then you need to edit your xorg.conf file. 

```
sudo pico /etc/X11/xorg.conf
```

There are three sections to edit here. One is "Module". It should look something like this:

```
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "r128"
        Load    "dbe"

```

You don't need all those, but you want to make sure to add "r128", "dbe" and "dri". If all of them are there, no changes are necessary.

The second section is "Device". It should look something like this:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
        Driver          "r128"
        BusID           "PCI:0:16:0"
        VideoRam        8192
        Option          "AGPMode"       "2"
        Option          "AGPFastWrite"  "true"
        Option          "UseFBDev"      "true"
        Option          "EnablePageFlip""true"
        Option          "DMAForXv"      "true"

```

You don't have to have all those. The important ones are "Driver    r128",  and the option for "AGPMode" set to "2". And those are tabs between the words, not spaces.

The third section is "Screen". There is only one thing to change here, and that is the default bit depth. It should be 16, not 24, something like this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
        Monitor         "Pismo LCD"
        DefaultDepth    16
        SubSection "Display"

```

Control-X, "y" to save.

What all this does is 1) make sure the kernel modules for the video driver and AGP system are loaded, 2) tell X11 to use the open source r128 driver instead of the stock ati driver, and 3) tell the machine to only run 16 bits per pixel, which makes better use of the machine's limited video RAM. Restart X, or reboot, open a terminal window and type

```
glxinfo | grep direct
```

You should see:

```
direct rendering: Yes
```

---

### Post by handylinux on 2007-01-07
Thanks, I'll save this for when I get my Pismo going. Where did you learn about this? Is it in Ubuntu documentation somewhere? If "the proper AGP modules aren't loaded in /etc/modules", then where are they? Does this set of commands download them from somewhere?

"you want to make sure to add 'r128', 'dbe' and 'dri'." Do they have to be in the order shown, i.e. dri in #4 position, r128 & dbe at the end of the list?

Is any of this (or something similar) necessary to get best performance out of an iBook G3, with ATI Mobility Radeon 7500 (AGP 2x) card and 32MB VRAM, or an iBook G4, with ATI Mobility Radeon 9200 (AGP 4x) card and 32MB VRAM (the two Macs I've so far tried with Ubuntu)? How about the "Lombard" PowerBook G3, with ATI Rage LT Pro card? Is there an open-source driver for that? Where are such things found?

---

### Post by dpny on 2007-01-07
> **handylinux said:**
> Thanks, I'll save this for when I get my Pismo going. Where did you learn about this? Is it in Ubuntu documentation somewhere?

I learned about it by googling around. Some of the info was from threads here, and some from other places. It took a little while to get it all together.

> If "the proper AGP modules aren't loaded in /etc/modules", then where are they? Does this set of commands download them from somewhere?

The modules are in the standard install, they're just not loaded by default. All adding those lines to /etc/modules does is tells the machine to load them on startup. It's one of the things about Linux: you pay for more tweakability by having to dig a little deeper.

> "you want to make sure to add 'r128', 'dbe' and 'dri'." Do they have to be in the order shown, i.e. dri in #4 position, r128 & dbe at the end of the list?

As far as I know they don't have to be in any specific order.

> Is any of this (or something similar) necessary to get best performance out of an iBook G3, with ATI Mobility Radeon 7500 (AGP 2x) card and 32MB VRAM, or an iBook G4, with ATI Mobility Radeon 9200 (AGP 4x) card and 32MB VRAM (the two Macs I've so far tried with Ubuntu)?

As I've never worked with Linux on those machines I don't know. The issue with the Pismo's video card is that it is relatively old, so support isn't as good. The way to see if direct, i.e., hardware, rendering is running on any machine is to type

```
glxinfo | grep direct
```

in a shell/terminal window. If it returns "Direct rendering: Yes" then you don't have to worry. However, one of the thing about the X windowing system, the system which drives the GUI in Linux, is that it's very, very tuneable, so even with well-supported machines you can muck around with it.

> How about the "Lombard" PowerBook G3, with ATI Rage LT Pro card? Is there an open-source driver for that? Where are such things found?

That I can't tell you, because I have never put Linux on that machine. Your best bet is to Google around some.

---

### Post by handylinux on 2007-01-07
Thanks for the info; lots to learn, I guess.

---

### Post by salguod on 2007-01-11
Hi all,
I have a Beige G3 macintosh (not the tower) and have successfully installed Kubuntu 6.06 on it using the BootX method.

But, as curiosity killed the cat, I tried switching to Ubuntu from Kubuntu but ended up screwing it up. I can't even boot into terminal mode now! I don't really know what I did.

This is the message i get (after entering my username and password): 
"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to log in. Please contact your system administrator."

So, I would like to install Ubuntu 6.10 (which has the live CD and install on one disk) on it.

I copied the Initrd and vmlinux files to the system folder and linux kernels folder on the mac os side (as is did for the 6.06 installation) but I would like to know what  the boot parameters are to tell BootX to boot from the Live CD.

I saw the instructions on how to boot from the 5.10 live CD, but that parameter did not work.

salguod

---

