---
title: "Cannot burn iso"
date: 2005-01-15
forum: Apple PPC Users
---

### Post by perroboy on 2005-01-15
I downloaded the ppc iso from mirrors in Switzerland and Germany and cannot burn either one in OS X 3.7 using Disk Utility and a variety of burning programs. In fact, Disk Utility just crashes. (And yes I'm doing it the same I always have and described in the How-to pages.)

Any ideas  :confused:

---

### Post by DJ_Max on 2005-01-15
Open up "Console" and look for any relevant error messages. Also, when you said you used other CD Burning applications, what happens? You have to burn as a "Disc Image" on a blank CD-R or CD-RW.

---

### Post by perroboy on 2005-01-15
Keep forgetting about the Console...good tip, and here's what it gives:

*** malloc[15671]: error for object 0x18f6600: Incorrect checksum for freed object - object was probably modified after being freed; break at szone_error
*** malloc_zone_malloc[15671]: argument too large: 3328212968
*** malloc[15679]: error for object 0x1803e00: Incorrect checksum for freed object - object was probably modified after being freed; break at szone_error
disk1 device will be unmounted ...
***Notifications Complete for type 1
***Disk Unmounted('disk1')

don't know what it means exactly, though

in Toast the durn starts, but then errs before the disc has been touched. No crash, but no burn either

any clues?

---

### Post by DJ_Max on 2005-01-15
Does it crash after you load the image?? It might be a bad ISO image. Have you checked the md5 checksum of the ISO you downloaded??

Open "Terminal", go to the directory it's downloaded to, and i beleive you run *openssl md5 FILENAME* 

Compare that to the md5checksum file on the mirror you downloaded it from.

There's also another program for burning [http://www.apple.com/downloads/macosx/system_disk_utilities/imageburner.html](http://www.apple.com/downloads/macosx/system_disk_utilities/imageburner.html)

---

### Post by chascon on 2005-01-15
NO NO NO NO
ubuntu-ppc does not burn with OS X's disk utility.  And for ethical reasons keep away from Toast (especially with great software such as XCDRoast that does more than the free Toast you got with your burner.  In fact XCDRoast does everything "Toast Pro (what ever its called)" does, as far as I can tell and is not propietary.

Of coarse test the md5 of the iso in OS X after every download.  You can drag and drop the iso to get the pathway for it in the md5 term command.

Please read (this is how I burned ubuntu-ppc from OS X ... because disk utility would crap out trying to burn the ubuntu-ppc iso.  Guess what, the iso's md5 checked out despite disk utility crapping out.):
[http://www.ubuntulinux.org/wiki/BurningIsoHowto/view?searchterm=ppc](http://www.ubuntulinux.org/wiki/BurningIsoHowto/view?searchterm=ppc)
"Burning/writing an .iso Image to CD with Mac OS X

To burn most isos, you can use Apple's Disk Utility (Disk Copy in older versions). However, there are some CDs? that will not burn with Disk Utility (warty ppc, for example). For these, you need another piece of burning software, listed below ...
Using Firestarter FX (avaliable at [http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter](http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter) ):

    *

      Open Firestarter.
    *

      If you can burn anything with Apple's tools (Disk Utility, Disk Copy, Finder), then you can leave the defaults at the setup screen. If not, you might have to play with your driver settings, try the defaults first though.
    *

      Choose the "Burn Image" tab.
    *

      Click "Open" for the image file box and choose your iso.
    *

      Click "Burn."

PS- The checksum command (in OS X) is "md5 pathway/to/iso".
-OS X's disk utility's checksum might work to verify md5 even if it doesn't want to burn the CD.

---

### Post by perroboy on 2005-01-16
First off, the checksum checked out fine. That's why I was so puzzled by what I found in Console.

Second, I DID read "Burning/writing an .iso Image to CD with Mac OS X" ([http://www.ubuntulinux.org/wiki/Bur...?searchterm=ppc](http://www.ubuntulinux.org/wiki/Bur...?searchterm=ppc)) It said use Disk Utility so that's what I tried. 

Normally I DO use FireStarter, but the current beta just expired (even a few days before the announced Jan 15 cut-off date ?) so no go there.

I even tried the Image Burn utility suggested by DJMAX, but that didn't work either. 

**What did finally work is booting into an external drive with 10.2.8 installed and using DiskCopy.**

Is this a bug in 10.3?

---

### Post by DJ_Max on 2005-01-16
I doubt it's a bug on 10.3 as it would have been well known. It's something wrong with your system, and just needs to be fix. Go over to forums.macosxhints.com I'm sure they can help you.

---

### Post by perroboy on 2005-01-16
you could be right, but it would mean that my standard installation of 10.3.7 is broken on two different machines...highly unlikely

Then again, I realize this is not the place to discuss this

---

### Post by grover on 2005-01-16
I experienced the exact same thing yesterday (tried to burn a hoary powerpc live CD iso in OSX 10.3.7 -- disk utility crashed every time).

A quick google search confirmed that others were having the same problem, so this is not a problem with your OSX installation.  It is a bug (or feature limitation) in OSX.

I burned my iso by using fink ([http://fink.sourceforge.net/](http://fink.sourceforge.net/)) to install cdrecord.  I had trouble figuring out what device to use with cdrecord under OSX on my iMac G5.  For the benefit of anyone else who wants to do this, this is the command I used:

sudo cdrecord dev=IODVDServices hoary-live-powerpc.iso

---

### Post by chascon on 2005-01-17
he perroboy, 
It's obious you did not read the burn iso how to becuse it details that mac OS X diskk utility is good enough for MOST  isos but NOT all.

"Burning/writing an .iso Image to CD with Mac OS X
To burn most isos, you can use Apple's Disk Utility (Disk Copy in older versions). However, there are some CDs? that will not burn with Disk Utility (warty ppc, for example). For these, you need another piece of burning software, listed below."

Date cuenta que dice que no todos los iso son compatibles con disk utility perroboy. 

About it being a bug, I also had the same problem on my Panther install, what ever version it was at, I hardly use it or care to use.  So given that the HowTo warns about incompatibility and that my system doesn't work, I doubt it is really particular problem with perroboy's particular system or mine for that matter.  I believe I've also had problems with other and only linux isos.

I suspected that Jaguar disk copy might work, but never tried it.  I provided info on how I did it, according to the HowTo.

I'm sure you can get another beta firestarter.  Try throwing out the firestarter preference file if something is keeping track of how long you've had it. That still sometimes works.
But this is hindsight now.

The propper iso burn HotTo is at
[http://www.ubuntulinux.org/wiki/BurningIsoHowto](http://www.ubuntulinux.org/wiki/BurningIsoHowto)

---

### Post by perroboy on 2005-01-17
Jeez Louise!

I for one missed that little detail, Chascon. Hands up, who thinks the how-to-burn needs re-writing? 

Thanks for your constructivism, though. =D>

---

### Post by chascon on 2005-01-23
Yeah how do we go about getting people change these wikis.  Some are terribly arch specific, and need some ppc info contributed.  Have you noticed that the restricted formats one mentions some repository but if you go there you will NOT find ppc debs.

---

### Post by DJ_Max on 2005-01-23
[QUOTE=chascon]Yeah how do we go about getting people change these wikis.  Some are terribly arch specific, and need some ppc info contributed.  Have you noticed that the restricted formats one mentions some repository but if you go there you will NOT find ppc debs.[/QUOTE]
 On a related note, I was thinking about setting  up a strictly PPC Wiki, I let everyone know when I do.

---

### Post by adamw on 2005-01-27
I think it's worth mentioning that the iso image crashed Disk Utility on a powerbook 1.5ghz running 10.3.7, a 2.0ghz G5 running 10.3.7 and 10.2.8, and a 1ghz G4 desktop running 10.4 beta (yes, my copy was legally obtained directly from Apple).  I filed a crash report to Apple each and every time.  Maybe they'll get the picture  :)   Anyways, I seem to recall burning successfully with Toast.  Too bad it's not free.

---

### Post by skipunk on 2005-01-27
I'd like to join the can't burn iso club too.  I am using 10.3.7 and last night I tried to burn the iso for the liveCD and the Disk Utility crashed everytime.  I tried the image burn utility as well, and when I drag the image file into ImageBurn, nothing happens.  The readme says it should start buring automatically, but it doesn't.

---

### Post by usr3301 on 2005-01-27
I hate to say it, but I used Toast to burn my Warty ISO.  I didn't have any problems.  I am running Jaguar.  Ubuntu Rocks!!!

---

### Post by skipunk on 2005-01-27
I used firestarter(I Just turned my clock back a year :) ) and burned the iso.  I am now typing this from the Ubuntu ppc LiveCD.  Ubuntu rocks!!

---

### Post by Huxley on 2005-01-28
Also try missing media burner
[http://www.versiontracker.com/dyn/moreinfo/macosx/16799](http://www.versiontracker.com/dyn/moreinfo/macosx/16799)
Select data.
Burn iso.
Drop the ubuntu ppc iso into the window.
Burn.

---

### Post by ewaldgroup on 2005-01-29
Missing Media Burner worked great for me. here is a link to the version tracker download page: [http://www.versiontracker.com/dyn/moreinfo/macosx/16799](http://www.versiontracker.com/dyn/moreinfo/macosx/16799)

Thanks,
ewaldgroup

---

### Post by jjramsey on 2005-02-03
[QUOTE=skipunk]I used firestarter(I Just turned my clock back a year :) ) and burned the iso.  I am now typing this from the Ubuntu ppc LiveCD.  Ubuntu rocks!![/QUOTE]

How did you find Firestarter? I went to the [link](http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter) pointed to by the [Burning ISO Howto](http://www.ubuntulinux.org/wiki/BurningIsoHowto), and there didn't seem to be a download link for Firestarter. It looked like Firestarter went offline.

---

### Post by Thomas Ferreira on 2005-02-10
I was having the same problem where Apple's Disk Utility would not work and yes, FireStarter worked for me.  Downloaded it from versiontracker.com.  Yes, this version of FireStarter is now past date so it does not launch unless you temporarily set the date of your system back before like 1/15/05.  I set it to 1/10/05 and it launched fine for me.  Easy to run application and burned my iso fine.  I still can't get my linux system to boot yet but that is another issue.

tj

---

### Post by PBdan on 2005-02-12
[QUOTE=jjramsey]How did you find Firestarter? I went to the [link](http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter) pointed to by the [Burning ISO Howto](http://www.ubuntulinux.org/wiki/BurningIsoHowto), and there didn't seem to be a download link for Firestarter. It looked like Firestarter went offline.[/QUOTE]

Hi!

[http://www.projectomega.org/click.php?dl=1&url=contents/en/downloads/internal_products/firestarter/FireStarter_FX-1.0b8.tar.bz2](http://www.projectomega.org/click.php?dl=1&url=contents/en/downloads/internal_products/firestarter/FireStarter_FX-1.0b8.tar.bz2)

PBdan
Excuse my english :-)

---

### Post by Leonida on 2005-02-19
[QUOTE=DJ_Max]On a related note, I was thinking about setting  up a strictly PPC Wiki, I let everyone know when I do.[/QUOTE]
I've summarized this topic editing [How to burn an ISO Image](http://ubuntuppc.webplazahosting.com/index.php?FrontPage) page at your Wiky.

Hoping to be useful.

.L.

---

### Post by forkart on 2005-03-04
[QUOTE=perroboy]I downloaded the ppc iso from mirrors in Switzerland and Germany and cannot burn either one in OS X 3.7 using Disk Utility and a variety of burning programs. In fact, Disk Utility just crashes. (And yes I'm doing it the same I always have and described in the How-to pages.)

Any ideas  :confused:[/QUOTE]

Download MagicISO, It is good [iso burner](http://www.magiciso.com/tutorials/miso-burnwin.htm). 
[http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)

---

### Post by Viro on 2005-03-04
[QUOTE=forkart]Download MagicISO, It is good [iso burner](http://www.magiciso.com/tutorials/miso-burnwin.htm). 
[http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)[/QUOTE]
 That is a Windows program. It doesn't run on PPC machines.

---

### Post by TearingHairOut on 2005-03-26
[QUOTE=perroboy]
Hands up, who thinks the how-to-burn needs re-writing? 
[/QUOTE]
Hands up, who thinks Disk Utility needs re-writing?
*Me raises hand*

---

### Post by eduardgrebe on 2005-04-11
[QUOTE=DJ_Max]I doubt it's a bug on 10.3 as it would have been well known. It's something wrong with your system, and just needs to be fix. Go over to forums.macosxhints.com I'm sure they can help you.[/QUOTE]
 I have the same problem, and I suspect it is a bug in disk utility.

---

### Post by ambiogas on 2008-02-16
All, I'm having a problem which is similar to those in this thread.  I am trying to burn an iso for my compaq pc, and there are identified problems with the oem cd/dvd burner.

So, I thought that I would burn the iso on my imac (os X leopard).  The md5 checksum matches.  When I used disk utility, the iso seemed to copy, but failed verification at the end.  I was trying to be conservative and burned at 8x.

I tried to boot on it anyway, and it worked partially.  The splashscreen came up, and I hit install.  The CD started spinning, and then went into hyperspace.

I work with linux at my workplace, and remember using cdrecord or mkisofs, I can't quite remember the details.  With all of the troubles with the burning utilities, would this be a more sure bet to burn the iso?  And if so, is anyone familiar with the syntax on an imac?  I am new to mac.  Thanks,

Andy

---

### Post by oswaldkelso on 2008-02-16
How I burn an iso in osx.

I had a lot of bad burns in osx. So this is what I do now it works for me so I've never changed.

1. download the disc image.
open disc utility.
drag the disc image into the left hand pane on disc utility.
select the image in the pane.
then select burn.
[B]
you must not open the disk image with the finder it can mess it up!![/B]

2. use burnfreex [http://www.macupdate.com/info.php/id/13824](http://www.macupdate.com/info.php/id/13824)

3. If you use toast in os 9,burn using the straight iso 9660 not pc, mac, etc

4. If you use windows I don't know!

---

### Post by stream303 on 2008-02-16
Those are great tips - especially about using iso9660 on other 3rd-party tools.

For windows, if all you want to do is burn an iso without all the bloat, I like the free isorecorder utility:

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

The illustrated howto is handy:

[http://isorecorder.alexfeinman.com/HowTo.htm](http://isorecorder.alexfeinman.com/HowTo.htm)

---

### Post by ambiogas on 2008-02-17
Thanks for the replies, oswaldkelso and stream303.  I had already been doing what you had posted, so your affirmations helped me to get past this.

I found some other posts that complained of the osx disk utility having trouble verifying the iso burn, and they suspected that the verify function was for some unknown reason having trouble with the 7.10 desktop 386 iso.

So, I did the verify disk from the ubuntu install splashscreen, and it said that there were no errors.  I gritted my teeth and did the install.  The install went fine, and now I have a dual boot machine.

It would be nice to know why the osx verify failed, but I guess that I can let this one go. (I have trouble with that sometimes).

Thanks again for your help, and thanks to the ubuntu developers for creating a wonderful os suite.

Andy

---

