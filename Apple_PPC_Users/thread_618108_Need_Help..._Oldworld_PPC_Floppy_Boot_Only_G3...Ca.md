---
title: "Need Help... Oldworld PPC Floppy Boot Only G3...Cannot Install..."
date: 2007-11-20
forum: Apple PPC Users
---

### Post by foxholeunder on 2007-11-20
Usually I do not end up needing to ask for very much help... However, recently I have run into a snag that I cannot seem to find a solution. I have an Oldworld PowerPC. A Power Macintosh 7300/180--Beige to be exact. This system as great as it is--it does not however boot from cdrom... floppy only... 

My question is: How do I obtain floppy images that will allow Ubuntu to start installation from floppy and then proceed using the cdrom to complete installation? And most importantly, how do I create them using Ubuntu? I have found similar posts using Windows to create floppies, but I have long since saved myself from the tiresome world of Windows.... 

I have tried the Debian PPC floppy images, but the system ejects them immediately, a fact that most likely indicates that these discs are not properly formated to be read by the 7300/180 box. I do not even know if these discs were to work...if they would even allow me install Ubuntu, or only allow a pure Debian install. Preferably I would like to stick with Ubuntu being as I already have 7 other machines running Ubuntu and already am fluent in the Ubuntu specific intricacies... but hey... If I cannot then no big deal. 

The system already has a painfully slow stripped OS/8 with very little in the way of packages and would like to completely dump this install altogether and go for a straight Ubuntu install. (At least some flavor of Linux if nothing else.) I do not even care if there is drivers for the 128 MB Rage 3D video card... This box is going to find home in my kitchen and loaded with recipes with Web access to search for other recipes and perhaps stream music from my music server while I cook...Nothing more...

I have an old 75 Mhz CPU - 128 MB ram Sun Workstation 5 that runs OpenBox running atop 6.06 Server extremely well. So I feel confident that once I figure out the floppy boot only problem presented with the PowerPC 7300/180, I should have a nice little Recipe server in my kitchen... The Sun box is in my shop aiding shop related tasks otherwise I would move it into the kitchen.

Any help would be appreciated on if there are available floppies to start the Ubuntu install (for ppc), and/or how to create them. I have browsed many posts here and cannot seem to find the answer I require.

Again, this is the Beige 7300/180

Thanks for your help in advance!

---

### Post by oswaldkelso on 2007-11-20
I take it you know you need a boot loader like bootx or miboot? there is a tutorial on the debian forums that may give you some ideas. i.e make a small os 8 partition and stick the linux bootlader in the control panel/extention 

[http://forums.debian.net/viewtopic.php?t=19915]("http://forums.debian.net/viewtopic.php?t=19915")

The above does have a cd rom but will give you some ideas.

There was an alternative  called quik that didn't need a boot loader but it seems it was a bit flakie so most people go down the bootx / miboot road.

You may find some info on reading you floppys here

[http://www.euronet.nl/users/mvdk/Most_important_links.html]("http://www.euronet.nl/users/mvdk/Most_important_links.html")

I think I have some links someware on bootx I'll try and find them and post later

EDIT

[http://penguinppc.org/bootloaders/bootx/]("http://penguinppc.org/bootloaders/bootx/")

google "bootx floppy" there are lot of snipets

---

### Post by foxholeunder on 2007-11-20
I was trying the Yaboot loader that came with the Official Debian PPC floppies. They did not appear to work. I may have not transfered them to floppy correctly though.

Thanks for the tips!

I am going to try them out and let ya know how it goes!

---

### Post by foxholeunder on 2007-11-21
Been playing around here trying to get this to go correctly and am still having issues.

I found this site: [http://www.gifford.co.uk/~coredump/beigeg3.htm]("http://www.gifford.co.uk/~coredump/beigeg3.htm")

I have found BootX successful in finding and starting the CD, yet no matter what version of Ubuntu ppc edition I try ... and I have them all now ... Every time I click the Linux button to begin the installation, I hear/see the CD drive spin-up and the screen goes into a frantic static waver and never recovers until I hard reboot the computer. 

If I add any other arguments to the boot parameters the screen just goes black until I finally give in and hard reboot the system.

The whole deal is proving to be harder than it probably is... Yet I am just stubborn enough to desire to continue on until I finally achieve an Ubuntu installed Oldworld G3. It took me five months to get a GUI running on my old Sun Workstation 5, and as slow as it may be it is the most beautiful thing in my eyes. Point being ... I will not give up until this G3 7300/180 has Ubuntu up and running!!!

Does anyone have any possible solutions as to the screen issues I am getting that are preventing me from seeing the install screens as the above tutorial suggests I should be seeing?

I think... I still have an adapter or two converting Apple's video port to standard vga ... I still as of yet need to locate them. Perhaps there is an issue with screen size or similar video error causing the fuzzy or blank screen. The monitor is nameless Apple 17inch CRT, the ID tags on the back are faded. If I can locate them I will be trying this solution and hopefully this will solve my new problem. Who knows if there will be more issues that arise before everything is complete. 

I have in the meantime successfully upgraded from OS/8 to OS/9.1 using BootX so I know the program and cdrom drive are working correctly in this aspect... I just seem to not have a supported Apple monitor for installing Ubuntu. The above link suggests an additional problem that I may encounter once I can get Ubuntu installed... We shall see... I will keep updating this post as I figure things out.

---

### Post by ppc_guy on 2007-11-22
Well hopefully I can help shed some light here. 

1.) The 7300 is not actually a G3 machine. They are PPC604e chips, considered a PCI-Mac. 
    - So trying to run an iso that that supports a G3 will not work. It will have to be something older. Think NetBSD or MKlinux though that project has been dead for a very long time. But I feel you pain. I have a 7200 here that was pretty much useless before NetBSD. 

2.) You are on the right track with BootX and the issues are getting are not your fault. Just the wrong kernel for the machine. 

 Now on to the links. For one: [www.lowendmac.com](www.lowendmac.com) If you click on mac profiles you can learn some very useful things about that machine. Don't worry you have a good find. The 73/7600's where some over the best machines Apple ever made.
 Second link: [http://penguinppc.org/](http://penguinppc.org/) to lean all things old school mac and linux related. Granted this page is a bit old and not all that maintained anymore, but it's a great reference and a good start. 

 Hope that helps.. Feel free to post back and I will answer if I can..


Nathan
-------------------------------------------------------------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango_Hotel
-------------------------------------------------------------------------------------------------------------------------

---

### Post by pxwpxw on 2007-11-22
My standard configuration oldworld 7300/180 powerpc 604e cpu, beige desktop, scsi drives. (version before oldworld G3 beige desktop of same appearance). Not sure how the following relates to the G3 oldworld, it depends on the open firmware version also.

Is running ubuntu 610 (command line) for which initial restart requires an additional manual fixup <modprobe mesh> to update-initramfs.

Has had text mode (alternate) install CD's booted by bootx 1.2b3 from ubuntu410 to 610, (also 704, but that had scsi problems ), also debian woody, sarge.

They required various amounts of fiddling with video settings to get the text mode install screen usable, or even visible.

My notes say this included:

In macos, select 256 colour 640x480 resolution, because with bootx this carries over into linux installer.

In bootx 1.2b3
 []novideo driver - leave unchecked.
 In [Other options], I have 
 [x] Force video settings checked, but not sure what this was during  install.
 
I am not too sure now if that is all correct, but they were the relevant parameters to get video for the install.

There were no bootx kernel parameters added for video, only append lines copied from the yaboot.conf <append= .... > if you want cli.seed or other options. (read these in yaboot.conf on the cd) Do not try to use Desktop CD.

Other install screen startup failures have been caused by an extra video card in use, when the installer uses the original apple video.

---

### Post by foxholeunder on 2007-11-23
Hey thanks everyone!

I was figuring the machine was a G3c as I guess I got confused when reading the Wikipedia article that talks about a G3 in the same section as my particular machine... They even have a picture of what my box looks like. I apologize for the mistake!

Article Here:

[http://en.wikipedia.org/wiki/Power_Macintosh_7300]("http://en.wikipedia.org/wiki/Power_Macintosh_7300")

**pxwpxw**: I will try your suggestions for Video modes... if not then I will be using your suggestion **ppc_guy ** and give NetBSD a whirl.

I am hoping Ubuntu can install on this box... what can I say I love Ubuntu and I love the default color scheme!

NetBSD eh? That is one Unix I have not tried yet. I do have a FreeBSD machine I run as my local DHCP server (for years now) so I am familiar with the differences between LInux and Unix.. albeit minute differences in many instances.

I know it is not the wrong video port as I have only one available card in this thing so I will try the suggested screen resolutions and look into the yaboot conf..

Here's another question regarding the PCI slots. Are these standard PCI slots or do I need special Mac PCI cards? I am curious as I have several older 5.1 surround sound cards that I know for sure work under ALSA. Assuming I can get this thing up and running I would love to add one of these cards. Probably overkill for a system that will reside in the kitchen and serve recipes, but hey, would be nice to wire up several speakers and maybe stream my TV or a video into the thing while in the kitchen. I just do not want to blow the card up if the power to these slots are different. I know they fit into the slots but I have never turned the thing on while they were in.

I will give these a shot tomorrow... Turkey dinner at my dads then turkey dinner at my moms -- I am over-turkied and tired out tonight! I will post to let everyone know my results!

EDIT !!!
I just re-read the Wiki page and the code name was 'Montana' -- I had to laugh I do not know how I missed that before as I live here in Montana!

---

### Post by oswaldkelso on 2007-11-23
A few more links for you :)

[http://www.netbsd.org/ports/macppc/models.html]("http://www.netbsd.org/ports/macppc/models.html")

[http://www.debian.org/ports/powerpc/inst/pmac]("http://www.debian.org/ports/powerpc/inst/pmac")

[http://www.debian.org/ports/powerpc/inst/install]("http://www.debian.org/ports/powerpc/inst/install")

[http://www.debian.org/ports/powerpc/]("http://www.debian.org/ports/powerpc/")

[http://www.debian.org/releases/stable/powerpc/ch05s01.html.en]("http://www.debian.org/releases/stable/powerpc/ch05s01.html.en")
[URL="http://www.debian.org/releases/stable/powerpc/ch05s01.html.en#id2536590"]
http://www.debian.org/releases/stable/powerpc/ch05s01.html.en#id2536590[/URL]

[http://wiki.debian.org/DebianInstaller/PowerPC/OldWorld/PreAlphaManualUpdates]("http://wiki.debian.org/DebianInstaller/PowerPC/OldWorld/PreAlphaManualUpdates")

[http://mfdh.ca/apple/debian_on_oldworld_mac.html]("http://mfdh.ca/apple/debian_on_oldworld_mac.html")
[URL="http://www.ppcnux.de/?q=node/7024"]
http://www.ppcnux.de/?q=node/7024[/URL]

If you go down the debian route Then an older Kernel sarge? is likely to give you better results The only other distro that may work well easily is yellow dog, try yd 2 or 3. 
[URL="http://www.yellowdog-board.com/viewtopic.php?p=1269"]
http://www.yellowdog-board.com/viewtopic.php?p=1269[/URL]

[http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg52909.html]("http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg52909.html")

---

### Post by foxholeunder on 2007-11-23
**oswaldkelso**, Thank you for all the links! Wow! lots of good reading material while I attempt this project today! Very Very Appreciated! 

I was just this morning looking at Yellow Dog as an option! Now that you specifically mention it I think I will obtain a Yellow Dog CD and give it a go as well. 

While that is downloading I am going to attempt screen resolution settings and see if Ubuntu will not actually work. If so then I will be writing a thorough tutorial on the matter and share it here. 

I found my Mac-vid to VGA video adapter (three in fact), and will be giving that a go today if nothing else works..

Stay tuned for the results of this projects!

Again, Thank You ALL that have contributed suggestions!!!

---

### Post by foxholeunder on 2007-11-26
WoooooooHooooooo!

O.K. Finally, everything falls together and Ubuntu 6.06 Server ppc installs. I had to finally use a Mac video to Standard VGA converter to force a specific screen resolution. But hey, it worked. In fact standard Ubuntu 6.06 worked, but there was a lot of drag when after Gnome booted so I reverted down to straight server and grabbed everything needed to compile my own packages.

I started by trying something different, rather than picking a preconfigured desktop gui that comes with various packages, I opted to be safe and prevent myself headaches and compile all packages I would like from scratch. 

A long story short, I got Openbox running giving me a window manager, I proceeded with grabbing firefox, I grabbed msql along with various support packages for xml. Once these items were finally obtained and compiled I grabbed Anymeal [http://www.wedesoft.demon.co.uk/anymeal-api/]("http://www.wedesoft.demon.co.uk/anymeal-api/")

I ran a few tests within my main box of various recipe packages and Anymeal appealed to me. I especially liked the fact that Anymeal works directly with mysql, Now if I should be over at my family or friends and require a recipe I can just log into my network and access my recipe collection remotely.

Now all I need is a few recipes to add to my database...... That and maybe some support for audio so I can stream some music while cooking.

Thank you all for your helpful suggestions!

Unless I get sidetracked by another project I will compile my notes and make some sort of how-to. 

Again though, Thank you all that gave me suggestions!

---

### Post by oswaldkelso on 2007-11-26
Waaaaay, Nice one, it alway feels good when you finally crack a project. I feel really pleased for you there is nothing quite as much fun as keeping old hardware going. Just be sure to write down how you did it! Just incase :)

---

### Post by foxholeunder on 2007-11-29
> **oswaldkelso said:**
> Waaaaay, Nice one, it alway feels good when you finally crack a project. I feel really pleased for you there is nothing quite as much fun as keeping old hardware going. Just be sure to write down how you did it! Just incase :)

I am hoping to turn my notes into some worthwhile tutorial and share with others. I will say now that this box has more response than I think it has ever had! I cannot recall a time when it was not sluggish trying to do things. Considering the overall specs for the machine though this is of course nothing to whine about, as it is just the nature of this box. -- But, seeing as Ubuntu 6.06 server and OpenBox window manager are getting down to the absolute minimum of what is required to have some GUI functionality... This machine now (for all intense purposes), has the illusion of being a screaming fast modern computer. -- Technically, in reality, it is now extremely fast and responsive in regard to the tasks I am requesting this box to perform. 

Old hardware perhaps, but now capable of having a new life and once again putting a smile on the face of its user. Man and Machine have once again been reunited helping each other conquer the struggle of life in the digital age.

Thank you again for everyones help!

---

