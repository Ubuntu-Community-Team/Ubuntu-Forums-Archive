---
title: "PowerBook G4"
date: 2014-04-29
forum: Apple Hardware Users
---

### Post by gulmer on 2014-04-29
I just installed Lubuntu on my Apple PowerPc laptop. The install went fine, the OS is usable except no WIFI and I can't get the battery icon on the panel. I ran lspci -nn | grep 0280 in terminal and the internal Broadcom BCM4306 v3 showed up, even the USB WIFI adapter showed up(Ralink). I went to Synaptics and installed the b43 driver, restarted and still no wifi. There seems to be no program to even show the wireless networks. I'm a long time Ubuntu user and I know wifi with Ubuntu but Lubuntu's new to me, at least navigating it's desktop is, so I downloaded Ubuntu for the PowerPc and tried the live cd in the Apple. Unfortunately, the main desktop was a white blank and the network program or any program disappeared behind the white, but the top panel was visible and I could see that Ubuntu could search for wifi networks and connect to my router, but I could not do anything past that. So, I've got Lubuntu installed and want my wife to use this laptop, but she needs the wifi to work. What is my next move to get WIFI to work? :confused:

---

### Post by este.el.paz on 2014-05-01
@Gulmer:

You aren't saying what version you are trying to install . . . assuming it is 14.04???  Probably easier to go to 12.04, everything should work better there; I think I recall seeing some issues with network manager?? in 14.04 Lubuntu on the Lu users list serve???  Haven't yet had time to try an install on my iBook . . . .

But, if you have 14.04 and want to keep it, you ***probably*** will need the "b43-legacy" driver, not just the "b43" . . . that might make a difference . . . and with the "white screen" you might have to try out some boot params or set up the proper xorg.conf file if you are already installed . . . that I really can't help you with, but there are links to sites that have pre-made xorg,conf files . . . usually it's about selecting the proper video driver for your display . . . possibly "nvidia" or "radeon" . . . can be a little bit of a pain to get the screen working, after that should be OK, except I guess for sound doesn't seem to be working out of the box in 14.04 . . . hence the suggestion for 12.04 . . . in Lubun or Xubun or whichever . . . .

e.e.p.

---

### Post by gulmer on 2014-05-01
The b43-legacy did nothing, a suggestion to install the linux-firmware-nonfree for the driver was made, still not connecting. The Broadcom card sees my network, just no connection.

---

### Post by este.el.paz on 2014-05-01
> **gulmer said:**
> The b43-legacy did nothing, a suggestion to install the linux-firmware-nonfree for the driver was made, still not connecting. The Broadcom card sees my network, just no connection.

OK, failure is part of life, or rather, living . . . did you then "uninstall" the regular b43 module?  Sometimes there are a few extra steps that have to be done to get something to be recognized . . . did you read through the PowerPCFAQ on getting wifi working?

But, the first question I asked remains untouched . . . is this 14.04 or 12.04?  Or something else?

e.e.p.

---

### Post by gulmer on 2014-05-01
Lubuntu 14.04 and no did not read the PPCFAQ, will be my next step. Another helper said that the b43 module should not be interfering since I'm using the linux-firmware-nonfree. Can't hurt to try, though.

---

### Post by este.el.paz on 2014-05-01
> **gulmer said:**
> Lubuntu 14.04 and no did not read the PPCFAQ, will be my next step. Another helper said that the b43 module should not be interfering since I'm using the linux-firmware-nonfree. Can't hurt to try, though.

OK, there is also a "PPCknown issues" page that you might be able to find, it is linked I believe in the "PPC Testers wanted for 14.04" thread . . . but the PPC stuff is no longer placed in obvious plain sight . . . but would probably be linked from the PPCFAQ page . . . .  Thinking about this a bit, as I mentioned there is something about the "Network manager" mentioned as an issue in the Lu 14, and even on my iMac w/12.04 after some update/upgrade there is an "x" next to the network icon and it says that "wifi is not available" . . . since it's stationary and hardwired I don't "need" wifi . . . but some experts have mentioned loading "wicd" as an option to getting a connection . . . .  I've done so many installs of various linux flavors I know at one point I had wicd AND nm going . . . so might look into that . . . .

Otherwise, for PPC, since it's falling behind the wave of technology and 14.04 is brand new and still a work in progress, you might try 12.04, probably be closer to working right out of the box . . . ***easier**** and then, as I mentioned, in 14.04 can you plug in ethernet and get a connection?  Because it seems like if you get wifi working then the next missing link in 14.04 is "sound" for PPC . . . .

e.e.p.

---

### Post by rsavage on 2014-05-01
> **este.el.paz said:**
> OK, there is also a "PPCknown issues" page that you might be able to find, it is linked I believe in the "PPC Testers wanted for 14.04" thread . . . but the PPC stuff is no longer placed in obvious plain sight . . . but would probably be linked from the PPCFAQ page . . . . 

The FAQ and Known Issues pages are on the getlubuntu page [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Mac_systems](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Mac_systems) .  It tells you to read them before installing.  Again they are linked on the main Downloads page [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) with the same message.  They are linked on the first thread of this forum.  I'm not sure what more can be done to make people look at them.

For some unknown reason (well actually I know the reason - they were trying to write to non-techies) lubuntu have a powerpc wiki page too, but most of the information is wrong and I wish they'd get rid of it.  Thankfully, that is the wiki page that is hard to find.

---

### Post by gulmer on 2014-05-01
Burning 12.04 to disc now and will see if that works with wifi any better.

---

### Post by este.el.paz on 2014-05-01
@Gulmer:

Should be easier to get it working w/12.04 . . . still will have to use the "additional drivers" app to find the right module for your machine, but it should show you that as an option . . . .

@rsavage:  I did reply to your post, saying thanks for the links, and offering some other thoughts about how it isn't exactly clear to find the PPC links, but, it seems to have been deleted????  Or wasn't posted???  Should have been "acceptable" to the forum????  Gone . . . .

e.e.p.

---

### Post by gulmer on 2014-05-01
The live cd should show me if the wifi is working?

---

### Post by este.el.paz on 2014-05-01
> **gulmer said:**
> The live cd should show me if the wifi is working?

It might, can't remember frankly . . . but, the install might require that the proper driver be added . . . .

e.e.p.

---

### Post by John_Ross_Hunt on 2014-05-01
I had the same problem with my PowerBook.  After installing the firmware, you need to remove and reload the wireless module for it to take effect.

[COLOR=#2E8B57][FONT=Monaco]sudo rmmod b43[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]sudo modprobe b43[/FONT][/COLOR]

---

### Post by este.el.paz on 2014-05-03
@Gulmer:

Any updates?  Success?  Failure?  If the question is "answered" and your install went well, you can mark the thread as "solved" in the thread tools menu top right . . . .

e.e.p.

---

### Post by robert94 on 2014-05-04
ok 2 of us now :o

I have a Powerbook G4 too. I managed to get lubuntu 14.04 working from a live DVD but like you no Wifi which is very frustrating :( 

My issue is further compounded in the the G4's Ethernet port does not work [I am trying to ascertain whether this is a HW failure]

So I can't even install updates such as [COLOR=#333333]firmware-b43-installer etc, well unless someone explains how to do that for me when booted from a live DVD with no Wifi or Ethernet !
[/COLOR]
So I have almost given up...unless I try a 12.04 ubuntu minimal install and assume the wifi will work straight out of the image ?

HELP !

---

### Post by rsavage on 2014-05-04
It's all in the FAQ.  You both just need to look at the Airport Extreme section. If you can't get the ethernet port working then you just download the firmware from MacOSX and save it where you can access it.

---

### Post by robert94 on 2014-05-04
> **rsavage said:**
> It's all in the FAQ.  You both just need to look at the Airport Extreme section. If you can't get the ethernet port working then you just download the firmware from MacOSX and save it where you can access it.

Hi thank you for the reply

I'm a newbie so I guess I will have to try and figure out how and where from to download the b43 packages from MacOSX and save it to a usb stick [& hope I can access that from a live DVD boot], that said it appears the original thread creator tried b43 with no success ?

Do you have a PowerBook G4 working with Wifi on Lubuntu 14.04 ?

ps: What terminal commands can I use to determine whether the Ethernet port is really dead ?

---

### Post by rsavage on 2014-05-04
Yes I have wifi working in 14.04 on the two iBooks I have access to.  One uses the default network manager without problem, the other I have to use wicd.  Not entirely sure why that is (they both have exactly the same card as far as I'm aware) so it might be the different access points causing the annomaly.  I can't be bothered to look into it.

I'm sure you think I'm quite unhelpful telling you both to read the FAQ, but what you ask is honestly all in there.  You just need to follow the links i.e. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Lubuntu is slightly different in that the b43-fwcutter is already installed on the live iso.

---

### Post by rsavage on 2014-05-04
Ethernet should just work when it is plugged in.  If it doesn't work in OSX and lubuntu then I guess you can say it is hardware failure.

---

### Post by gulmer on 2014-05-04
After installing 12.4, Hadaka had me run this set of codes;sudo apt-get update
sudo apt get install linux-firmware-nonfree
sudo modprobe b43
Then I moved the panel to the top of desktop, where for the first time I got the wireless manager icon that I could open and put in the info for my router and bodabing bodaboom, I now have a good wireless connection. Thanks all for your help.

---

### Post by robert94 on 2014-05-06
> **rsavage said:**
> Yes I have wifi working in 14.04 on the two iBooks I have access to. One uses the default network manager without problem, the other I have to use wicd. Not entirely sure why that is (they both have exactly the same card as far as I'm aware) so it might be the different access points causing the annomaly. I can't be bothered to look into it.

I'm sure you think I'm quite unhelpful telling you both to read the FAQ, but what you ask is honestly all in there. You just need to follow the links i.e. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Lubuntu is slightly different in that the b43-fwcutter is already installed on the live iso.

Thank you for the reply

ok I have booted from my lubuntu 14.04 live DVD and installed b43-fwcutter which appeared successful
I then ran [COLOR=#333333][FONT=UbuntuMono]sudo modprobe -r b43 bcma and then [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo modprobe b43 [I couldn't reload as I am running from a live DVD]
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]I then ran lshw -class network and that shows BCM4306 using configuration driver=b43-pic-bridge
But nm-tool only shows eth0 wired but no Wifi networks or WLAN adapter

When I run lspci -vvnn etc that shows the controller is BCM4306 rev02 so I know I have the right b43 driver

Question: What command[s] can I issue to see if I now have an enabled Wifi adapter ?

I think I am getting closer ?

[/FONT][/COLOR]
> **gulmer said:**
> After installing 12.4, Hadaka had me run this set of codes;sudo apt-get update
sudo apt get install linux-firmware-nonfree
sudo modprobe b43
Then I moved the panel to the top of desktop, where for the first time I got the wireless manager icon that I could open and put in the info for my router and bodabing bodaboom, I now have a good wireless connection. Thanks all for your help.

I assume you installed Ubuntu 12.04 PPC since there is no 12.04 PPC for Lubuntu ?

---

### Post by este.el.paz on 2014-05-06
> **robert94 said:**
> [COLOR=#333333][FONT=UbuntuMono]
I think I am getting closer ?

[/FONT][/COLOR]I assume you installed Ubuntu 12.04 PPC since there is no 12.04 PPC for Lubuntu ?

@robert:

You can do this wifi driver thru the terminal, but you can also use the "add'l drivers" app as well . . . you might have to log out or restart to get the system to "see" the upgrade . . . but, to your "there is no 12.04 PPC for Lubuntu" . . . there is, for most of the 12.04 flavors there is a PPC version . . . it's just in the 14.04 LTS that it looks like Lubuntu is the only choice in PPC??  I haven't checked out the "alternate" or minimal install versions to see if you can do PPC that way, and then add in your DEs, probably could . . . .  But, for Lubun 12.04 PPC . . . [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/)

e.e.p.

---

### Post by robert94 on 2014-05-07
> **este.el.paz said:**
> @robert:

You can do this wifi driver thru the terminal, but you can also use the "add'l drivers" app as well . . . you might have to log out or restart to get the system to "see" the upgrade . . . but, to your "there is no 12.04 PPC for Lubuntu" . . . there is, for most of the 12.04 flavors there is a PPC version . . . it's just in the 14.04 LTS that it looks like Lubuntu is the only choice in PPC??  I haven't checked out the "alternate" or minimal install versions to see if you can do PPC that way, and then add in your DEs, probably could . . . .  But, for Lubun 12.04 PPC . . . [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/)

e.e.p.

@ e.e.p. The reason I didn't think there was a Lubuntu 12.04 for PC was because at [this]("https://wiki.ubuntu.com/PowerPCDownloads") location PPC for 12.x Lubuntu was not listed so thank you for the new link

Why did you give up on 14.04 ?

Note I am running of a live DVD so cannot reboot or download drivers as the Ethernet port does not work and I do no want to destroy the MAC OS 10.3.9 partition [yet] until I know I can get the Wifi to work

---

### Post by este.el.paz on 2014-05-07
> **robert94 said:**
> @ e.e.p. The reason I didn't think there was a Lubuntu 12.04 for PC was because at [this]("https://wiki.ubuntu.com/PowerPCDownloads") location PPC for 12.x Lubuntu was not listed so thank you for the new link
Why did you give up on 14.04 ?
Note I am running of a live DVD so cannot reboot or download drivers as the Ethernet port does not work and I do no want to destroy the MAC OS 10.3.9 partition [yet] until I know I can get the Wifi to work

No worries, sometimes it's a tad obtuse to find stuff, you have to use belief.  But, I haven't exactly "given up" on 14.04; I have the 64 bit Xubun/MATE intel version installed on my MBPro . . . still needs a bit of tweaking.  Probably my G4 iMac will not make the jump up to 14, the difficulties are beyond my skilz . . . but, perhaps if a few things get fixed my 933MHz iBook ***might*** be do-able . . . I'm still testing the LiveDVD and maybe in a bit I may try a fresh download of it.  However, 12.04 is perfectly fine for PPC, a lot of issues have been thrashed through, and PPC is well supported in various flavors . . . it's fine.  It does seem that 14 is still in testing, particularly for PPC.

In terms of your ethernet issues, hopefully you caught rsavages suggestions of getting the firmware from OSX for ethernet??  I can't elucidate on that, but, all of my Macs are either dual boot or triple boot . . . unfortunately in PPC you would have to wipe the disc to partition it, but being able to use OSX can be very helpful.  As I mentioned before, if getting the OSX ethernet firmware and moving it over to a USB drive or CD and somehow installing it into a linux install is beyond your skilz, then physically replacing it might be the easiest way to go . . . and then for sure you should be able to do the install and then get the wifi driver, etc.
e
.e.p.

---

### Post by robert94 on 2014-05-09
> **este.el.paz said:**
> No worries, sometimes it's a tad obtuse to find stuff, you have to use belief.  But, I haven't exactly "given up" on 14.04; I have the 64 bit Xubun/MATE intel version installed on my MBPro . . . still needs a bit of tweaking.  Probably my G4 iMac will not make the jump up to 14, the difficulties are beyond my skilz . . . but, perhaps if a few things get fixed my 933MHz iBook ***might*** be do-able . . . I'm still testing the LiveDVD and maybe in a bit I may try a fresh download of it.  However, 12.04 is perfectly fine for PPC, a lot of issues have been thrashed through, and PPC is well supported in various flavors . . . it's fine.  It does seem that 14 is still in testing, particularly for PPC.

In terms of your ethernet issues, hopefully you caught rsavages suggestions of getting the firmware from OSX for ethernet??  I can't elucidate on that, but, all of my Macs are either dual boot or triple boot . . . unfortunately in PPC you would have to wipe the disc to partition it, but being able to use OSX can be very helpful.  As I mentioned before, if getting the OSX ethernet firmware and moving it over to a USB drive or CD and somehow installing it into a linux install is beyond your skilz, then physically replacing it might be the easiest way to go . . . and then for sure you should be able to do the install and then get the wifi driver, etc.
e
.e.p.

Good news with rsavages help :)  [see my more recent thread [here]("http://ubuntuforums.org/showthread.php?t=2222807")] I have got wifi to work on my PowerBook G4 from the live DVD. Now that I know it works I am keen to dual boot but he problem I now is that the Apple has MAC OS 10.3.9 which does not allow one to resize the existing UFS partition if I don't want to loose it [which I dont']. So I either needs to find a 10.5.x install disk as Leopard allows resizing of some 3rd party software...I checked and gparted cannot resize UFS partitions

---

### Post by rsavage on 2014-05-09
Are you sure you are using UFS?  I maybe wrong, but I thought HFS+ was generally used? - [https://wiki.ubuntu.com/PowerPCFAQ#What_do_I_need_to_know_for_dual-booting.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_do_I_need_to_know_for_dual-booting.3F)

---

### Post by este.el.paz on 2014-05-09
> **robert94 said:**
> Good news with rsavages help :)  [see my more recent thread [here]("http://ubuntuforums.org/showthread.php?t=2222807")] I have got wifi to work on my PowerBook G4 from the live DVD. Now that I know it works I am keen to dual boot but he problem I now is that the Apple has MAC OS 10.3.9 which does not allow one to resize the existing UFS partition if I don't want to loose it [which I dont']. So I either needs to find a 10.5.x install disk as Leopard allows resizing of some 3rd party software...I checked and gparted cannot resize UFS partitions

@robert:

> all of my Macs are either dual boot or triple boot . . . unfortunately  in PPC you would have to wipe the disc to partition it, but being able  to use OSX can be very helpful.  For sure, 10.4.11 is HFS+ . . . but, as I mentioned you can't drag the disk to re-partition it the way you can with intel processor . . . I'm pretty sure I asked some advice on that two years ago when I started w/linux installs.  You either have to clone your existing system to an ext HD by FW, then boot into it to wipe the HD, or use the install DVD to do that, partition the drive, re-install OSX, then lastly install linux.

e.e.p.

---

### Post by rsavage on 2014-05-09
@eep are you sure?  There is a lot of inaccurate information out there.  It would be good to get some clarity on it.  Gparted is supposed to be able to shrink HFS+ partitions.  You may have to install the hfsprogs package first.  It will probably take a long time.

Also there is the diskutil commandline tool in OSX - [https://developer.apple.com/library/mac/documentation/Darwin/Reference/Manpages/man8/diskutil.8.html](https://developer.apple.com/library/mac/documentation/Darwin/Reference/Manpages/man8/diskutil.8.html)

The info from the intel community wiki says:

For pre-Leopard OS X, there are no such tools. [BootCamp]("https://help.ubuntu.com/community/BootCamp") does not run, and DiskUtility  will only allow you to create more partitions if you wipe out all the  current partitions. However, the underlying commandline utility still  exists. 

Here's  a usage example. Let&#8217;s say you want to resize your OS X partition to  200GB and leave the rest of the disk free (for Ubuntu of course). You  would open a terminal and type the following, followed by the "Return"  key. 

sudo diskutil resizeVolume disk0s2 200G

You can read more on diskutil by typing 'diskutil help' in your OS X terminal.

---

### Post by rsavage on 2014-05-09
A bit of googling and the diskutil resizevolume command seems to only work in Tiger 10.4.6 and above....

---

### Post by rsavage on 2014-05-09
....and maybe doesn't work with the PowerPC partitioning scheme.....

---

### Post by este.el.paz on 2014-05-09
> **rsavage said:**
> @eep are you sure?  There is a lot of inaccurate information out there.  It would be good to get some clarity on it.  Gparted is supposed to be able to shrink HFS+ partitions.  You may have to install the hfsprogs package first.  It will probably take a long time.
You  would open a terminal and type the following, followed by the "Return"  key. 
sudo diskutil resizeVolume disk0s2 200G
You can read more on diskutil by typing 'diskutil help' in your OS X terminal.

@rsavage:

Never 100% sure about anything in this world, let alone linux stuff . . . but, at that time I did post question on the OSX Technologies forum and other places on the Apple forum, because, as you say, there is a tremendous amount of information and much is just opinion . . . but, seemingly the advice was that, and maybe this was just the "easiest" way, but needing to wipe the disk to re-partition it was the accepted or recommended method . . . .  The only **problem*** might be needing a large enough FW HD to clone the present system/data to . . . otherwise, at that time Carbon Copy Cloner was free to folks like me who were either students or faculty . . . and half hour or so to clone . . . .  So, the only issue is if no $$ for the ext HD, then maybe trying your diskutil method, but the OP has 10.3.9 Pannnntherrr . . . it's hard to get everything we think we want in this world . . . sometimes sacrifices must be made . . . .  But, safest way is to first clone the present system, then whatever you do to the disk you have the backup . . . but, OSX does not play well with others, so it goes in first, if it goes in last the install messes with the Yaboot set up, perhaps for guyz who know what they are doing, easy to fix . . . but, I'm just basically a "plug-n-play" user, end user . . . I like easy . . . wipe the HD, re-partition it, install OSX, install the linux of choice . . . still I'd say 12, no?

e.e.p.

---

### Post by rsavage on 2014-05-09
Thanks eep.  I think what you are saying is indeed the recommended.  People seem obsessed with putting the yaboot partition first on the disk and the only way to do this is to move the partitions about. I'm still not sure why this is (EDIT: probably this [http://www.fixstars.com/en/technologies/linux/support/solutions/ydl_general/reset_boot/](http://www.fixstars.com/en/technologies/linux/support/solutions/ydl_general/reset_boot/) ).

I also can't find anything that says gparted doesn't work with HFS+ on powerpc.  The only advice seems to be to disable journalling.

---

### Post by este.el.paz on 2014-05-09
> **rsavage said:**
> Thanks eep.  I think what you are saying is indeed the recommended.  People seem obsessed with putting the yaboot partition first on the disk and the only way to do this is to move the partitions about. I'm still not sure why this is (EDIT: probably this [http://www.fixstars.com/en/technologies/linux/support/solutions/ydl_general/reset_boot/](http://www.fixstars.com/en/technologies/linux/support/solutions/ydl_general/reset_boot/) ).

I also can't find anything that says gparted doesn't work with HFS+ on powerpc.  The only advice seems to be to disable journalling.

@rsavage:

You edited the post since I got the email . . . I was going to say, yeah, I did that Startup Disk gaffe recently . . . and I think I just did a total fresh install to get around it.  Since I have the units set up as primarily OSX I have the Yaboot partition after the OSX partition . . . but obviously it makes it vulnerable, and had I found your link here might have made it easier . . . .  But, to your point about GParted, yes I believe you could set up the disk from the linux installer . . . and might be able to set the OSX partition as empty, install linux w/Yaboot in front of the OSX, and then afterward, drop the OSX in as a clone?  But I think if you would use the OSX installer it might wipe stuff out???  I've only done it the way I've said, but I've done it a number of times . . . .

e.e.p.

---

### Post by robert94 on 2014-05-09
rsavage and e.e.p

Good to see some discussion ! - when I run gparted from lubuntu 14.04 live dvd it shows my OS 10.3.9 80GB drive as UFS, the gparted feature sheet [here]("http://gparted.org/features.php") shows that UFS cannot be resized :(

The best option is for me to find/acquire MAC OS 10.5.x install media so I can upgrade to 10.5.8 and in addition get the ability to resize the existing partition to allow room for Lubuntu. There are some 3rd party apps such as [Stellar]("http://www.stellarinfo.com/mac-software/partition-mac/partition-mac-drive.php") that allow one to resize 10.3.9 disks but they cost money ! but I'll keep looking for a free one

Note I know of at least one other Apple user who has gone with Lubuntu 12.04 PPC due to the issues he was getting with 14.04, I may yet do the same - my personal preference is xubuntu which I use now on Intel but it doesn't appear to have a PPC image

---

### Post by rsavage on 2014-05-10
> **este.el.paz said:**
> 
. . . I was going to say, yeah, I did that Startup Disk gaffe recently . . . and I think I just did a total fresh install to get around it.

Doh!  You should of said as the instructions have been in the FAQ for ages.

@robert

If you are up for a challenge - and I am in no way putting this forward as a straightforward solution - you could always install onto a virtual disk like wubi does.  The problem being, nobody has done this before on PowerPC as far as I can tell.  You would have to use Grub2, which is no bad thing.  I could get you so far at the moment, the persistent USB instructions in the FAQ would be a good place to start....

---

### Post by robert94 on 2014-05-10
> **rsavage said:**
> Doh!  You should of said as the instructions have been in the FAQ for ages.

@robert

If you are up for a challenge - and I am in no way putting this forward as a straightforward solution - you could always install onto a virtual disk like wubi does.  The problem being, nobody has done this before on PowerPC as far as I can tell.  You would have to use Grub2, which is no bad thing.  I could get you so far at the moment, the persistent USB instructions in the FAQ would be a good place to start....

What do you mean virtual disk, you mean do something like Wubi does for Windows [which I have used], I wasn't aware of any Wubi like alternatives for MAC OS

BTW I gave up on trying to get the Powerbook G4 to boot from its USB ports [after creating a MAC formated live usb for Lubuntu 14.04] , its almost mission impossible [to get the G4 to boot from usb] I couldn't get the yaboot parameters right - there are some very very complication pages describing the process...

---

### Post by rsavage on 2014-05-10
> **robert94 said:**
> What do you mean virtual disk, you mean do something like Wubi does for Windows [which I have used], I wasn't aware of any Wubi like alternatives for MAC OS
There isn't (yet) a 'Mubi'.  That was why I said it wouldn't be straighforward!  It is not impossible to work out what wubi does and recreate it.  There used to be a 'lubi' (a linux version of wubi), but sadly that hasn't been updated for ages.  I'm looking into it, but I have real life stuff to be getting on with!
> 
BTW I gave up on trying to get the Powerbook G4 to boot from its USB ports [after creating a MAC formated live usb for Lubuntu 14.04] , its almost mission impossible [to get the G4 to boot from usb] I couldn't get the yaboot parameters right - there are some very very complication pages describing the process...
Well if you mean the FAQ ones, then that is my doing!  Careful what you say as I am very proud of that document!  The problem is that not all usb drives can be seen in openfirmware and people can waste a lot of time before they figure this out.

---

### Post by este.el.paz on 2014-05-10
> **robert94 said:**
> rsavage and e.e.p

Good to see some discussion ! - when I run gparted from lubuntu 14.04 live dvd it shows my OS 10.3.9 80GB drive as UFS, the gparted feature sheet [here]("http://gparted.org/features.php") shows that UFS cannot be resized :(
The best option is for me to find/acquire MAC OS 10.5.x install media so I can upgrade to 10.5.8 and in addition get the ability to resize the existing partition to allow room for Lubuntu. 

> **rsavage said:**
> Doh!  You should of said as the instructions have been in the FAQ for ages.

@rsavage:

It was worse than "Doh!" . . . but, I was trying to get to the OS 9.2.2 system on my originally dual boot iMac . . . basically to try to compare 9.2 to linux and see how far different they are . . . but, even with Startup Disk the computer couldn't make it to 9 . . . so I went back to 10 . . . 10 is fine . . . and 10.4.11 is fine for my needs, except for the browser updating or lack thereof . . . got the TFF, but no flash there either . . .

OK, back to robert:  If you haven't found another way, just plain old OSX Disk Utility can be used to partition the disk . . . either, as I mentioned, booted in a FW clone, or booted in an install Disk . . . use DU to wipe the drive and partition it into the zone where you will put OSX, whether or not you set up Yaboot in front of OSX, in which case you would need to use DU to do that . . . or, just cut it into two zones, one for OSX, one set for windows/linux . . . .

e.e.p.

---

### Post by rsavage on 2014-05-10
> **rsavage said:**
> 
If you are up for a challenge - and I am in no way putting this forward as a straightforward solution - you could always install onto a virtual disk like wubi does.  The problem being, nobody has done this before on PowerPC as far as I can tell. 

Correction - I've done it!  Spent most of eurovision and a bit more getting it to work.  Don't get your hopes up too much, at the moment it is just a set of 'complicated' instructions....and I don't know if it will work with hfs/hfs+/ufs yet (I think a bit more tweaking will be necessary).  I probably won't have time to work on it for quite a few days now.

---

### Post by robert94 on 2014-05-10
> **este.el.paz said:**
> @rsavage:

OK, back to robert: If you haven't found another way, just plain old OSX Disk Utility can be used to partition the disk . . . either, as I mentioned, booted in a FW clone, or booted in an install Disk . . . use DU to wipe the drive and partition it into the zone where you will put OSX, whether or not you set up Yaboot in front of OSX, in which case you would need to use DU to do that . . . or, just cut it into two zones, one for OSX, one set for windows/linux . . . .e.e.p.


The GUI disk utility in Panther [10.3.9] does not allow one to resize an existing [UFS] partition. Are you suggesting some Apple command line utility can ?
note even the Apple documentation states when going from 10.3.9 to 10.5.x one must reformat the existing partition and effectively restore [I wonder if I can use Clonezilla to back it up ?!]

> **rsavage said:**
> Correction - I've done it!  Spent most of eurovision and a bit more getting it to work.  Don't get your hopes up too much, at the moment it is just a set of 'complicated' instructions....and I don't know if it will work with hfs/hfs+/ufs yet (I think a bit more tweaking will be necessary).  I probably won't have time to work on it for quite a few days now.

Well done ! Now I'm happy to give it a go as long as what you propose does not mean me having to risk loosing the existing UFS partition [boot or data as it is not my PC ! and I don't have a backup of it [yet] note I assume what you propose means running Lubuntu on a virtual partition is similar to where with Wubi I have Xubuntu 12.04 running on a Windows PC that has NTFS. I ask as I found that Xubuntu 12.04 on a virtual partition on NTFS is really disk intensive i.e. slow at least compared to when I had it running from dual boot on a native Ext2 partition ?

---

### Post by rsavage on 2014-05-14
> **robert94 said:**
> 
Well done ! Now I'm happy to give it a go as long as what you propose does not mean me having to risk loosing the existing UFS partition [boot or data as it is not my PC ! and I don't have a backup of it [yet] note I assume what you propose means running Lubuntu on a virtual partition is similar to where with Wubi I have Xubuntu 12.04 running on a Windows PC that has NTFS. I ask as I found that Xubuntu 12.04 on a virtual partition on NTFS is really disk intensive i.e. slow at least compared to when I had it running from dual boot on a native Ext2 partition ?

Yes it is exactly like wubi (or as close to it as I can get it).  I think the speed is partly determined by how fragmented your drive is.  

I may get some time to write about it tonight.  I'm trying to figure out the easiest way to set it up.  Installing the system to virtual disks is actually quite easy, it is the bootloader that has caused the most trouble....

---

### Post by robert94 on 2014-05-18
Well I finally managed to get Leopard installed on the G4 [& from usb] and have resized to create a second 20GB partition. I am now in a position to install Lubuntu into that partition. I presume yaboot is what is used when I do this or is created when I do that install ?

I have left the MAC OS Partition at 60Gb [total 80GB] to allow for your procedure too

NB: I haven't decided what version of Lubuntu I'll install, I am still tempted to do 14.04 rather than 12.04 still despite all the issues with it...

---

### Post by rsavage on 2014-05-18
See [http://ubuntuforums.org/showthread.php?t=2224808](http://ubuntuforums.org/showthread.php?t=2224808)

---

### Post by John_Fuller on 2014-05-19
> **este.el.paz said:**
> @Gulmer:

You aren't saying what version you are trying to install . . . assuming it is 14.04???  Probably easier to go to 12.04, everything should work better there; I think I recall seeing some issues with network manager?? in 14.04 Lubuntu on the Lu users list serve???  Haven't yet had time to try an install on my iBook . . . .

But, if you have 14.04 and want to keep it, you ***probably*** will need the "b43-legacy" driver, not just the "b43" . . . that might make a difference . . . and with the "white screen" you might have to try out some boot params or set up the proper xorg.conf file if you are already installed . . . that I really can't help you with, but there are links to sites that have pre-made xorg,conf files . . . usually it's about selecting the proper video driver for your display . . . possibly "nvidia" or "radeon" . . . can be a little bit of a pain to get the screen working, after that should be OK, except I guess for sound doesn't seem to be working out of the box in 14.04 . . . hence the suggestion for 12.04 . . . in Lubun or Xubun or whichever . . . .

e.e.p.

Hello - s'cuse me for barging in here - but I have to start somewhere!
I'm new to all this. Decided my old PPC G4 would be more useful running on ubuntu [and using a partition so I can still use photoshop and illustrator].

I was following some old instructions I found. I burned the iso successfully onto a disc [ubuntu-12.04-desktop-powerpc]. And booted with 'c' key [whilst connected to the ethernet with cable]. Lots of encouraging whirring and whooshing noises, after I presses 'return' . A couple of times some text appeared for a short time [I photographed them].
Then everything stopped - went quiet for ages.... till I presses the power button, and it started up in Mac mode = it didn't work!

The screen messages were:   
Ubuntu 12.04 ... sand disabled:edit /etc/defaultsanedemo5) - FMU version: 17  [ok]
* Starting restore sound card(s') mixer state(s)
speech-dispatcher disabled: edit /etc/default/speech-dispatcher    [*"something blurred in red"*]

Ubuntu 12.04
...*stopping cold plug devices device security - FMU version: 17  [OK]
*stopping log initial device cresting state(s)     [OK]
*stopping System V runlevel compatibility/speech-dispatcher    [OK]
*starting enable remaining boot-time encrypted block devices [OK]
*starting configure network device security  [OK]
*starting configure virtual network devices  [OK]
*stopping configure  virtual network devices  [OK]
*starting save udev log and update rules   [OK]
*stopping save udev log and update rules   [OK]

Thank you for your patience if I'm on the wrong part of the forum.
John

---

### Post by rsavage on 2014-05-19
Hi John,

You might be better off starting a new thread since this one has been marked as solved (although it has already been hijacked by somebody else!).  Your problem is probably graphic card related (nothing to do with the lines of text you gave) so some more info on that would be good.  Have a look at the troubleshooting section [https://wiki.ubuntu.com/PowerPCFAQ#Ubuntu_boots_to_a_command_line.2C_hangs_during_boot.2C_or_blank_screen_etc](https://wiki.ubuntu.com/PowerPCFAQ#Ubuntu_boots_to_a_command_line.2C_hangs_during_boot.2C_or_blank_screen_etc). you might be able to solve the problem yourself.  Literally every 12.04 problem for PowerPC that has appeared on this forum has been documented in the FAQ and Known Issues pages.

---

### Post by este.el.paz on 2014-05-19
> **John_Fuller said:**
> Hello - s'cuse me for barging in here - but I have to start somewhere!
I'm new to all this. Decided my old PPC G4 would be more useful running on ubuntu [and using a partition so I can still use photoshop and illustrator].

s, after I presses 'return' . A couple of times some text appeared for a short time [I photographed them].
Then everything stopped - went quiet for ages.... till I presses the power button, and it started up in Mac mode = it didn't work!

John

@John:

It's good that rsavage has stepped in and provided that PPC FAQ link, indeed the answer will probably be there . . . it might help to know exactly which PPC G4 you are using, and as he mentioned, which graphics card it is using . . . .  But, a couple of other points . . . you said, "after pressing return" . . . but did you type anything in after the "boot" 1st Yaboot window?  Usually it should be at least "live" . . . and then depending on your machine it might be helpful to add some other stuff, and then you hit return . . . if you hit "tab" key at that window it should show you some other "boot parameter" options to try out . . . .  And, secondly, did you check the md5sum number for your .iso? . . . that didn't seem to be so critical in 12.04, but it seems to be more important these days to getting a good system install . . . .  Enjoy the process . . . .

e.e.p.

---

### Post by John_Fuller on 2014-05-20
Thank you rsavage for your quick response! I'll look into that link.

rep -  
1.67 GHz ppc g4  17"
1 GB RAM
POWERBOOK 5,9
And this is what I could find under 'graphics':
[FONT=Lucida Grande]**ATI Mobility Radeon 9700:**[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Lucida Grande]  Chipset Model:	ATY,RV360M11[/FONT]
[FONT=Lucida Grande]  Type:	Display[/FONT]
[FONT=Lucida Grande]  Bus:	AGP[/FONT]
[FONT=Lucida Grande]  VRAM (Total):	128 MB[/FONT]
[FONT=Lucida Grande]  Vendor:	ATI (0x1002)[/FONT]
[FONT=Lucida Grande]  Device ID:	0x4e50[/FONT]
[FONT=Lucida Grande]  Revision ID:	0x0000[/FONT]
[FONT=Lucida Grande]  ROM Revision:	113-xxxxx-169[/FONT]
[FONT=Lucida Grande]  Displays:[/FONT]
[FONT=Lucida Grande]**Color LCD:**[/FONT]
[FONT=Lucida Grande]  Display Type:	LCD[/FONT]
[FONT=Lucida Grande]  Resolution:	1440 x 900 @ 60 Hz[/FONT]
[FONT=Lucida Grande]  Depth:	32-bit Color[/FONT]
[FONT=Lucida Grande]  Built-In:	Yes[/FONT]
[FONT=Lucida Grande]  Core Image:	Supported[/FONT]
[FONT=Lucida Grande]  Main Display:	Yes[/FONT]
[FONT=Lucida Grande]  Mirror:	Off[/FONT]
[FONT=Lucida Grande]  Online:	Yes[/FONT]
[FONT=Lucida Grande]  Quartz Extreme:	Supported

[/FONT]
Re:"....[COLOR=#000000]did you type anything in after the "boot" 1st Yaboot window?" No! I wouldn't know what to type.... :)
I think I just pressed 'return'. Earlier I typed 'help', but don't think that led to much.  So, you suggest I type: "live" after the word 'boot'?

"..[/COLOR][COLOR=#000000]did you check the md5sum number for your .iso?"   - sorry, don't know what that is. Would that be displayed on th [/COLOR][COLOR=#000000]page from which I downloaded the iso? If so, I might not be able to find that easily.
[/COLOR]
Thank you [as you can seed I'm pretty green...]

---

### Post by este.el.paz on 2014-05-20
> **rsavage said:**
> Hi John,
You might be better off starting a new thread since this one has been marked as solved.   Your problem is probably graphic card related (nothing to do with the lines of text you gave) so some more info on that would be good.  Literally every 12.04 problem for PowerPC that has appeared on this forum has been documented in the FAQ and Known Issues pages.

> **John_Fuller said:**
> Thank you rsavage for your quick response! I'll look into that link.
[FONT=Lucida Grande]**ATI Mobility Radeon 9700:**[/FONT]
[FONT=Helvetica][/FONT][COLOR=#000000]  So, you suggest I type: "live" after the word 'boot'?
[/COLOR][COLOR=#000000]. Would that be displayed on th [/COLOR][COLOR=#000000]page from which I downloaded the iso? If so, I might not be able to find that easily.
[/COLOR]Thank you [as you can seed I'm pretty green...]

@John:  I'm just re-posting rsavages suggestion to start a fresh thread if you haven't figured out your solution.  Yes, I was suggesting that you type "live" after the word "boot" with the flashing prompt . . . .  But it seems from your previous post that you are getting to the "splash" window . . . the word "ubuntu" with the 4 dots flashing under it.  So, as rsavage suggests it could be the graphics card and you would have to add some stuff to your boot parameter, but in 12.04 on my radeon iBook I had no problem getting it to boot and run clean with just "live" . . . .

Which might bring it back to the md5sum number issue . . . yes, it is listed on the page where you downloaded your .iso file at the top of the list of files.  In OSX it is fairly easy to check, open Terminal type "md5" plus a space, then drag and drop the .iso file into the Terminal window and hit return.  That number it produces should match the one they list on the download page.

Don't be afraid to "Google" anything that gets mentioned, there is a lot to learn . . . .

[http://cdimage.ubuntu.com/releases/precise/release/](http://cdimage.ubuntu.com/releases/precise/release/)

e.e.p.

---

### Post by John_Fuller on 2014-05-21
Well - I had assumed [wrongly] that the word 'live' referred to the fact that the iso was up and ready!!   :)

Anyway, I had a go and it was loading up for some time [no text]. Eventually the computer went quiet [it turned off].

Then I tried live-nosplash-powerpc and got quite a lot of text while it was booting. But it stopped after a while [whe it got to 'stopping save udev log & update rules'. It shut down.
Same happened with the live-powerpc option.

Re: "..[COLOR=#000000] in 12.04 on my radeon iBook I had no problem getting it to boot and run clean with just "live" . . . ." 
I guess I need to open a new thread and go down the route of adding some specific command to the boot. [/COLOR]

---

### Post by este.el.paz on 2014-05-21
@John:

Did you check the md5sum yet?  If not, please do that; if the number doesn't match up then download a fresh .iso until the number matches . . . then burn to CD/DVD . . . then re-try your various boot commands until you get passed the splash . . . .  Otherwise, I'll try to pay attention if you start a new thread . . . and at least I'll "view" it.  : - )

e.e.p.

---

### Post by John_Fuller on 2014-05-21
OK eep, I'll try to do that. I'll let you know if/when I succeed .. tho it might take a while 'cos I'll need to understand what I'm doing, and 'll ned some time.

Thank you so much for your help and attention.
John [near Manchester, UK]

---

### Post by John_Fuller on 2014-05-22
I was using the desktop iso [duh...].
Sorry to have wasted your time - but I'm learning!

I'm going to post a new thread on the forum about the fact that the arrow keys stopped working when I got to the partition page. It could be that the iso [or boot type??] won't allow a partition...
J

---

