---
title: "266 Mhz blue iMac install woes"
date: 2004-10-29
forum: Apple PPC Users
---

### Post by DaveyJJ on 2004-10-29
Linux newbie, computer user for 25+ years so somewhat tech savvy. Having problems with my Ubuntu install on an older 266Mhz blue iMac. Downloaded the ISO for PPC, made sure it wasn't corrupted (checksum etc), burned to disk (correctly) using Toast 6. I created both ISO9660 and Mac versions of the disk.

Wiped the 6GB hard drive of my old iMac and created a single partition which I formatted to be a UNIX partition (rather than HFS+). here's where the problems begin ...

The installer disk I created does not boot using the "c" key hold technique. Other bootable disks are fine (i.e., OSX disk boots fine when "c" is held). So I boot into open firmware (version 3.0r2?) and use the >boot cd:,\install\yaboot technique as described in the Read me.

Seems to start fine, as I can choose language, country, keyboard etc. It begins to load "mesh" and then errors out telling me the Ubuntu CD is not in the CD ROM. So, on a lark, I swapped out the ISO CD with the Mac CD at this point and then installation seems to proceed. Some of the packages begin to be read, PCMIA network card question is asked, and then it fails again. It gives me an error at this point saying the Ubuntu CD is not in the CD ROM again. 

Swapping back and forth between ISO/Mac-format disks doesn't help but it does allow me to get back to a Ubuntu screen where I can cancel the process and reboot (or try to read the CD again, skip portions of the install, etc.)

What's going on? Why isn't the CD readable? I'm going to attempt later tonight another install with another ISO CD crteated directly in Toast (which, mounts 2 separate disk images from the downloaded ISO, rather than the 1 virtual image when you just double click on the download in Finder).

Any other older iMac users ever get this to work, yet?

All help appreciated.

Maybe the disk should be formatted for HFS+????

PS. The CDROM and hard disk are fine as I was able to repartition it before I left for work this AM into two 3GB chunks, on 1 I've loaded OSX 10.2 without a problem.

---

### Post by jdong on 2004-10-29
**Moved to PPC Help**

---

### Post by cerulean coil on 2004-10-29
Perhaps this thread will help....

[Clicky.](http://www.ubuntuforums.org/showthread.php?t=2340) 

Hope this is of use.

---

### Post by DaveyJJ on 2004-10-30
OK, for all Mac users out there, here's something to consider. While at work yesterday (a PC environment), I took the downloaded ISO I had on my Mac laptop and transferred it across the network to one of the IT guys. I'd had a programmer at work suggest that maybe, just maybe, the burn-to-disk process itself on the Mac was somehow messing up the byte size or bootability or fiole sizes or naming structures of the files in the ISO.

Sure enough, I get the IT guy to burn to disk the PPC ISO **on a PC** and suddenly the disk works perfectly on my Mac. I tested the "c" key that forces the CD to boot first on my laptop and it works! Bring it home to the old iMac I have a it worked **perfectly**. 

The install did take 30 minutes or so, but I now have a all but useless (for OSX anyways) 266Mhz blue iMac with 196MB RAM running a superbly fast and apparently very stable Ubuntu Linux. Networking etc all works.

My suggestion to Mac users is to make sure they burn the ppc iso on a PC, or at least don't use Toast 6.

Thanks for all help.

David

---

### Post by thevine on 2004-10-30
If using toast 6 you need to  burn as copy (not data) and check the image file radio button, bootable iso every time.

---

### Post by cerulean coil on 2004-10-30
[QUOTE=DaveyJJ]

My suggestion to Mac users is to make sure they burn the ppc iso on a PC, or at least don't use Toast 6.

Thanks for all help.

David[/QUOTE]

Interesting. I'll give that a try. I'm not using Toast 6, I'm using the Disk Copy utility that comes with OS X.

Cheers.  8)

---

### Post by TekMate on 2004-10-30
I had to use a PC as well it just wouldn't work doing it on the Mac and I tried two different ones. :-k

---

### Post by DaveyJJ on 2004-10-30
[QUOTE=thevine]If using toast 6 you need to  burn as copy (not data) and check the image file radio button, bootable iso every time.[/QUOTE]

Did that. I went through 10 CDs in varying Toast configurations and nothing I could do made it work for me. I figured it was something else, and as a pretty tech savvy Mac user (since 1986) I've got a good grasp of Toast (6 is my 4th version of the program) so while I have my moments of stupidity, I'm relieved to: a) know it wasn't me and my Toast settings, and b) have a cool Linux box.

---

### Post by supernaut on 2004-10-31
Hmm... I burned on GNU/Linux PC box too actually... hdiutil burn kept either segfaulting, saying the ISO was unverifiable, or just giving some protection error.

---

### Post by cerulean coil on 2004-11-03
[QUOTE=cerulean coil]Interesting. I'll give that a try. I'm not using Toast 6, I'm using the Disk Copy utility that comes with OS X.

Cheers.  8)[/QUOTE]

Okay, my friend downloaded and burnt to CD-RW the ppc iso using Nero on his PC.

It still doesn't work properly. It installs, and then gets [errors galore.](http://ubuntuforums.org/showthread.php?t=2977) 

I'm going to try installing Ubuntu with the iMac actually connected to the 'net later tonight, and if that doesn't work, I'm putting Mac OS X on it and its going back on eBay. [-o<

---

### Post by Huxley on 2004-11-04
I used MissingMediaBurner to burn the iso to a 700mb CD-R.
This worked.  

[http://www.versiontracker.com/dyn/moreinfo/macosx/16799](http://www.versiontracker.com/dyn/moreinfo/macosx/16799)

My powerbook g3 400 bronze installed without problems using >boot cd:,\install\yaboot.

---

### Post by cerulean coil on 2004-11-07
[QUOTE=Huxley]I used MissingMediaBurner to burn the iso to a 700mb CD-R.
This worked.  

[http://www.versiontracker.com/dyn/moreinfo/macosx/16799](http://www.versiontracker.com/dyn/moreinfo/macosx/16799)

My powerbook g3 400 bronze installed without problems using >boot cd:,\install\yaboot.[/QUOTE]

Cheers mate. :D

I never actually got around to trying the install again, but I'll try MissingMediaBurner when I return home.

Fingers crossed!

---

### Post by cerulean coil on 2004-11-08
Okay, how do you get MissingMediaBurner to work? Basically, which driver do I chose?

Thanks.

---

### Post by Huxley on 2004-11-08
From [http://www.xlr8yourmac.com/archives/apr03/040903.html](http://www.xlr8yourmac.com/archives/apr03/040903.html)
"It (MissingMediaBurner) has a cocoa GUI that controls the command line app called CDRDAO"

So I went to [http://cdrdao.sourceforge.net/drives.html](http://cdrdao.sourceforge.net/drives.html)
I have a Pioneer 107D on my G4 867.
Seeing most of the Pioneer 10x drives used " generic-mmc" - I selected 
generic-mmc and it worked for me.

Show drive-info option in MissingMediaBurner might give you:
"Device seems to be: Generic mmc2 DVD-R/DVD-RW"

I then selected the "Data" icon.
Selected "burn iso" from choose function.
Drag the iso into the files window and burn.

---

### Post by cerulean coil on 2004-11-10
Right, I'm giving MissingMediaBurner one more try. (I also used YuBurner, on the recommendation of a MacAddict.com forum user. This seems to have worked better, as I can now log into a default session, but I get the same errors as I used to with a safe GNOME session.)

Thanks Huxley. :)

Edit: What 'Write Mode' do I use? I'm going to try the default now, which is -tao.

---

### Post by ljoris on 2004-11-12
[QUOTE=DaveyJJ]OK, for all Mac users out there, here's something to consider. While at work yesterday (a PC environment), I took the downloaded ISO I had on my Mac laptop and transferred it across the network to one of the IT guys. I'd had a programmer at work suggest that maybe, just maybe, the burn-to-disk process itself on the Mac was somehow messing up the byte size or bootability or fiole sizes or naming structures of the files in the ISO.

Sure enough, I get the IT guy to burn to disk the PPC ISO **on a PC** and suddenly the disk works perfectly on my Mac. I tested the "c" key that forces the CD to boot first on my laptop and it works! Bring it home to the old iMac I have a it worked **perfectly**. 

The install did take 30 minutes or so, but I now have a all but useless (for OSX anyways) 266Mhz blue iMac with 196MB RAM running a superbly fast and apparently very stable Ubuntu Linux. Networking etc all works.

My suggestion to Mac users is to make sure they burn the ppc iso on a PC, or at least don't use Toast 6.

Thanks for all help.

David[/QUOTE]


Uhm, dont tell me you are referring to a windows-pc. I burned the ppc-iso on my linux-pc and it doesn work for the powermac 6500/250 i was trying to install it on ... do you have any suggestions ?

---

### Post by badnews_bear on 2004-11-25
I originally installed Yellow Dog Linux on my old 266Mhz Bondi Blue iMac.  I ran into a similar problem with the not being able to read the CDROM at first.  What it turned out to be was the speed at which the CD was burned at.  I had to burn at 1x (I did this on a PC).  Now, any ISO that I create for my iMac is burned at that speed and I haven't had any read problems since.

---

### Post by cerulean coil on 2004-11-26
[QUOTE=badnews_bear]I originally installed Yellow Dog Linux on my old 266Mhz Bondi Blue iMac.  I ran into a similar problem with the not being able to read the CDROM at first.  What it turned out to be was the speed at which the CD was burned at.  I had to burn at 1x (I did this on a PC).  Now, any ISO that I create for my iMac is burned at that speed and I haven't had any read problems since.[/QUOTE]

I burnt mine at 2x, but what the heck, I'll try 1x.

What's another CD anyway? ;)

---

### Post by xico on 2004-11-26
Hello everyone,
I read somewhere in a post:
 "In my case, the only media that would boot on my G3 iMac was a gold
 Apogee cd usually used for audio masters (and about 10x the cost of
 your average CDR. Doh!)"

Tell us if that works!

François

---

### Post by cerulean coil on 2004-11-26
[QUOTE=xico]"In my case, the only media that would boot on my G3 iMac was a gold Apogee cd usually used for audio masters (and about 10x the cost of your average CDR. Doh!)"[/QUOTE]

Ouch.

---

