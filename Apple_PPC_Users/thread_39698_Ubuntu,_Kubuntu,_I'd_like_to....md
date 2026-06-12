---
title: "Ubuntu, Kubuntu, I'd like to..."
date: 2005-06-06
forum: Apple PPC Users
---

### Post by aussie149 on 2005-06-06
Hi,

I have been running X11 and/or Xdarwin on my eMac for some time, with a fair bit of success, thanks largely to Fink.  I wanted to try linux, and liked the look of ubuntu.  I've downloaded ubuntu live and kubuntu live, and they both worked.  I prefer KDE to Gnome, so I downloaded Kubuntu PPC install.  Then the fun started.  

I have tried to install to a firewire drive, creating both a 9Gb and 19Gb free space partition.  The install goes along fine, but the yaboot install fails every time, no matter whether I try to partition manually or automatically.  So, I took a breath and freed up a 2Gb partition on my internal drive.  Tried install again.  Same result: the install gets to yaboot then fails. I am offered the possibility to continue without yaboot, but if I do so, the result appears unbootable. 

What am I missing here? 

1. is it possible to install k/ubuntu on a firewire drive without a degree in IT?  
2.  failing that, how do I simply install it in a little partition on an internal drive - without re-formatting?

All help appreciated.  I have used up a lot of time trying to do something I thought should be quite simple.  I have looked around on this forum, and googled, but couldn't find an answer to this specific problem.

I have an eMac 1.25Ghz running 10.3.9 with 1Gb RAM.  All versions of ubuntu/kubuntu I have tried are 5.04.

Peter

---

### Post by Mez on 2005-06-06
yaboot?

I cant see a yaboot package ... ?

[edit][

Oops - didnt realise this was in PPC - sorry

---

### Post by Rxke on 2005-06-06
What do you mean exactly with 'the install gets to yaboot then fails'?

you mean during install it crashes or doesn't recognize your drives/partitions? Or something else?
I mean does the installer 'say' it fails, or do your changes simply not take effect?

you say you did free up a 2gig partition. How? was this an existing partition decided to use for the install, or did you repartition w/o erasing your disk (using some software gizmo errr... utility)



And IIRC  there  do seem to be some issues with external FireWire drives used as bootdisk, depending on the model etc.... So you'd probably not need an IT degree but a voodoo doctor degree, sigh...

---

### Post by aussie149 on 2005-06-06
[QUOTE=Rxke]What do you mean exactly with 'the install gets to yaboot then fails'?

you mean during install it crashes or doesn't recognize your drives/partitions? Or something else?
I mean does the installer 'say' it fails, or do your changes simply not take effect?

you say you did free up a 2gig partition. How? was this an existing partition decided to use for the install, or did you repartition w/o erasing your disk (using some software gizmo errr... utility)



And IIRC  there  do seem to be some issues with external FireWire drives used as bootdisk, depending on the model etc.... So you'd probably not need an IT degree but a voodoo doctor degree, sigh...[/QUOTE]
 
Thanks.  The installer *tells* me it has failed to install yaboot, in front of a startling red screeen to emphasise the message.  Good question about the 2 Gb partition.  I thought I had I had freed it up by erasing the partition.  When I use the *gizmo* to look at it, it shows up as UNIX_SVR2, rather than free space.  Is there a way I can make it free space,without wiping the whole drive?  I used the gizmo program to create free space for the  partitions on the external drive, but can't use it on my internal drive.  It just won't create free space on that drive.
 

Voodoo is good, rhymes with ubuntu, kubuntu...

---

### Post by aussie149 on 2005-06-06
I just found this in another post.  Would it work on my 2Gb UNIX partition, I wonder?  and is 2GB enough to do anything?  [I really wanted to use my external disk because it's 200GB, lots of acreage,  Anyway here was the post:

QUOTE: Hi - I’m also an absolute linux newbie. The following worked for me.

After booting from the CD you choose as required:
language
location
keyboard
detect hardware (automatic)
scanning CDrom (automatic
loading installer components (automatic)
detecting network (automatic)
configuring network (automatic)
enter hostname (you enter a name here)
detecting disks and hardware (automatic)
start partitioner (automatic)

partition disks screen - select manually edit partition table then scroll to the partition you wish to use which I believe in your case is the 12 gig partition then hit return (be careful to select the correct partition here). Then select delete the partition. This should now show as FREE SPACE.
Select the FREE SPACE and hit return then select automatically partition free space. The partitioner will do the rest and create the appropriate 3 partitions for boot, swap, and /.QUOTE

---

### Post by Rxke on 2005-06-06
that's indeed pretty much the way to go. And "2Gig should be enough for everyone"  :razz:  ;-) 
(seriousl, it should be enough, but not really errrr... plenty...)

it doesn't matter wether it's empty/unix /mac formatted or whatever, like the above poster explained, you can erase it using the installer. just make double sure you erase the right partition, and then do the automatic thingy... it then works out a sub-partitioning of that partition, and you get rederected back to the screen with your partitions. If you don't like what you see, just exit or retry, it doesn't actually do anything untill you explicitly commit the changes....

---

### Post by aussie149 on 2005-06-06
[QUOTE=Rxke]that's indeed pretty much the way to go. And "2Gig should be enough for everyone"  :razz:  ;-) 
(seriousl, it should be enough, but not really errrr... plenty...)

it doesn't matter wether it's empty/unix /mac formatted or whatever, like the above poster explained, you can erase it using the installer. just make double sure you erase the right partition, and then do the automatic thingy... it then works out a sub-partitioning of that partition, and you get rederected back to the screen with your partitions. If you don't like what you see, just exit or retry, it doesn't actually do anything untill you explicitly commit the changes....[/QUOTE]
 
Thanks Rxke.  I have tried this, and it went smoothly *until* we got to the instal yaboot part.  at that point, I was given one choice only of /dev/hda6 to install yaboot.  I slected it and *bingo* the same red screen of disaster, telling me that the installer had failed to install yaboot.  going back simply gave the same choices.  Proceeding has presumably installed an unbootable ubuntu: on re-starting the mac just goes into os x straight away.

Bummer! still stuck :-((

---

### Post by pvz on 2005-06-06
Did the installer create a small bootpartition were yaboot can reside, or did you create one yourself? This is necessary to install the bootloader. I'm not sure if it can be done without reformatting your harddrive, and thus wiping out your existing OSX install. A couple of mb should be enough, and the partition type can be set during installation. Choose type boot. If you decide to go this way you could make an install in that 2gb partition and have your yaboot install in it's own partition, and make some other partitions like /home and /data, or whatever, on the external firewire. You should be able to format it when making the other partitions during installation, and it should then show up on your desktop when you plug it in..

---

### Post by Rxke on 2005-06-06
*slaps forehead pretty hard*

Urgh. Now I rmember the headaches it gave me (slapping and head-to-wall-contact) to try to install it on an *existing* OSX system...

it is probably possible but not at all straightforward....

But the main problem is the installer doesn't recognize your external drive as bootable (or at all?), otherwise it should show up during the partitioning process... I have 2 HDD, both internal, and it showed both... Firewire not bootable for Kubuntu? possible...

Hmmm... The only way you could surely make it work, is backup your stuff to the external or on optical disks, then reformat the drive in partitions, using your installdisks of OSX, just don't start the install, but select from the menu the diskutility... keep one partition for Kubuntu... restart with kubuntu cd, then install Kubuntu on that partition, then re-install osx... Or was it the other way round, first X, then kubuntu???? Dang, should've kept notes, grrrrr...

Ok, seems like I`m not much of a great help, better STFU  :-?

---

### Post by Ptero-4 on 2005-06-06
[QUOTE=Rxke]*slaps forehead pretty hard*

Urgh. Now I rmember the headaches it gave me (slapping and head-to-wall-contact) to try to install it on an *existing* OSX system...

it is probably possible but not at all straightforward....

But the main problem is the installer doesn't recognize your external drive as bootable (or at all?), otherwise it should show up during the partitioning process... I have 2 HDD, both internal, and it showed both... Firewire not bootable for Kubuntu? possible...

Hmmm... The only way you could surely make it work, is backup your stuff to the external or on optical disks, then reformat the drive in partitions, using your installdisks of OSX, just don't start the install, but select from the menu the diskutility... keep one partition for Kubuntu... restart with kubuntu cd, then install Kubuntu on that partition, then re-install osx... Or was it the other way round, first X, then kubuntu???? Dang, should've kept notes, grrrrr...

Ok, seems like I`m not much of a great help, better STFU  :-?[/QUOTE]
 You have to make the partitions with the OSX CD, install OSX and then Ubuntu (write down the partition number of the partition where OSX is installed) (if you do it the other way round the OSX bootloader will overwrite yaboot and since the OSX bootloader doesn't support multiboot you'll end up with an unbootable Ubuntu install). And after installing both OSX and Ubuntu, boot into Ubuntu and in a terminal window type gksu gedit /etc/yaboot.conf, once in gedit go to the end of the document add a new line and type macosx=/dev/hdxn (hdxn means the partition number where OSX is installed) and save the document (if you want to boot OSX by default look for the line that says defaultos= and replace whatever is at the right of the equal sign with the word macosx). After that in the terminal window type sudo ybin -v and when it finishes you're ready, reboot (if you want, it's not needed but you'll probably want to test-drive your new yaboot config right away.)

---

### Post by aussie149 on 2005-06-07
[QUOTE=Ptero-4]You have to make the partitions with the OSX CD, install OSX and then Ubuntu (write down the partition number of the partition where OSX is installed) (if you do it the other way round the OSX bootloader will overwrite yaboot and since the OSX bootloader doesn't support multiboot you'll end up with an unbootable Ubuntu install). And after installing both OSX and Ubuntu, boot into Ubuntu and in a terminal window type gksu gedit /etc/yaboot.conf, once in gedit go to the end of the document add a new line and type macosx=/dev/hdxn (hdxn means the partition number where OSX is installed) and save the document (if you want to boot OSX by default look for the line that says defaultos= and replace whatever is at the right of the equal sign with the word macosx). After that in the terminal window type sudo ybin -v and when it finishes you're ready, reboot (if you want, it's not needed but you'll probably want to test-drive your new yaboot config right away.)[/QUOTE]

Thanks folks.  I've been offline for a day trying again to install both internally and externally.  Yes, the kubuntu partitioner sees all the partitions, inc. those on the firwire disk.  I keep getting stuck with the "yaboot fail" step.  In the external boot, it gives me only one option [sda3] to install yaboot, then fails to install it.  So, I am not sure how to boot into  ubuntu, even if it is there?  Is there some way to install yaboot "manually", by moving files or terminal command in OS X?  Sorry to be such a pain, I wish I wasn't - and now Apple tells me it's going to Intel chips, so we're all learning this for a platform that will not be manufactured from 2006!

Peter

---

### Post by aussie149 on 2005-06-07
I'm still trying with this.  Today, I've spent some time trying to tweak the partitions to make it work. I've tried getting the installer to automatically partition the 2Gb section, having deleted it to create free space: the partitioner does it nicely, EXCEPT that the black-face symbol appears next to what it has set up as a boot partition, and I know that is the black face of doom, which leads inexorably to the red screen of failure to install yaboot later.  

I delete the boot partition to create free space again, and try to set up  a boot partition manually.  I also delete  anything with a lightning symbol that looks like it is a phantom boot space.  I've automatically partitioned in one partition, and in "desktop" mode, but both were unsuccessful.   Nothing has worked so far: always the yaboot install fails.  I hate to admit defeat, probably the Irish in me - or the Scots.  I will keep trying.  

One thing I *did* discover in all this, is that the install process is a darn sight faster on the internal drive than the firewire [like minutes instead of hours, kidding aside].

PS is there any relevance in the choice of kernels, between linux-powerpc; linux-image-powerpc; linux-image-2.6.10-5powerpc?

---

### Post by pvz on 2005-06-07
A lightning symbol is good, if I'm not mistaken. I think it means that the partition is bootable, going from memory. You should be able to toggle the boot partition in the installer menu, something like "set partition as boot", going from memory again. It seems like you're pretty close now  :smile:

---

### Post by aussie149 on 2005-06-08
[QUOTE=pvz]A lightning symbol is good, if I'm not mistaken. I think it means that the partition is bootable, going from memory. You should be able to toggle the boot partition in the installer menu, something like "set partition as boot", going from memory again. It seems like you're pretty close now  :smile:[/QUOTE]

Yes, the lightning symbol is for the boot partition I believe.  I can turn the bootable flag on or off.  The problem I keep coming up against is that I not only have a lighnting symbol, but next to it is this ominous black face [an aside: is linux racist, where black faces are bad and white are good?] which I can't seem to get around.  

I'm now only trying to install on the internal disk.  I used a disk gizmo program to tidy up the device, clearing lots of contiguous free space and putting it towards to the front/top of the disk, and reducing the number of partitions [I had got up to about 18 during all this, now I start with about five or six].  I am now trying to install onto a 2.6 GB partition, instead of 2.0 GB.  The thing that keeps stopping me is this @#% fail on the yaboot install, which I relate to the fact that I can't seem to get the boot partition to show upo with a smiley face symbol!  I have tried both the basic automatic partition adn the desktop partitoning.  In each case the offending partition shows up as 1 MB, with the ominous face and the boot-lightning symbols.  

I am starting to think that nothing short of a complete reformat is going to convince this installer to install a yaboot partition, but I seem to remember some instructions for setting up a linux boot where you placed a couple of specific boot files at the base level of your disk, and yaboot worked.  

Can anyone help on this?  Thanks for all input so far.  An interesting journey!

---

### Post by Rxke on 2005-06-11
Any luck yet?

---

### Post by aussie149 on 2005-06-12
[QUOTE=Rxke]Any luck yet?[/QUOTE]

No, but thanks for your interest and help.  It seems a reformat may be the only way to get yaboot installed.  I really think I am going to have to start backing up my internal drive, and then re-format, leaving a reasonable free space partition [maybe 6 GB or even 10 GB].   To do that, I will need to find some extra space somehow.  That may mean sacrificing my X11 stuff [currently about 13 Gb], or possibly trying to link to the X11 programs on an external drive, if I can work out how to do that [do I simply move the /sw/bin and some other directories to an external drive, and set up a path to them in X11, or will that muck up some of my OS X programs as well?]

I'm trying to work ou the best way to do this still.

---

### Post by pvz on 2005-06-12
I just installed Debian Sarge on a spare partition on my iBook alongside Kubuntu and  OSX, and I paid some extra attention to the bootstrap partition. On my iBook it resides on /dev/hda2 and is only 1 mb in size. It has the lightning bolt and the "black face" next to it, and I have no problems installing yaboot.. I noticed that the face turns white if you highlight it btw. I have no clue why this won't work for you..

---

### Post by godsunderstudy on 2005-06-12
Came the Fink route on an eMac 4 months ago and Yes, we had an interesting time trying to install Ubuntu. Several interesting times, in fact. Ptero-4 is correct, IMO, especially about backing everything up. 
Only 2 partitions are needed, cos the Ubuntu Hoary install adds the rest.
Put both OS X and Ubuntu on your internal drive. It just works. You can play about later.
I would start with Ubuntu cos on my eMac and iMac Hoary is stable (as in Ubuntu rocks) and kubuntu is ..... flaky. Which is wierd, because in Warty it seemed the other way around.
Eventually OS X will overide yaboot. You have to change somesuch OS X config file to stop it happening. Alternatively, hold down the alt key during bootup.

BTW this is godsundersudysdad who can't be bothered with logout then login

---

### Post by aussie149 on 2005-06-15
[QUOTE=godsunderstudy]Came the Fink route on an eMac 4 months ago and Yes, we had an interesting time trying to install Ubuntu. Several interesting times, in fact. Ptero-4 is correct, IMO, especially about backing everything up. 
Only 2 partitions are needed, cos the Ubuntu Hoary install adds the rest.
Put both OS X and Ubuntu on your internal drive. It just works. You can play about later.
I would start with Ubuntu cos on my eMac and iMac Hoary is stable (as in Ubuntu rocks) and kubuntu is ..... flaky. Which is wierd, because in Warty it seemed the other way around.
Eventually OS X will overide yaboot. You have to change somesuch OS X config file to stop it happening. Alternatively, hold down the alt key during bootup.

BTW this is godsundersudysdad who can't be bothered with logout then login[/QUOTE]
  

Update: Still trying.  I am using Ubuntu Live to send this message.  That's not a good sign.  My daughter's fiance talked me out of reformating my internal drive.  

Instead I reformatted the external drive, leaving free space at the beginning of the drive, and putting my backup on the back part of the drive.  I then installed kubuntu.  Same problem: gets to yaboot bootloader install and fails.  

I used a drive program to clear free space again.  Tried ubuntu this time, in case the problem was with my .iso image on the kubuntu disk.  Same problem again.  Yaboot fail.

As far as I can see with fdisk, there are the appropriate partitions there, but I obviously can't boot into ubuntu to see whether it works. 

I am now reluctant to reformat and install onto my internal disk, if I am just going to see the same harsh red "yaboot install fail" screen at the end of the process. 

 Maybe when I upgrade to Tiger I might try again!

---

### Post by Rxke on 2005-06-17
Do not upgrade to Tiger for getting Ubuntu, it's even worse, Tiger's case-sensitive formatting breaks the installer, from what i've read.

Anyway, 

did you try to do it from the live-cd? [http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/](http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/)

(you DO have a free partition? if not you will have to reformat anyway, or use a third party program to resize your disk...)

---

### Post by aussie149 on 2005-06-18
[QUOTE=Rxke]Do not upgrade to Tiger for getting Ubuntu, it's even worse, Tiger's case-sensitive formatting breaks the installer, from what i've read.

Anyway, 

did you try to do it from the live-cd? [http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/](http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/)

(you DO have a free partition? if not you will have to reformat anyway, or use a third party program to resize your disk...)[/QUOTE]

Disappointing news about Tiger, but I am reluctant to reformat my internal drive until I do a mjaor update, and it seems I won't get [k]ubuntu to work unless I do.  

Yes, I do have a free partition created by a drive program: it all looks OK, apart from the darkened face icon next to that boot partition in the partitioning process, then the bootloader install fail at that part of the process.  

I read Rachel's blog [above], but it's a bit technical for me [partiton IDs?chroots? etc]: I am afraid of doing major damage to files I might want to keep! 

Thanks for the suggestions.

---

### Post by Rxke on 2005-06-18
[QUOTE=aussie149].... it's a bit technical for me [partiton IDs?chroots? etc]: I am afraid of doing major damage to files I might want to keep! [/QUOTE]

when in doubt, do nothing. That's the safest approach in such cases.

BTW, I'm going back to Debian for my deskcomputer. I had the idea (years ago,) I was much more able to understand why things didn't work, when setting up the system. Ubuntu is sometimes too 'easy,' you don't have to follow a crash course in Linux to get it running (normally) but you don't learn anything about the filesystem etc...

My iBook'll stay Kubuntu, though. just works too good to do away with.

---

### Post by dudeman on 2005-08-05
I figured out that if you install from the warty cd, and then automatically update, yaboot will install just fine. Hope that helps!

---

### Post by TroutMaskReplica on 2005-09-04
i'm new to linux, and i was trying to install ubuntu onto an external firwire drive just like the original poster, after having a great experience with the live CD. also just like the original poster the reformatting went fine but the install continually fails at the yaboot stage. the error message that is generated at that time is very unhelpful.

i'm a little disappointed in ubuntu right now. i've wasted half a day on this and there appears to be no clear cut way to work around what appears to be a critically flawed installation process.

i don't feel i can trust my data to ubuntu at this time (even if i were able to get it working). i'll try again when the next version comes out (maybe).

---

