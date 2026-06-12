---
title: "iPhone no longer mounting after iOS 4.2 upgrade"
date: 2010-11-22
forum: Any Other OS
---

### Post by Caldur06 on 2010-11-22
iOS 4.2.1 was released today. I upgraded through iTunes on a Windows machine. I had a problem that [a lot of people are having]("http://techcrunch.com/2010/11/22/ios-42-bug/") though, where all of my songs are missing. So, the workaround that other people are using involves the iTunes that you normally sync your music with. Obviously I sync my music with my ubuntu, so that doesn't work.

I came home tonight and my computer isn't even recognizing my iPhone when I plug it in. So now I've got an iPhone with no music and an OS that's oblivious to it. >_<

---

### Post by holiday on 2010-11-22
> **Caldur06 said:**
> iOS 4.2.1 was released today. I upgraded through iTunes on a Windows machine. I had a problem that [a lot of people are having]("http://techcrunch.com/2010/11/22/ios-42-bug/") though, where all of my songs are missing. So, the workaround that other people are using involves the iTunes that you normally sync your music with. Obviously I sync my music with my ubuntu, so that doesn't work.

I came home tonight and my computer isn't even recognizing my iPhone when I plug it in. So now I've got an iPhone with no music and an OS that's oblivious to it. >_<

I've heard you can rollback your iPhone "upgrades" through iTunes. Is there anything you need 4.2.1 for? I wonder if locking out non-iTunes interfaces is one of 4.2.1 "improvements".

---

### Post by topheth on 2010-11-22
Same issue here as well.  Upgraded iPhone to iOS 4.2 on my 3G and had to 'resync' to see my music on the phone.  However, since then the phone will not connect through Rhythmbox.  :(

---

### Post by aleolivat on 2010-11-23
I am having the same problem after updating to  iOS  4.2.    I can not mount the iphone so I cannot copy the pictures to the computer.

---

### Post by dannyadornato on 2010-11-23
Same problem with me.

---

### Post by gb@ssan on 2010-11-23
Yeah. Same here. :o
Ubuntu 10.10 with iOS 4.2.1.

---

### Post by Deersindal on 2010-11-25
same problem here. ubuntu 11.04 and ios 4.2.1 on an ipod touch 2g (jailbroken)

---

### Post by elvisrv on 2010-11-25
Same here on an iPod Touch 2G (iOS 4.2.1) on Ubuntu Lucid Lynx 10.04.1

---

### Post by atomatt on 2010-11-25
It's a known bug. See [http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421](http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421) for details.

---

### Post by kanazky on 2010-11-25
Nor can I on Linux Mint 10 :( And My iPhone doesn't have any music on it haha so its even worse.

---

### Post by adanesin on 2010-11-26
Same here. The solution might be to reinstall libraries compiled with openssl. I hope they will come up with a easier solution...

---

### Post by z06steve on 2010-11-26
So I guess I have to wait :(

---

### Post by ThatBum on 2010-11-27
Yep, mine won't mount. It is a jailbroken 3G with 4.2.1.

It gives me an error, it says "Unable to mount iPhone - DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

So it's DBus related...

Also, I checked out [libimobiledevice's place]("http://www.libimobiledevice.org/"), they SAY they have support for 4.2.1 devices with their 1.0.3 release, but I used their PPA to get that version and it did nothing. However, the Maverick repo version of libimobiledevice is 1.0.1, so that may be something.

---

### Post by ThePengwin on 2010-11-27
> **ThatBum said:**
> Yep, mine won't mount. It is a jailbroken 3G with 4.2.1.

It gives me an error, it says "Unable to mount iPhone - DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

So it's DBus related...

Also, I checked out [libimobiledevice's place]("http://www.libimobiledevice.org/"), they SAY they have support for 4.2.1 devices with their 1.0.3 release, but I used their PPA to get that version and it did nothing. However, the Maverick repo version of libimobiledevice is 1.0.1, so that may be something.

It looks like the support is actually in 1.0.4, as per that site, and the PPA version is still 1.0.3, So i guess we will all have to wait for the PPA maintainer to recompile the new version, or compile it manually.

---

### Post by ThatBum on 2010-11-28
Oh whoops, sorry, it seems I've forgotten how to read. I would compile it, but I'm away from my machine with all the dev stuff on it, so I'll do it later. Might make a deb or something and put it up here if no one beats me to it.

[COLOR=Red]E: YAAAAY! I found a pre-compiled 1.0.4 for SuSE whilst Googling around. I extracted the RPM, and all that was in it was a lib and a symlink to the lib. I moved them both to /usr/lib/, renamed my old libimobiledevice with a .old extension, and slip-bam-jam it works. Attached it what I used.

[COLOR=Black]Edit: This is moot now. 1.0.4 is now in the repos.[/COLOR]
[/COLOR]

---

### Post by ThePengwin on 2010-11-28
> **ThatBum said:**
> Oh whoops, sorry, it seems I've forgotten how to read. I would compile it, but I'm away from my machine with all the dev stuff on it, so I'll do it later. Might make a deb or something and put it up here if no one beats me to it.

E: YAAAAY! I found a pre-compiled 1.0.4 for SuSE whilst Googling around. I extracted the RPM, and all that was in it was a lib and a symlink to the lib. I moved them both to /usr/lib/, renamed my old libimobiledevice with a .old extension, and slip-bam-jam it works. Attached it what I used.

Thanks a lot. This worked perfectly for me too!

---

### Post by Bigadada_saba on 2010-11-28
> **ThePengwin said:**
> Thanks a lot. This worked perfectly for me too!

can you explain that in newbe terms so we can get it done also.

---

### Post by ThatBum on 2010-11-28
[COLOR=Red]Well, do you know how to move files around with the terminal? Extract the zip up there and change the directory to the extracted archive's folder in terminal (cd ~/Downloads/libimobiledevice-1.0.4/, presumably). Then move both files to /usr/lib as root (sudo mv * /usr/lib/), and rename the old lib so it's not unintentionally used, also as root (sudo mv /usr/lib/libimobiledevice.so.1.0.3 /usr/lib/libimobiledevice.so.1.0.3.old), and that's it, no reboot or anything.

[COLOR=Black]Edit: This is now moot. 1.0.4 is now in the repos.[/COLOR]
[/COLOR]

---

### Post by brianC on 2010-11-28
ThatBum is a good Bum  Worked.......Yeah Baby!

---

### Post by Decatf on 2010-11-28
The ppa was updated today.
[https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

---

### Post by dtaylorl on 2010-11-29
I just installed libimobiledevice 1.0.4 from the linked ppa and I am still having the same issue (DBus error).  Is there anything else that needs to be done to make it work?

---

### Post by manuw2009 on 2010-11-30
> **dtaylorl said:**
> I just installed libimobiledevice 1.0.4 from the linked ppa and I am still having the same issue (DBus error).  Is there anything else that needs to be done to make it work?

I upgraded to ios 4.2.1 & updated libimobiledevice yesterday on my maverick install.
And it works fine :p
1. Have you updated usbmuxd & ifuse as well ?
2. Do you have any locally compiled libimobiledevice ? maybe you should do a "purge" remove + reinstall
3. Is your device a 4G one or an older one with the upgraded iOS ?
I read that music transfer only works for pre 4G devices (and it did work at my end).
maybe they have mount issues too

---

### Post by aleolivat on 2010-11-30
The PPA solution works for me.   Thank you very much.

---

### Post by DodgeV83 on 2010-11-30
The PPA by itself didn't work for me.  I then had to run:
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

Got the answer from the following Bug Reports

[http://libiphone.lighthouseapp.com/projects/27916/tickets/183-cannon-mount-iphone-with-ios-421-in-ubuntu-1010#ticket-183-13](http://libiphone.lighthouseapp.com/projects/27916/tickets/183-cannon-mount-iphone-with-ios-421-in-ubuntu-1010#ticket-183-13)

[http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10](http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10)

---

### Post by earthmeLon on 2010-12-01
> **Decatf said:**
> The ppa was updated today.
[https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

Append the following to the end of /etc/apt/source.list:
```

#libimobile
deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) maverick

```

Then do:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D48B8E25
sudo apt-get update && sudo apt-get upgrade

```

Worked for Ubuntu 10.10 (x64) on iPad 4.2

---

### Post by StuPigeon on 2010-12-01
After getting it to mount i opened rhythm box and synced some music the iphone DOES NOT detect any of it? any fixes?
Or new threads for that?

---

### Post by ThePengwin on 2010-12-02
> **StuPigeon said:**
> After getting it to mount i opened rhythm box and synced some music the iphone DOES NOT detect any of it? any fixes?
Or new threads for that?


the libimobiledevice site says that the iPad and iPhone on 4.2.1 are currently unable to sync the music database. They are working on it though.

---

### Post by StuPigeon on 2010-12-03
Thanks i decided running a VM would be a lot easier.

---

### Post by dyintrovert2 on 2010-12-04
> **StuPigeon said:**
> Thanks i decided running a VM would be a lot easier.

I'm doing the same.  VirtualBox with XP installed (copied music via network connection).  By no means ideal but it does work.

Also tried a Natty VirtualBox, using the latest test ISO.  Got some odd errors (including a segfault once) when I tried to open Rhythmbox with the iTouch plugged in.

For now at least the XP install seems to work best.

---

### Post by duff_bluff on 2010-12-05
Any updates on this?  I can't seem to update libimoviledevice past version 1.0.1

---

### Post by migmruiz on 2010-12-06
If you experienced this, please go to [https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/685752](https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/685752) and mark that this Bug affects you.

---

### Post by migmruiz on 2010-12-06
I had to run that too
> **DodgeV83 said:**
> The PPA by itself didn't work for me.  I then had to run:
```

idevicepair unpair
idevicepair pair
idevicepair validate
```Got the answer from the following Bug Reports

[http://libiphone.lighthouseapp.com/projects/27916/tickets/183-cannon-mount-iphone-with-ios-421-in-ubuntu-1010#ticket-183-13](http://libiphone.lighthouseapp.com/projects/27916/tickets/183-cannon-mount-iphone-with-ios-421-in-ubuntu-1010#ticket-183-13)

[http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10](http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10)

just remembering: to do that you need to have libimobiledevice-utils installed, if you don't have it
```

sudo apt-get install libimobiledevice-utils

```

---

### Post by impresionist on 2010-12-06
> **migmruiz said:**
> 

just remembering: to do that you need to have libimobiledevice-utils installed, if you don't have it
```

sudo apt-get install libimobiledevice-utils

```

Hello,
In Lucid after installing the libimobiledevice-utils no any change, the OS can't mount the Iphone 3GS after upgrading to 4.2.1... and with
lsusb -- > it's found as Bus 001 Device 013: ID 05ac:1294 Apple, Inc. iPhone 3GS ... but no way to mount it...

And in Ubuntu 10.10 I get:
> 
error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)



Like always, it's only problems with Iphone, each two months for each upgrade...

---

### Post by eddieray7 on 2010-12-06
I manually installed the PPA packages mentioned earlier (libimobiledevice and libimobiledevice-utils) v1.0.4 on Maverick, disconnected the phone (3GS), reconnected it and it worked first try.

---

### Post by migmruiz on 2010-12-06
> **impresionist said:**
> Hello,
... after installing the libimobiledevice-utils no any change, the OS can't mount the Iphone 3GS after upgrading to 4.2.1... 

Have you installed the ppa version?

If you did so, have you tried to run

```

idevicepair unpair
idevicepair pair
idevicepair validate 
```

??

well.. again, that worked for me

---

### Post by migmruiz on 2010-12-06
Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```
and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

---

### Post by ThatBum on 2010-12-07
libimobiledevice-utils is cool. You can see realtime dmesg output of the iDevice with idevicesyslog, see all sorts of config parameters and things with ideviceinfo, and even backup and restore the whole iDevice with idevicebackup. Neat stuff.

I tried some operations with my iPhone 3G. Everything works, I can mount it, read music from it, and sync music to it. I didn't have to unpair and pair, I just had to install libimobiledevice 1.0.4. Maybe my machine is magical or something...

---

### Post by Random8 on 2010-12-07
How likely is it that this will not be resolved in future updates?

Should we all go with the VM Solution?

---

### Post by Random8 on 2010-12-07
And I love for for this post. Why could none of all the other forms I've read put it so clearly?

---

### Post by dorjem on 2010-12-09
migmruiz (and everyone else on this thread) many thanks for sharing your time and expertise.

Had same problem here
Ubuntu 10.04 / iPhone 3GS running iOS 4.2.1 
and suddenly couldn't connect to the phone at all

did the applications / accessories / terminal
lsusb 
and could see the Apple device connected

But it never showed up on the desktop (didn't mount in other words)

I used applications / Ubuntu software centre
to install iFuse

but pluging in my iPhone still didn't show on the desktop

In the terminal window I did the following to get the libimobile files installed (this took a while, to get the syntax etc right. You'll need to enter the password for a user with ROOT access)

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get upgrade

but there was a message that some packages had been kept back 

So I read
[http://ubuntuforums.org/showthread.php?t=228788 ]("http://ubuntuforums.org/showthread.php?t=228788")

Which told me I should try 

sudo aptitude dist-upgrade 
This updated the packages which had been kept back (some of which were GVFS related)

Anyway the really useful page I got to was 

[http://www.taranfx.com/sync-iphone-linux](http://www.taranfx.com/sync-iphone-linux)

I did steps 1 2 3 4 then rebooted as it instructs in 5
I forgot to unplug my iPhone
And hey presto when I logged in here was my iPhone on the desktop asking me what I wanted to do open Fspot (images) open Rythmbox (music) blah blah

So I'm thrilled and hope others find this useful too. And it only took 2 and a half hours :-)

Many thanks to all of you here, cannonical and everyone for the [ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29") you show by sharing

---

### Post by gb@ssan on 2010-12-09
Hey guys!

My iPhone is mounting once again, since I've updated the libimobiledevice to the version 1.0.4!!!

But I notice a strange behavior: 

Before the libimobiledevice update, I was able to see the iPhone charging status in the power management icon in the notification area, with my laptop charging status. 

But now, I can't see the iphone status and in addition, the Power Management is unable to notice if my notebook is under A/C power or battery as long the iPhone is plugged in.

Can anyone help me ?

Thanks in advance!

---

### Post by tc7 on 2010-12-09
Worked perfectly for me first time.

phone: iPhone 3GS with 4.2.1
laptop: Maverick 64: 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

I appended the two lines to /etc/apt/sources.list
then used synaptic to update/upgrade / install libimobiledevice-utils.
Unplugged and plugged in usb cable - bingo!

Just dragged and dropped 100 tracks onto my iPhone using Rhythmbox.

Great post - good job :popcorn:.
thanks.

---

### Post by jeff.scott on 2010-12-10
> **tc7 said:**
> Worked perfectly for me first time.

phone: iPhone 3GS with 4.2.1
laptop: Maverick 64: 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

I appended the two lines to /etc/apt/sources.list
then used synaptic to update/upgrade / install libimobiledevice-utils.
Unplugged and plugged in usb cable - bingo!

Just dragged and dropped 100 tracks onto my iPhone using Rhythmbox.

Great post - good job :popcorn:.
thanks.


I have almost same configuration
phone: iphone 3GS with IOS 4.2.1
desktop: Ubuntu 10.04 64bit Desktop

After following multiple threads, I can mount the iphone and fspot was able to see the photos...but nothing else works.  Does not show on desktop and Rhythmbox does not see phone.

Suggestions?

---

### Post by migmruiz on 2010-12-11
> **gb@ssan said:**
> Hey guys!

My iPhone is mounting once again, since I've updated the libimobiledevice to the version 1.0.4!!!

But I notice a strange behavior:

Before the libimobiledevice update, I was able to see the iPhone charging status in the power management icon in the notification area, with my laptop charging status.

But now, I can't see the iphone status and in addition, the Power Management is unable to notice if my notebook is under A/C power or battery as long the iPhone is plugged in.

Can anyone help me ?

Thanks in advance!

perhaps if the  A/C cable in connected u are under  A/C power, otherwise u are under battery. :)

now, seriously, I really think we are going to live with that until natty
or, at last, 'til next year
[https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/682331](https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/682331)

if you wanna help, I think a Stable Realease Update or a Backport is needed and follow the SRU or the Backport process might be helpful
[https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/682331/comments/5](https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/682331/comments/5)

> **jeff.scott said:**
> I have almost same configuration
phone: iphone 3GS with IOS 4.2.1
desktop: Ubuntu 10.04 64bit Desktop

After following multiple threads, I can mount the iphone and fspot was able to see the photos...but nothing else works.  Does not show on desktop and Rhythmbox does not see phone.

Suggestions?

as ThePengwin already said

> **ThePengwin said:**
> the libimobiledevice site says that the iPad  and iPhone on 4.2.1 are currently unable to sync the music database.  They are working on it though.

---

### Post by MrGreen on 2010-12-12
Tried all of the above still getting error message from dbus

Running ilibmobiledevice 1.0.4 Ubuntu 10.10 

Tried idevicepair unpair

Still nothing

MrG

---

### Post by MrGreen on 2010-12-12
Make sure /usr/local/lib/ does not have any libimobile stuff in it

I removed those file and my phone is now mounting again

[http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10](http://libiphone.lighthouseapp.com/projects/27916/tickets/181-cant-mount-iphone-in-ios-421#ticket-181-10)



YMMV

MrG

---

### Post by mrmadowl on 2010-12-21
> **migmruiz said:**
> Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```
and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

This worked for me, Thanks m8  :KS

---

### Post by thoughts on 2010-12-24
> **migmruiz said:**
> Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```
and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

This worked for me too, on my non-jailbroken iPhone 4.

I have a question though: I did need to install the libimobiledevice-utils package (and then run the 3 idevicepair commands).  But in the past, I've never had to do anything special to get my iPhone to work with Ubuntu; I just plugged it in, and then I could always go to the computer:/// location in Nautilus and browse the iPhone's contents (photos is mainly what I need to access this way).  So does this mean that, going forward, the libimobiledevice-utils package is always required for iPhone support?  And will it then eventually be included in Ubuntu automatically?  I'm just trying to determine whether I need to keep a note of this, and trying to avoid having any extra packages installed that aren't strictly necessary.

Thanks,

--
Anthony DiSante
[http://encodable.com/](http://encodable.com/)
[http://nodivisions.com/](http://nodivisions.com/)

---

### Post by snail stoves on 2010-12-24
> **dorjem said:**
> migmruiz (and everyone else on this thread) many thanks for sharing your time and expertise.

Had same problem here
Ubuntu 10.04 / iPhone 3GS running iOS 4.2.1 
and suddenly couldn't connect to the phone at all

did the applications / accessories / terminal
lsusb 
and could see the Apple device connected

But it never showed up on the desktop (didn't mount in other words)

I used applications / Ubuntu software centre
to install iFuse

but pluging in my iPhone still didn't show on the desktop

In the terminal window I did the following to get the libimobile files installed (this took a while, to get the syntax etc right. You'll need to enter the password for a user with ROOT access)

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get upgrade

but there was a message that some packages had been kept back 

So I read
[http://ubuntuforums.org/showthread.php?t=228788 ]("http://ubuntuforums.org/showthread.php?t=228788")

Which told me I should try 

sudo aptitude dist-upgrade 
This updated the packages which had been kept back (some of which were GVFS related)

Anyway the really useful page I got to was 

[http://www.taranfx.com/sync-iphone-linux](http://www.taranfx.com/sync-iphone-linux)

I did steps 1 2 3 4 then rebooted as it instructs in 5
I forgot to unplug my iPhone
And hey presto when I logged in here was my iPhone on the desktop asking me what I wanted to do open Fspot (images) open Rythmbox (music) blah blah

So I'm thrilled and hope others find this useful too. And it only took 2 and a half hours :-)

Many thanks to all of you here, cannonical and everyone for the [ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29") you show by sharing


**************************************************************
iphone 3g - jailbroken - unlocked - 4.2os - ubuntu 10.04
So, this worked for me, Thank you SO much for the S-B-Step guide. 
Brilliant
Perfect
Sharing is Caring
All the best
Smiffy
**************************************************************

---

### Post by fslezak on 2010-12-25
Ok.. I tried the above solutions, and no success with my iPod touch. Info below:

iPod Touch 4
iOS 4.2.1 ( 8C148 )

Ubuntu 10.04 desktop (32 bit)
Linux 2.6.32-24-generic

Please Help!

---

### Post by bapoumba on 2010-12-28
Worked here, thanks much !
iPod touch 4.2.1 (8C148 ), Maverick up to date with pmcenery ppa.

---

### Post by brettansley on 2010-12-28
I started getting the 
Unable to Mount Brett's iPod
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
error.

Following the stuff in this thread I can now successfully mount my iPod G4 on 10.10 Linux 2.6.35-24-generic

But I still cannot get RhythmBox to recognise the device - I can see in PCMan but not in Rhythmbox.

Any other ideas?

Thanks

---

### Post by bapoumba on 2010-12-28
Have you installed libimobiledevice-utils ?

I had to restart my laptop for other reasons, and did not try to mount the iPod before the reboot. Shows up okay in Rhythmbox, able to move music to the iPod or from the iPod.

---

### Post by eurobeatboy on 2010-12-29
> **aleolivat said:**
> The PPA solution works for me.   Thank you very much.

Same here. 
Thank you!!!! :)

Rhythmbox played my MP3s off my iPhone4 flawlessly after adding this PPA to software sources. I just needed to re-enable the iPod plugin in Rhythmbox and, presto! "iPhone 4" appeared in the left-pane list

---

### Post by bin ai on 2010-12-29
> **ThatBum said:**
> [COLOR=Red]Well, do you know how to move files around with the terminal? Extract the zip up there and change the directory to the extracted archive's folder in terminal (cd ~/Downloads/libimobiledevice-1.0.4/, presumably). Then move both files to /usr/lib as root (sudo mv * /usr/lib/), and rename the old lib so it's not unintentionally used, also as root (sudo mv /usr/lib/libimobiledevice.so.1.0.3 /usr/lib/libimobiledevice.so.1.0.3.old), and that's it, no reboot or anything.

[COLOR=Black]Edit: This is now moot. 1.0.4 is now in the repos.[/COLOR]
[/COLOR]

Many thanks, it worked perfectly.

---

### Post by fattyz on 2010-12-29
I am too noob for that last post, i don't know how to move files around with the terminal and I am sort of lost now since I have been trying to get this to work so long with so many upgrades and version changes and stuff.

Right now I get the camera icon, and I can transfer photos from the iphone 3gs 4.2.1 to the computer ubuntu 10.04 but can not copy anything to the iphone.

As far as i know from all the threads everything is up to date?

idevice commands do not work in the terminal and I never got ipheth-utils pairing to work, I got fatal errors.

Will it work in windows if it's jailbroken?  I just tried my son's jailbroken phone on Ubuntu and got the same result. (nope, just tested it, same result, pics only and only one way.)

Thanks
Fattyz

I'd really like it to work in Ubuntu.  Help!

---

### Post by fattyz on 2010-12-29
Actually it works in winblows with phone disk.  The trial period expires in 8 days.  It's only 20 bucks.  If this is what I have to do, I'll do it.

FattyZ

---

### Post by fslezak on 2010-12-29
Tried everything to no avail. 

Also, the computer does not see iPod at all.

---

### Post by fattyz on 2010-12-29
I found a free app called discover that lets me transfer files between the computer and phone. (WiFi i guess)  Works in winblows but have not tried it ubuntu yet.  Sadly, I'm making more progress in winblows.

FattyZ

---

### Post by jyanek on 2010-12-29
> **migmruiz said:**
> Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```
and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```
Worked for me.  Thank you!
Ubuntu 10.10 x64 with iPhone 4 running 4.2.1

---

### Post by fattyz on 2010-12-30
Could be the Iphone 3gs 4.2.1 is the problem or the version of ubuntu?  I tried all these things in ubuntu 10.04 no luck.

Fattyz

---

### Post by slochewie on 2010-12-30
iPhone 4 with iOS 4.21. I just upgrade from 10.04 to 10.10 and still no luck seeing the iPhone in rhythmbox or gtkpod.

It seems to mount fine and I have an icon for it on my desktop and can open and browse it in nautilus.
ideviceinfo returns tons of info.

---

### Post by fattyz on 2010-12-31
Somehow everything started working in winblows.  I do not know how.  I think it may be because no. 1 son had to put on itunes to help him out of jail.  At any rate, I way prefer Ubuntu, but as long as I can make it work and do not have to return my phones.

Fattyz

---

### Post by spegru on 2011-01-01
I'm on Mint10 (Ubuntu 10.10 based)fresh install
iPhone 4 with iOS 4.2.1

When first plugged in nothing happened so I updated the repos with the pmcenery ppa, to get iphoneutils 1.0.4 just as many people here have.

The phone now mounts straight away and fspot and rhythmbox even offer to start. Rhythmbox can see into the phone too, and will also play music in there

However, when I push music into the phone using rhythmbox, it doesn't show up on the iphone and when I copy pictures from the phone to the PC, they don't  show up in f-spot

I have made sure to eject the phone in rhythmbox and I have also done the unpair, pair, validate thing - but it makes no difference

It's almost there but what is the missing link?

---

### Post by spegru on 2011-01-01
Oh by the way: 

The phone is not jailbroken

Also if i install libimobiledevice-utils, I get the following error: 
"error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"
However if libimobiledevice-utils is not installed there are no error messages

I get nice desktop icons and can borows inside the phone ok - it's just that rhythmbox music transfers do not show up on the phone

---

### Post by axel112 on 2011-01-02
> **jyanek said:**
> Worked for me.  Thank you!
Ubuntu 10.10 x64 with iPhone 4 running 4.2.1

> **fattyz said:**
> Could be the Iphone 3gs 4.2.1 is the problem or the version of ubuntu?  I tried all these things in ubuntu 10.04 no luck.

Fattyz

It works for me.
Iphone 3gs, ios 4.2.1
ubuntu 10.10 maverick.

Maybe upgrade to maverick?

---

### Post by spegru on 2011-01-02
I'm using mint 10 now which is based on maverick anyway. I guess there could be some difference though. Maybe I'll try a native 10.10 if all elase fails
The only other difference I can see is you have an Iphone3GS whereas this is an Iphone4. But I suppose that is mainly a hardware difference so I would be a bit surprised if it was relevant ...

What else have you installed and are you using Rhythmbox to do the transfers?

---

### Post by axel112 on 2011-01-03
> **spegru said:**
> I'm using mint 10 now which is based on maverick anyway. I guess there could be some difference though. Maybe I'll try a native 10.10 if all elase fails
The only other difference I can see is you have an Iphone3GS whereas this is an Iphone4. But I suppose that is mainly a hardware difference so I would be a bit surprised if it was relevant ...

What else have you installed and are you using Rhythmbox to do the transfers?

Nothing else installed that I think is relevant to communication between ubuntu and the iphone.

I'm using rhythmbox to transfer music and podcast by simply dragging them over. I can make playlists, but not add music or podcasts to them. If I use gtkpod, playlists work.

---

### Post by Add3r on 2011-01-04
Food evening all, 
I am trying to sync an iPhone 3gs, which I (stupidly) upgraded to iOS 4.2.1, with Ubuntu 10.04
I was able to sync music with Rhytmbox before the update, then my laptop wasn't even mounting it: I followed the instructions and installed libmobildevice 1.04, and now I can see the iPhone on my desktop, I can browse it, I can see it in Rhytmbox.
However, when I use Rhytmbox to transfer music, seems that it works, but on the iPhone itself I can't find any file!
Curiously, if I browse the iPhone with Nautilus, I can see the music files and even play them...
Is this a known bug?

Thanks!

---

### Post by spegru on 2011-01-04
Well that is exactly the same problem as I have with and iPhone 4 so I would say that it is a known problem.
However Axel112 seems to have it working 
I wonder if he (or she) knows clearly all the versions and everything that has been done?

---

### Post by jmyette on 2011-01-04
> **migmruiz said:**
> Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```
and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

I still couldn't mount my iPhone after following those steps, so I followed step 2 on [http://www.taranfx.com/sync-iphone-linux]("http://www.taranfx.com/sync-iphone-linux"), but replacing libiphone-utils by libimobiledevice-utils, libiphone0 by libimobiledevice1 and python-iphone by python-imobiledevice:

```
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libimobiledevice-utils libimobiledevice1 python-imobiledevice libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
```

I'm now able again to copy music/photos from/to my iPhone. I think it's because libimobiledevice1 also needed to be updated to 1.0.4, not just libimobiledevice-utils. You may not need to install all the other libraries as I did.

---

### Post by JacquesKik on 2011-01-05
I followed the previously mentioned steps and (only after restarting) my ipod is getting recognized.

However, when syncing with Rhythmbox, everything is OK, except that the files never appear in the ipod.
When I replug it, and, in the autorun dialog, choose Amarok, the latter actually reads the files I've previously synced in Rhythmbox. But Rhythmbox itself doesn't read anything.

How do I get these files to show up in the ipod itself though ?

PS: This is the same problem mentioned by spegru and Add3r in page 7 of this thread... seems to be rather common.
I'm running the latest ipod touch 4.2.1 iOS and Ubuntu Lucid Lynx 10.04
I wonder what systems are running the people who managed to sync files.

PPS: Amarok doesn't read the ipod in its sources... the files come up straight in the playlist when I choose autorun in amarok.... I'd prefer working with Amarok when syncing my music rather than Rhythmbox...

---

### Post by Add3r on 2011-01-05
> **jmyette said:**
> I still couldn't mount my iPhone after following those steps, so I followed step 2 on [http://www.taranfx.com/sync-iphone-linux](http://www.taranfx.com/sync-iphone-linux), but replacing libiphone-utils by libimobiledevice-utils, libiphone0 by libimobiledevice1 and python-iphone by python-imobiledevice:

```
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libimobiledevice-utils libimobiledevice1 python-imobiledevice libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
```I'm now able again to copy music/photos from/to my iPhone. I think it's because libimobiledevice1 also needed to be updated to 1.0.4, not just libimobiledevice-utils. You may not need to install all the other libraries as I did.


Thanks jmyette,
I tried as you said, also verifying that I had the last packages from ppmcenery in Synaptic. At first, I couldn't read anymore the filesystem of the iPod, then, after I did the pair/unpair/validate, I coud browse the iPhone again.
However, now, when I try to transfer music with Rhythmbox, I get the error "Error transferring track: Error while getting peer-to-peer dbus connection: The name :1.90 was not provided by any .service files"

At least something changes...does anyone have an idea of what I could have done wrong?

By the way, if I am allowed to ask a silly question:
since iOs 4.2.1 is the source of all evil, could there be a way to use the access, that Ubuntu grants us the the iPhone's filesystem, to put back a good old version of ios?
I can delete and add files there, (but the iPhone itself won't read them), thus I guess I could also delete/modify system files
(there's a lot of technical knowledge I miss about that, but maybe it's theoretically possible!)

Cheers!

---

### Post by axel112 on 2011-01-05
> **spegru said:**
> Well that is exactly the same problem as I have with and iPhone 4 so I would say that it is a known problem.
However Axel112 seems to have it working 
I wonder if he (or she) knows clearly all the versions and everything that has been done?

The only thing I did, was adding the pmcenery repo and then:
```
apt-get install libimobiledevice-utils
```
Ubuntu then installed libimobiledevice-utils:i386 (1.0.4-1ubuntu1~maverick1) and upgraded libimobiledevice1:i386 (1.0.1-1, 1.0.4-1ubuntu1~maverick1)

I then did
```
idevicepair unpair
idevicepair pair
idevicepair validate
```

And it worked. Oh, by the way, it's he. ):P

---

### Post by spegru on 2011-01-06
can someone confirm what is the point of 
sudo apt-get upgrade ?

I didn't do that one so far as am a little reluctant to use it on my Mint system as I have had problems between Ubuntu and mint Repositories before using that command

---

### Post by JacquesKik on 2011-01-06
Update:

If I open the ipod touch icon that appears on my desktop, in the iTunes_Control>Device directory, there's a file named: SysInfoExtended (24.7 kb) and the songs synced but which do not appear on the ipod appear in the same folders (the F** folders) with the ones synced on iTunes and which appear on the ipod.

However, in my /home/ipod/iTunes_Control/Device there is a different file called SysInfo (19 Bytes) and no songs show up anywhere.

I'm wondering what does this difference in the directories reflect, and what is the true directory of the iPod icon that appears on the desktop ?

This is getting frustrating...

PS: I should've noted that I'm running a 60bit Toshiba, and that my iPod is not jailbroken.

---

### Post by Psyael on 2011-01-06
I have a lot of the same issues. iPod mounts, appears in Rhythmbox, file copy results in a syncing message, but it never shows up in Music.app.

---

### Post by spegru on 2011-01-07
A bit of an update.
Tried the libimobiledevice-utils and unpair, pair validate steps but it made no difference, music transferred to the iphone did not show up.
However I discovered that music transferred to the phone from itunes was then visible from Rhythmbox and could be transferred successfully to the PC

Only one step missing! Music on Linux PC to phone not working......

Is there a logfile to look at?

---

### Post by JacquesKik on 2011-01-07
That's exactly my situation spegru...

Today I tried deleting a song from Rhythmbox... to my surprise, it worked! well, partially, at least.
The file still appeared in the "Artists" tab on the iPod, but disappeared from the "Songs", and when I tried to play it (from the artists tab), it would automatically start the next song.

So the delete function works partially.

I wonder if someone is working on a fix for this problem, or are we still considered isolated cases ?

Thanks all

---

### Post by JacquesKik on 2011-01-07
*message inadvertently posted twice*

---

### Post by Psyael on 2011-01-07
I noticed the songs I added from Rhythmbox are actually in the folder structure of the device, and play if I open them up in Totem, so they're either copying incorrectly or something is wrong.

iTunes on Windows doesn't see the songs I added either, since someone reported getting the songs to "appear" after connecting to it.

---

### Post by spegru on 2011-01-08
Yes music is visible on the phone via file browsing from linux (or probably windows too) after transfer from Rhythmbox. It wont play on the phone though!

Another thing I noticed was that when the phone was connected to itunes for the first time (it's brand new and had only been tried with linux up until that point), there was a message saying that the device was already synchronised to another copy of itunes. It wasn't of course but it had been tried to synchronise with rhythmbox

So something has happened anyway. I wonder if Apple has done something deeply sneaky to the phone to prevent it syncing such as tying it to the mac address the PC network adaptor (which is unique). 
What would be interesting would be to see what happens if you try to synch with an itunes on another PC.

However, assuming it's not anything like that I remain interested in those who seem to have succeeded with iphones or ipods running 4.2.1. It seems that several of us have failed to get music to show up on the phone but some have done maybe some small thing and succeeded - but what is it?

---

### Post by RavisPohan on 2011-01-09
> **spegru said:**
> Yes music is visible on the phone via file browsing from linux (or probably windows too) after transfer from Rhythmbox. It wont play on the phone though!


Same problem for me. Also iOS 4.2.1, iPhone 4. All titles show up on Linux in the file tree, none are accessible from the iPhone. It is driving me crazy.

---

### Post by alpharaptor on 2011-01-09
I am trying to get an iPad that we got Mom for Christmas to mount so I can put pictures on it.  I followed the directions above, added the mcenry ppa, installed everything plus gvfs and gvfs utilities.  
The idevicepair validate comes up correctly.  When I plug the iPad into the USB port, it chirps.  Lsusb shows an apple device.  But it does not show up in Places, no icon comes up on the desktop and I cannot access any folders or files.  ~/.gvfs is empty.  I suspect an issue with gvfs but don't know that much about it or what it does.

The iPad is verson 4.2.1  The computer is a Lenovo laptop running Lucid 10.04 with all updates installed.

---

### Post by spegru on 2011-01-10
alpharaptor you will see on this thread that some of us are still having problems with 4.2.1, but it seems possible from what you wrote that you are a few steps behind us, because at least we can mount the idevices onto the system.
Did you do this yet?
sudo add-apt-repository ppa:pmcenery/ppa
You need that to get the most up to date version of libimobiledevice-utils

As a matter of fact although I am still having problems with music, at least I can access pictures - although I only tested that copying from phone to pc so far

---

### Post by alpharaptor on 2011-01-10
I added the mcenry ppa and downloaded the imobiledevice utilities.  That's where the idevicepair program came from.  It verifys that the iPad is connected.  lsusb also identifys it as connected.  The iPad chirps when plugged in.  But no icon appears on the desktop and there is no entry under Places.  I checked fdisk -l and mount -l and no mountable devices show up.  If I can just copy the pictures onto it that would be sufficient for now.  At some point I'd like to rip some of her classical CD's to MP3 (easily done in linux) and put them on it as well.  I don't care about syncing.  I know how to move and copy files.  (I also know how to use rsync)

I tried running Itunes under Wine to no avail as well.  About 3  years ago I set up a Ubuntu machine out of curiousity.  It was so superior to Microsoft in so many ways that when the old Win 98 machine died I did not replace it.  I will send this iPad back before I will spend another $500 on a crappy Windows machine just to transfer pictures to this thing.

---

### Post by spegru on 2011-01-10
what version of libimobiledevice-utils do you have? It need to be 1.0.4 at least before the phone/pad/pod will mount - at least that was my experience.

Fspot also allows you to transfer pictures but I only tried it iphone to pc so far

I can also now confirm that music on the phone shows up in rhythmbox and play and copies correctly

the only thing missing is transferring music the other way

---

### Post by alpharaptor on 2011-01-10
> **spegru said:**
> what version of libimobiledevice-utils do you have? It need to be 1.0.4 at least before the phone/pad/pod will mount - at least that was my experience.

Fspot also allows you to transfer pictures but I only tried it iphone to pc so far

I can also now confirm that music on the phone shows up in rhythmbox and play and copies correctly

the only thing missing is transferring music the other way

I'm running 1.0.4, the newest version.  Fspot does not see it.  Neither does anything else.  Is there some sort of mount command or utility that needs to be run?  Thing is it doesn't show up as a mountable device either.

---

### Post by alpharaptor on 2011-01-10
If I can just get it to do what is demonstrated in the first 50 seconds of this video I will be more than happy!  This shows that it *is* possible

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by alpharaptor on 2011-01-10
If I can just get it to do what is demonstrated in the first 50 seconds of this video I will be more than happy!  This shows that it *is* possible

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by JacquesKik on 2011-01-10
alpharaptor you don't really have to consider buying another computer or whatever to get your iphone working on Linux...

There's an easy and 100% effective solution which I've opted for today: VirtualBox. It's a linux app that allows you to install and run a windows operating system within it.

Of course go for windows xp, it's the lightest, and it loads in just a couple of secs!
Until we get this bug fixed, this seems the best solution.

See? even with its downsides, Linus is still superior! ;)

PS: My internet is really slow now and I can't search for the documentation for you, but you can easily find it. Beware that after you install everything you have to fix a bug in a script to get it working rightly. It's all in the official ubuntu documentation website.

---

### Post by alpharaptor on 2011-01-10
I've not had experience with virtualbox but I did try running iTunes under Wine "reporting" win XP and that did not work.   One thing I did do was set up an old computer with win xp just to run itunes.  I can't go online with it because if I do I get a product activation warning and then it gets disabled and I have to reformat and reinstall XP.  Just one more of the many reasons I try to run a micro$oft free house (which incidently I have done successfully for the past 2 years until I got her this expensive paper weight for Christmas).  Will I have this problem with virtualbox?

I can live without going online as I only want to transfer pictures from various cameras to the hard drive of my desktop (Ubuntu Lucid) to the iPad.  But if I use the old XP box transfer them to the iPad with Itunes (a ghastly frustrating process) and then delete them from the hard drive, the next time I log in iTunes delets them from the iPad.  This is maddening.  I just want to be able to copy pictures from a hard drive to the iPad and leave them there until she asks me to delete them.  

I have until 1/31 to return the iPad so long as it's not been opened or jailbroken.  I'm told to get a generic tablet PC and put Android on it.  Anyone have experience with that?

> **JacquesKik said:**
> alpharaptor you don't really have to consider buying another computer or whatever to get your iphone working on Linux...

There's an easy and 100% effective solution which I've opted for today: VirtualBox. It's a linux app that allows you to install and run a windows operating system within it.

Of course go for windows xp, it's the lightest, and it loads in just a couple of secs!
Until we get this bug fixed, this seems the best solution.

See? even with its downsides, Linus is still superior! ;)

PS: My internet is really slow now and I can't search for the documentation for you, but you can easily find it. Beware that after you install everything you have to fix a bug in a script to get it working rightly. It's all in the official ubuntu documentation website.

---

### Post by alpharaptor on 2011-01-11
I got the iPad to mount!  Turns out gvfs was corrupted.  Autoremove and reinstall fixed that and a bunch of other problems, like inability to browse samba shares.

However it appears that just copying the photos to the PHOTOS or DCIM folders on the ipad won't make them accessible, as it does with cameras.  I tried using the Tripod and iPixpod programs but they apparently only work with iPods and not iPads.  Anyone got an idea how to fix this?

Thanks again to everyone for your help!

---

### Post by Caldur06 on 2011-01-11
Cool, my topic is still here.

Okay, I've done everything in the topic and I've had some weird results.

A few days ago I mounted my iphone and synced three albums. None of them would show up on the iphone. I tried deleting one of the albums to see if that would force an update to the library db. No such luck. Well, the next day I'm thumbing through my library and the two albums I synced were actually there! The one I deleted obviously wasn't. So, in the past three days I've managed to sync music to my iphone and I've been able to find and listen to it on the phone.

However, yesterday, I went back to try to add the album I synced and deleted. I couldn't get this to work for anything. I tried syncing/deleting several times, restarting the Music.app, restarting the iphone, restarting rhythmbox, deleting rhythmbox/ipod's gconf, etc. Every trick I knew and I couldn't get that album synced. I hadn't changed any of the packages since I had a successful sync.

Today I just plugged the phone into a windows computer, played a song from itunes, and it finished the sync. So if you do have access to a windows machine, that's an option. Although it would be nice to not have to worry about using two computers to put music on my phone.

---

### Post by spegru on 2011-01-12
Caldur06, what exactly did you do with itunes on windows? I tried a normal sync (I think) and it still didn't help

BTW a while back, on another ipod (a 6th gen ipod classic) I had a problem with music appearing on the ipod but I discovered that if i ejected using gtkpod rather than rhythmbox - it worked ok. I wonder if that would work now....

---

### Post by spegru on 2011-01-13
I can confirm a few further things

1. Pictures cannot be transferred from PC to iphone either, although as with music they can be transferred from iphone to pc.
2. GTKphone connects to the phone ok but syncing it from there makes no difference
3. GTKphone also cannot transfer music to the iphone and have it appear on the iphone.
4. In fact GTKphone exhibited an error while trying to transfer music, which was 'Unsupported Checksum type" - could that be a clue to the problem?

---

### Post by Sonsum on 2011-01-14
installing the pmcenery ppa and doing a system worked perfectly to get Maverick to recognize my ipod touch 2g running 4.2.1.

Not sure about syncing though since I use my other XP computer for that.

---

### Post by rosencrantz on 2011-01-14
> **alpharaptor said:**
> I've not had experience with virtualbox but I did try running iTunes under Wine "reporting" win XP and that did not work.   One thing I did do was set up an old computer with win xp just to run itunes.  I can't go online with it because if I do I get a product activation warning and then it gets disabled and I have to reformat and reinstall XP. [...]  Will I have this problem with virtualbox?
[...] I just want to be able to copy pictures from a hard drive to the iPad and leave them there until she asks me to delete them.  
[...] I'm told to get a generic tablet PC and put Android on it.  Anyone have experience with that?

Hi alpharaptor,
my 5ct on some of your issues:
a) AFAIK, wine has no USB support, so no luck there
b) Windows doesn't distinguish between a virtual and a physical machine, so you would still have activation problems without a license.
c) In my experience, itunes on a virtual machine is excruciatingly slow. I can barely manage single-file transfers (VB on a i5-450M, 4GB RAM, iTouch 4G), managing a >50GB library is hopeless, that's why I kept the pre-installed Win7.
d) On itunes deleting pictures: Have you set it up to sync pictures? Try disabling that option and dragging/dropping images by hand.
e) The Android question: On my phone, the multimedia libraries are on the SD card and that registers on every OS with read/write access. You get further system access with the Android SDK, which is also available for Linux. So, if you want to avoid Windows at all cost, go for the new tablet - just keep in mind it's not an iPad (different hardware, look and feel, range of apps).

Cheers,
rosencrantz

---

### Post by Spook Bat on 2011-01-14
> **migmruiz said:**
> Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```
That worked out great for me.  Thanks for your time!  Using an iPhone 3G.

---

### Post by spegru on 2011-01-15
> **Sonsum said:**
> installing the pmcenery ppa and doing a system worked perfectly to get Maverick to recognize my ipod touch 2g running 4.2.1.

Not sure about syncing though since I use my other XP computer for that.

Could you have a look to see if it syncs using rhythmbox or gtkpod or amarok or banshee?
That is the one step missing for several of us

---

### Post by spegru on 2011-01-15
> **Spook Bat said:**
> That worked out great for me.  Thanks for your time!  Using an iPhone 3G.

What iphone firmware do you have?

---

### Post by altjx on 2011-01-15
> **Spook Bat said:**
> That worked out great for me.  Thanks for your time!  Using an iPhone 3G.

Nice, thanks. This worked for me. I have an iPhone 4 running iOS 4.2.1 (Not jailbroken)

---

### Post by spegru on 2011-01-15
> **altjx said:**
> Nice, thanks. This worked for me. I have an iPhone 4 running iOS 4.2.1 (Not jailbroken)

Hi altjx you have the same phone & ios as me. Does your music syncing work too? Are you using rhythmbox?

---

### Post by altjx on 2011-01-15
> **spegru said:**
> Hi altjx you have the same phone & ios as me. Does your music syncing work too? Are you using rhythmbox?

Hey Spegru,

I use Rhythmbox to listen to the music, but I didn't know iPhone could sync music from Rhythmbox? Can it really? If so is there a guide somewhere? I thought it only worked with iTunes

---

### Post by spegru on 2011-01-16
Hi altjx. So you're not managing the iphone4 (4.2.1) from rhythmbox?
That's what several of us have been trying to do.

State of play is that default 10.10 & Mint10 installations do not mount the phone at all but by adding the new pmcenery ppa and thereby upgrading libimobiledevice-utils to 1.04 to it does. I guess you did that much already. However although you can see into the phone from you file manager and also from rhythmbox, and also play music in there, and also copy music from there to your pc and also (seemingly) transfer music from the pc to the phone, it never shows up on the phone. In fact the same applies to pictures. I also tried gtkpod and that has the same problem (it showed an 'unknown checksum' errror), Rhythmbox etc all work ok with older devices or with older firmware than 4.2.1

I don't know how to get that last vital 1%  and would be grateful to hear from anyone who succeeded!

---

### Post by altjx on 2011-01-16
> **spegru said:**
> Hi altjx. So you're not managing the iphone4 (4.2.1) from rhythmbox?
That's what several of us have been trying to do.

State of play is that default 10.10 & Mint10 installations do not mount the phone at all but by adding the new pmcenery ppa and thereby upgrading libimobiledevice-utils to 1.04 to it does. I guess you did that much already. However although you can see into the phone from you file manager and also from rhythmbox, and also play music in there, and also copy music from there to your pc and also (seemingly) transfer music from the pc to the phone, it never shows up on the phone. In fact the same applies to pictures. I also tried gtkpod and that has the same problem (it showed an 'unknown checksum' errror), Rhythmbox etc all work ok with older devices or with older firmware than 4.2.1

I don't know how to get that last vital 1%  and would be grateful to hear from anyone who succeeded!

Not at all. I'm actually about to go back to Windows 7 Ultimate though. Good luck guys

---

### Post by phophollety on 2011-01-16
I was having the same problem with my iTouch 3gen with iOS 4.2.1, but after reinstaling the libimobiledevice-utils the problem just solved.. Now I can manage it through rythmbox

Tks guys!

---

### Post by spegru on 2011-01-17
phophollety that is interesting. I would expect that the important thing is the firmware, so even though ipod touch is different from iphone4 it may be you have done something I have failed to do so far.
Can you check whether you can put music onto the ipod from rhythmbox?
If so, are you sure you didnt do anything else to get it working?

---

### Post by bapoumba on 2011-01-17
> **spegru said:**
> Hi altjx you have the same phone & ios as me. Does your music syncing work too? Are you using rhythmbox?
I can transfer music to and from the iPod, but sync does not work.

---

### Post by spegru on 2011-01-18
how do you mean you can transfer music but sync doesnt work?
Can you play music on the ipod which you put there from the PC?

---

### Post by bapoumba on 2011-01-18
> **spegru said:**
> how do you mean you can transfer music but sync doesnt work?
Can you play music on the ipod which you put there from the PC?
Yes, I can play the music I added with rythmbox on ubuntu. I can move to and from the iPod to rythmbox. The sync button on rythmbox  does not do anything.
This iPod is also on my mac, so most of my music library is in iTunes on the mac. I use ubuntu when my kids want CDs I've bought (if I've ripped them once and they are on the iPod, I do not rip a second time) on their own players. One of them is an iPod nano, with no issues at all. I sometimes also get music from them, but not much. I'm less fond of their stuff than they are of mine :)

---

### Post by JacquesKik on 2011-01-19
There's been an update to several packages from the ppa:mcenery today... no idea what's changed/fixed (after all the fiddling I had done my ipod isn't recognized by ubuntu anymore so I don't know if this update fixes the syncing issues).

---

### Post by JacquesKik on 2011-01-19
There's been an update to several packages from the ppa:mcenery today... no idea what's changed/fixed (after all the fiddling I had done my ipod isn't recognized by ubuntu anymore so I don't know if this update fixes the syncing issues).

Any input would be appreciated!

---

### Post by bapoumba on 2011-01-19
Oh, I've not seen the update yet, and I have to run for now. I'll look into it when I come back tonight, thank!

---

### Post by arpoodle on 2011-01-19
Upgraded my iPhone 3GS to 4.2.1 last week.

Before the upgrade I would get prompted to open fspot and rhythmbox when I plugged my iPhone into my laptop (ubuntu Lucid 10.04.1), and it was mounted automatically.

After the upgrade, it no longer mounts and isn't seen in rhythmbox.

---

### Post by spegru on 2011-01-20
Arpoodle you need to to do the steps at the top of page 8 of this thread.

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update

If you have libimobiledevice-utils already (I think you must have if it was working before) you will then get the new version and your phone should mount

However I would be interested to see if you can put music on the phone from rhythmbox, I can't but then I have an iphone4. It will be interesting if you can do it on an iphone3. bapoumba seems to have done it on a ipod with ios 4.2.1


ps. how do i get rid of the stupid smiley that appears in my text above? (copy/paste still works correctly tho)

---

### Post by mpw on 2011-01-22
Works perfekt!

Thanks to [jmyette]("http://ubuntuforums.org/member.php?u=1217999")!!!

---

### Post by DrJohn999 on 2011-01-23
Fresh install of 10.10 on a Asus Eee-1215N; same problem occurs with iPhone 4 + 4.2.1. Above fix works fine for me, with install of the pmcenery ppa plus libimobiledevice-utils, which were not installed by the main distro,

I can play tunes from the iPhone through RythmBox (not that the speakers on this little thing sound too good...)

I had the same problem on a Lucid desktop upon upgrading to Maverick when it released in October, and had hoped that this one was into the mainstream by now. Maybe in 11.04??

---

### Post by Komputor on 2011-01-23
@spegru: I think that bapoumba doesn't understand our question. I too am running an iPhone 3GS with iOS 4.2.1 NOT jailbroken with ubuntu 10.04 lucid 32 bit and after updating libimobiledevice and utils and getting the pmcenery/ppa, I can mount, search, and play songs/view photos, transfer songs/photos to pc, but I can not transfer the other way. I wonder if this has anything to do with the firmware itself (forcing you to use iTunes on either a windows box or a Mac). Let's not forget that the enemy can be just as smart as us sometimes. I will do a little research on this regarding the iOS itself and see what I can uncover. Please if anyone has any insight it would be greatly appreciated, if not already so.

---

### Post by bapoumba on 2011-01-23
Hmm, the other day, I did move a couple songs from rythmbox to the iPod. I had to wait for the library to update on the iPod, but the songs were there and I can listen to them. I have not tried pics though.
Are there any tests I may run for you ?

---

### Post by Komputor on 2011-01-23
> **bapoumba said:**
> Hmm, the other day, I did move a couple songs from rythmbox to the iPod. I had to wait for the library to update on the iPod, but the songs were there and I can listen to them. I have not tried pics though.
Are there any tests I may run for you ?

What device are you using? That's the question spegru and myself (amongst others) are in need of answering. 

After doing some research I have found that apple has decided to add some "enhanced security measures" and "security fixes" to iOS 4.2.1. I suspect these have something to do with the way a computer (albeit a Mac, PC, or Linux) "talks" to the idevice. And get this, iOS 4.3 is around the corner! Wonder what jobs is going to do next? Probably block out Linux users all together with some kind of code that detects a Linux os. Until I get the functionality of adding/removing what I want in ubuntu, I am stuck with my dual boot vista/ubuntu for now :(

---

### Post by bapoumba on 2011-01-23
I have 4.2.1 [noparse](8C148)[/noparse], Maverick, pmcenery's PPA all up to date. One thing I have not said though, is:
```
Bus 001 Device 004: ID 05ac:1293 Apple, Inc. iPod Touch 2.Gen
```
The iPod is not jailbroken either, but it is a second gen device. Sorry I missed the question and I think it explains all the differences :/

@spegru: please try the BBcode noparse tags for [noparse]:p[/noparse], there is a link in my sig ;)

---

### Post by suzy223 on 2011-01-25
I managed to get my 8GB iPod Touch to mount with Rhythmbox and I put this song on it (album artwork and all... crispy clear resolution) and it synced, but whenever I click on 'Scan Removable Media' nothing happens. I have to drop a song into the list for the iPod to sync--I don't want to have to do that. I really want to delete a song I put in through Rhythmbox from my iPod and it's getting quite frustrating now... if you can put songs on the iPod, why can't you delete them through Rhythmbox as well? :S

Sorry if this is the wrong thread for it.

---

### Post by silverbolt027 on 2011-01-27
Can anyone else confirm that you can add a song to a playlist and it shows up on your iPod?  I have an iPod touch 2nd gen and I can't get anything to write to the iPod, but I can read it just fine.

---

### Post by johntaylor1887 on 2011-01-27
> **silverbolt027 said:**
> Can anyone else confirm that you can add a song to a playlist and it shows up on your iPod?  I have an iPod touch 2nd gen and I can't get anything to write to the iPod, but I can read it just fine.

Did you install the latest ifuse? It works for me using gtkpod.

---

### Post by ctsdownloads on 2011-01-28
Just to be clear, iOS 4.2.1 is a fail for me with the latest PPA delivered goodness from libimobiledevice, ifuse, usbmuxd installed.

Now here's where it gets interesting. Because I did the update from 10.04 to 10.10, I am apparently still using the following - at the same time.

```
libimobiledevice0
``` and ```
libimobiledevice1
```

This might be why I am having trouble. Removing both, installing libimobiledevice-utils to see which of the above it favors. Will post back.

**Edit:** Ubuntu allows me to remove the older libimobiledevice0, which also removed Rhythmbox and Banshee. So I have to reinstall those. Removing the other one, wasn't happening due to its tie-in with the Ubuntu/GNOME desktop. So libimobiledevice1 was left installed. Right now, with the older stuff removed, I am installing libimobiledevice-utils, then installing the Rhythmbox and Banshee stuff after that.

**Edit2:** Wild...even thought I explicitly removed Rhythmbox and Banshee, only Banshee was removed according to Synaptic and my programs list. Also, ability to mount is dead giving me an error of ```
"Failed to execute child process "/usr/lib/gvfs/gvfsd-afc" (No such file or directory)"
```

**Edit3:** Apparently removing libimobiledevice0, also ditched ifuse. So I had to reinstall it. Hence my "Failed to execute" error above I suspect.

So now I just did a 

```
idevicepair unpair
idevicepair pair
idevicepair validate
```

Each command indicated success, did with device plugged in of course. Disconnected Iphone 4, reconnected - 
```
Failed to execute child process "/usr/lib/gvfs/gvfsd-afc
```

This is awesome, let me tell ya. Rebooting computer and trying that now.

**Edit4:** Rebooted, plugging in iPhone now brings no error, no mount, nothing. lol

lsusb shows device as ```
"Bus 001 Device 009: ID 05ac:1297 Apple, Inc."
```

And finally, dmesg shows this as I disconnect, then reconnect:


```
[  817.696985] usb 1-4.3: USB disconnect, address 9
[  820.200087] usb 1-4.3: new high speed USB device using ehci_hcd and address 10
```

**Edit5:** Found gvfs-backends missing, so I reinstalled it. (this is getting ridiculous).

Then I ran

```
/usr/lib/gvfs/gvfs-afc-volume-monitor
```
got this as I expected to when I connected the iPhone for the 50th time today

```
Volume monitor alive
creating volume for device uuid 'my uuid which I am not sharing'
```

and of course---NO MOUNTING. Honestly ready to say that that it's best to go Sandisk and call it a day for MP3 player support, this just isn't worth fighting Apple on anymore.

**Edit6:** Because I never did know when to quit. :)

I rebooted the computer yet again. This time, my iPod did mount. So clearly gvfs-backends piece helped, but the PC had to be rebooted again to matter. Cool. So I can open things in F-Spot. Yes, you still have to browse to the DCIM/100APPLE directory manually though. But that is working - getting images and videos is possible! One down, one to go.

Now  Rhythmbox, is no longer seeing my iPhone. Yes, it's mounted to my desktop, F-Spot sees it. But no love from Rhythmbox. Why? Remember earlier when I removed Rhythmbox? Yeah, guess what else went with it? The rhythmbox-plugins package. you know, the one that also installs libgpod-common and ligpod4? :)

So back at Synaptic. I install:

```
rhythmbox-plugins
``` 
which also "automagically" gives me libgpod-common and ligpod4 as well. Cool. But before I do this, I am unmounting my iPhone...just to be safe.

Results?

Rhythmbox is now showing my iPhone when I plugged the iPhone back in...because it asks, I say yes, you get the idea. Ah, great...but will it actually allow music appearing to be transfered to it to STAY on the device this time? This was the problem in the first place. I do a sync, music appears to be transferring... I unmount, no music on iPhone. So let's see if after all of this, I can finally stop screaming at my computer. :)

Right click iPhone in app, "sync with library" option selected.

Activity below as it did from the beginning of this post, shows a sync. iPhone also shows this, but this happened before...meant nothing after unmount. So let's see if it bothers to work this time. What bothered me the most was how the iPhone like before, would go in and out of sync mode on the phone screen, indicating this was another waste of time. but you know what, if this last attempt fails, then I will go on record in stating that iOS updates render any more fusing with this a waste of time. I mean, if everything that can be done, has been, why keep doing this? It would instead indicate that it may think it's transferring music, but it's clearly not writing anything to the database. :)

So what was the end result? Drum roll please.... **NOTHING**. Nope, *_does not work_*. Encourage you to try this with GTKpod too, so you can watch the error codes fly by. :(

**So what appears to be going wrong**? I can browse into the iPhone via Nautilus, visit the /iTunes_Control/Music directory and sure enough, there are lots of numbered directories all starting with the letter F. clicking into one, there is some of my music -- it was indeed, transfered over. So the error is the database isn't recording the change. Awesome - not.

Sorry folks, it may work for some people, but I am VERY skeptical as to this working for iOS 4.2.1 on the iPhone 4. Anyone claiming it does, **prove it**. Did everything humanly possible on the iPhone 4, it's not happening. Looks like my music will remain on Sandisk devices in the future. Bite me Apple.

---

### Post by silverbolt027 on 2011-01-28
Thanks for trying man!

---

### Post by ctsdownloads on 2011-01-28
> **silverbolt027 said:**
> Thanks for trying man!

Wish I had success to report, just updated the last attempt above. 

All that can be tried, has been. Apple is to blame as it's an iTunes world if you want music on the iPhone 4. VirtualBox and iTunes might be an option for some though.

Edit: While there is Ubuntu One Music for the iPhone, and I have tried it, the service remains painful to use due to one simple feature that kills it for me. My playlists. I mean really, is it THAT hard to allow me to even **create** them on the phone or import them somehow? It's a showstopping missing feature and Canonical has done **nothing** to fix it, either. Service remains a toy until they do...

---

### Post by ctsdownloads on 2011-01-28
FYI everyone:

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

> Music/Video Synchronization - Done - 4.2.1 - Rhythmbox, gtkpod and Amarok sync with latest libgpod >= 0.7.90. 
**The iPhone 4, iPad and Apple TV do NOT work.**

---

### Post by silverbolt027 on 2011-01-29
I've got an iPod Touch 2nd Gen....so it should work then.... no?

---

### Post by ctsdownloads on 2011-01-30
> **silverbolt027 said:**
> I've got an iPod Touch 2nd Gen....so it should work then.... no?

Running 4.2.1, I doubt it. But it wouldn't hurt to try. Look everything I posted above carefully, you'll spot how everything appears to go fine...only to fail to stick when you unmount.

---

### Post by elbrios on 2011-01-31
**How to Fix it**
To correct this problem, open your terminal:

 sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by ctsdownloads on 2011-01-31
> **elbrios said:**
> **How to Fix it**
To correct this problem, open your terminal:

 sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

I assume you're talking about something else, because [this post here]("http://ubuntuforums.org/showpost.php?p=10406883&postcount=125") chronicles the various ways iOS 4.2.1 will not sync music successfully. It's a fact.

*Obviously* the repo was added, everything was properly updated....lol

```
iPhone4+iOS+4.2.1= music transferred without the database reflecting this fact.
```

---

### Post by gpwil1 on 2011-02-02
> **ctsdownloads said:**
> Just to be clear, iOS 4.2.1 is a fail for me with the latest PPA delivered goodness from libimobiledevice, ifuse, usbmuxd installed.

..

Sorry folks, it may work for some people, but I am VERY skeptical as to this working for iOS 4.2.1 on the iPhone 4. Anyone claiming it does, **prove it**. Did everything humanly possible on the iPhone 4, it's not happening. Looks like my music will remain on Sandisk devices in the future. Bite me Apple.

Thank you for trying this! I was having issues and didn't have nearly as much patience as you. Good to know you took one for the team to ensure it didn't work after all :P

G

---

### Post by ctsdownloads on 2011-02-02
> **gpwil1 said:**
> Thank you for trying this! I was having issues and didn't have nearly as much patience as you. Good to know you took one for the team to ensure it didn't work after all :P

G

Well the devs have done everything they can, all we can do now is support the hardware that chooses to support us. :)

---

### Post by scarral on 2011-02-08
> **ThatBum said:**
> [COLOR=Red]Well, do you know how to move files around with the terminal? Extract the zip up there and change the directory to the extracted archive's folder in terminal (cd ~/Downloads/libimobiledevice-1.0.4/, presumably). Then move both files to /usr/lib as root (sudo mv * /usr/lib/), and rename the old lib so it's not unintentionally used, also as root (sudo mv /usr/lib/libimobiledevice.so.1.0.3 /usr/lib/libimobiledevice.so.1.0.3.old), and that's it, no reboot or anything.

[COLOR=Black]Edit: This is now moot. 1.0.4 is now in the repos.[/COLOR]
[/COLOR]

I have Ubuntu 10.04, and I have libimobiledevice version 0.9.7. I just did a complete update via sudo apt-get update, and that library didn't get updated. In the synaptic package manager I can't find a way of updating this package. I tried downloading this libimobiledevice-1.0.4.zip recommended here, but contrary to what is described here, there's only one file in there. Otherwise I did all the rest described, and still same problem.

What worked for me was the following commands described above: 

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

After I did that I had to reboot before my iPod was recognised again.

Thanks!

---

### Post by silverbolt027 on 2011-02-08
Just a little note, it seems that the syncing issue is with libgpod and its inability to sync with Apple Database version 5, which was the result of the 4.2.1 update.  They are working on it.  See here:

[http://libiphone.lighthouseapp.com/projects/27916/tickets/199-ipod-4g-ios-421-sync-problems](http://libiphone.lighthouseapp.com/projects/27916/tickets/199-ipod-4g-ios-421-sync-problems)

---

### Post by sabutuga on 2011-02-10
> **migmruiz said:**
> Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

Hi there,

This just worked for me on my ipod  touch 3nd generation after reboot I manage to use the ipod with Banshee.

Thank you very much, if only everything with Ubuntu was this easy!

---

### Post by silverbolt027 on 2011-02-12
@sabutuga - Were you able to add music to your ipod, or just mount it?

---

### Post by sabutuga on 2011-02-13
> **silverbolt027 said:**
> @sabutuga - Were you able to add music to your ipod, or just mount it?

Yes and it transferred faster than when I had itunes on win7!

I didn't do this bit:

idevicepair unpair
idevicepair pair
idevicepair validate

because I didn&#8217;t succeeded using my ipod with Banshee before!

---

### Post by tora201 on 2011-02-13
Ah, this might be even simpler? (sorry if repeated somewhere below - I did not read through the whole thread)

Just do this:

sudo add-apt-repository ppa:pmcenery/ppa

sudo apt-get update
sudo apt-get install libimobiledevice1

From: 
[http://www.youtube.com/watch?v=HmsnkD47JRE&feature=related](http://www.youtube.com/watch?v=HmsnkD47JRE&feature=related)

Transferring music through Banshee works perfectly (Mint 10)

---

### Post by spegru on 2011-02-16
What is confusing this thread is that some people are using ipods and other are using iphones.
It appears to be only Iphone4 that has the syncing problem

---

### Post by sabutuga on 2011-02-16
> **spegru said:**
> What is confusing this thread is that some people are using ipods and other are using iphones.
It appears to be only Iphone4 that has the syncing problem

I had this problem with my Ipod touch 3rd generation iOS 4.2!

---

### Post by jeyml on 2011-02-18
I have found i way to sync you'r iphone with Rhythmbox.It's actualy verry simple:
Go to : ~/.gconf/apps/rhythmbox/state/ipod/
Delete gconf.xml and open up Rhythmbox.After that connect you'r iphone and it will work like a charm.You cand now add songs easily to you'r iphone/iphod.Hope i've helped.
I'm using Iphone 3g with jailbroken 4.2.1 an Ubuntu 10.10.

---

### Post by charlieab1 on 2011-02-19
try this website i my iphone 3gs working after reading this 

[http://www.underthepurplesky.com/2011/01/unable-to-mount-iphone-on-ubuntu-10-10/]("http://www.underthepurplesky.com/2011/01/unable-to-mount-iphone-on-ubuntu-10-10/")

good luck

---

### Post by cvmostert on 2011-03-08
Hi there,

this worked perfect for me, I had the iPhone unplugged and did not have to do the unpair/pair part.
Thanks!

---

### Post by paulysa1969 on 2011-03-08
Yep. Same with me.

Ubuntu 10.10. iPhone 3G with Wi-Fi that just stopped working and also slow so updated SW to IOS 4.2.1. Big mistake since now empty iPhone. VirtualBox 4/WindowsXP/iTunes not working so useless empty iPhone 3G:confused::confused:.........

Error is: "Invalid Mount Spec"

---

### Post by Add3r on 2011-03-09
This is really getting confusing.
Can everyone that writes please specify:
device (Iphone, Ipod touch)
Version (3gs, 4 etc)
Firmware (4.2.*, or 4.1.* or former)
Jailbroken or not

what version of ubuntu are you using
did you install the P. Cenery files?
if are you using virtualbox with windows and iTunes (BTW I don't see the point of writing about it in an Ubuntu forum, you're actually using Windows).

and, before screaming Eureka, tell what does work or not:
is it possible to mount the device?
is it possible to see the contents?
is it possible to transfer pictures?
Can you play the music stored in the device using a media player like Amarok, Rhythmbox etc?
Can you transfer music in the device, AND play it in the device itself after you unmount it?

My 2 cents:
Iphone 3gs, not jailbroken, firmware 4.2.1, trying to use it with Ubuntu 10.10, installed all the files from the ppacenery repository.
 I can mount it, see the contents, transfer pictures, play the music in Rhythmbox, transfer music in it with Rhythmbox but NOT play the music I transferred after I unmount the device.
The files get transferred but the database of the device just ignores them.

I also tried to delete the  ~/.gconf/apps/rhythmbox/state/ipod/gconf.xml file as suggested by jeyml, no improvement.
With firmware 4.1 Everything was working (also the springboard manager from the libimobiledivice pages!). After the update to 4.2, it all went bad, and I had to upgrade Ubuntu to 10.10 and install the new file from ppacenery to get to this point again.

From my understanding, for devices with 4.2.* firmware, not jailbroken, this is the state of the art:
no sync with music library so far.
Prove me wrong please :-)

Cheers!

P.S:
here somebody gas my same impression:
[http://www.lockergnome.com/linux/2011/01/30/getting-the-iphone-4-working-with-ubuntu/](http://www.lockergnome.com/linux/2011/01/30/getting-the-iphone-4-working-with-ubuntu/)
The problem is not the device as much as the iOS version! (up to 4.1 good, 4.2 bad!)

---

### Post by JFollest on 2011-03-09
Ok.. Iphone worked perfectly with Rhythm Box with info  from this thread. Thank you
Music showed up, played etc.

However, new problem.
Phone does not show in Rhythm box anymore possibly since installing Virtual Box but I am not sure on that one yet.
Music now doesn't show up.

Strange part is - 
                        Phone is mounted
                        Can access all folders/pictures etc.

Details:
Iphone 3GS 16GB v 4.2
Not Jailbroken
Ubuntu Lucid 10.4
Not using Virtualbox for Itunes
deleted gconf

And YES! This was already working with v 4.2.1 playing music in Rhythm box.

Thanks for your help in advance
Joe

Issue somewhat solved. It seems it was an issue with iphone-set-info staying in CPU and hogging it. I also removed ilibdevice0 and reapplied ilibdevice1.

Upon reboot everything was perfect again. Songs are in Rhythm Box and play.

BUT>>>

When I log out and back in again, Rhythm Box no longer see's my phone but yet it is Mounted and so on.

Joe

---

### Post by Add3r on 2011-03-09
> **JFollest said:**
> Ok.. Iphone worked perfectly with Rhythm Box with info  from this thread. Thank you
Music showed up, played etc.

Details:
Iphone 3GS 16GB v 4.2
Not Jailbroken
Ubuntu Lucid 10.4
Not using Virtualbox for Itunes
deleted gconf

And YES! This was already working with v 4.2.1 playing music in Rhythm box.

Thanks for your help in advance
Joe

Joe, do you confirm that, at least for a while, you were able to sync music in your iphone with ios 4.2 using rhythmbox? Did you get a "sincronizing" message on your iphone? Did music appear in your phone's itunes?

If yes, which steps did you follow exactly?

---

### Post by JFollest on 2011-03-09
No, I confirmed I could see all my music and play all my music in Rhythm Box. I will try syncing songs right now as I have fixed the last problem.

Sort of..

I'll let you know shortly..
Joe

---

### Post by JFollest on 2011-03-09
> **Add3r said:**
> Joe, do you confirm that, at least for a while, you were able to sync music in your iphone with ios 4.2 using rhythmbox? Did you get a "sincronizing" message on your iphone? Did music appear in your phone's itunes?

If yes, which steps did you follow exactly?

Yes It synchronized
Yes I saw it in my phone and played it

I followed these from pg 4 of this thread: 

Also in synaptics I removed Libdevice0 and added libedevice1

QUOTE=migmruiz;10208430]Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```[/QUOTE]

Let me know if it works for you.
Joe

---

### Post by landon418 on 2011-03-09
Thanks you so much you saved my day, otherwise I wouldn't have music on the long bus ride:popcorn:

---

### Post by Add3r on 2011-03-10
> **JFollest said:**
> Yes It synchronized
Yes I saw it in my phone and played it

I followed these from pg 4 of this thread: 

Also in synaptics I removed Libdevice0 and added libedevice1

QUOTE=migmruiz;10208430]Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```

Let me know if it works for you.
Joe[/QUOTE]

I managed to make it work as well! Now I am also able to sync music with Rhythmbox!
besides what jFollest already lists, I did two main things on 2 different laptops (both mounting Ubuntu 10-10):
went into Synaptyc and installed some more packages from the PMcenery rep:
libgpod-cil
libgpod-dev
libimobiledevice-dev
libusbmuxd-dev

I did this all in a desperate attempt, don't know what was that made syncronization work on the first laptop...:confused:

and, most of all:
in the second laptop I still had some old libimobiledevice interfering (even though I had removed it in Synaptyc and with apt-get remove):
itstarted to sync after I cleaned the folder /usr/local/lib/ from all the libimobiledevice files still there!

Thanks to everybody!
N.B.:
using iphone 3gs, unjailbroken, iOS 4.2.1

---

### Post by panderohit on 2011-03-17
works great. thanks. :)

---

### Post by J_khushal on 2011-03-18
i just followed the instructions here and now my IPHONE is connecting as well . . . . .AWESOME!!

---

### Post by timlev on 2011-03-20
Hi all,

Did this affect anyone's podcasts when you sync? All of my podcasts got separated on my Ipod Touch so that it is very hard to search through and find the most current episodes.  ](*,)

Thanks!

PS. I'm using Rythmbox to track the podcasts and to sync.

---

### Post by dok2033 on 2011-03-21
hi there I'm new Debian user and i can't add this repository to my source list its probably incompatible, any one help ...

---

### Post by Vanish00 on 2011-03-22
Thanks, this is exactly what I needed!

---

### Post by warrior_juggalo on 2011-03-22
Can someone re-write that out to do it in Fedora?, I Just re-installed Fedora and bought a HTC desire cause i thought my iphone 4 was never going to work again.

---

### Post by warrior_juggalo on 2011-03-23
Anyone?

---

### Post by Junosix on 2011-03-26
Post #151 worked for me :D  Thanks JFollest!

---

### Post by blue_bullet on 2011-04-02
Thank you.  Post #151 worked for me.  I had to upgrade my iPod touch to 4.3.1 via Windows 7 to get the device to work properly with Bluetooth on my new Toyota.  After doing so I could not mount my iPod.  Your instructions worked perfectly.  Thanks again.

---

### Post by maheshbhoir on 2011-04-04
thanks man. :)

---

### Post by alessandro0blanco on 2011-04-04
I have a jailroken iPod touch 4G with iOS 4.3.1.
Did someone manage to sync a 4G i touch?
(I tried, but I couldn't)
Thank you

---

### Post by vbghyu5 on 2011-04-05
My Iphone 3g on ios 4.2.1 at first wouldnt mount, but the instructions here got it to be recognized. Now, the tracks I put on with rythymbox show up on my phone, but are unable to play. Is this issue related?

---

### Post by fattyz on 2011-04-07
I had a similar issue with tracks not playing.  My iphone was skipping tracks as well.  I had used copytrans manager to do my playlists in windows.

Once I got set up in Ubuntu,(just getting upgrade manager current made it work)  I deleted everything on the phone, imported my tracks from windows to Ubuntu then into rythymbox, then I made playlists and all was well.

FattyZ

---

### Post by phazixc on 2011-04-08
I cann't say this will work for all, but i have been playing around for an hour trying to work this "libimobiledevice1" update and all I got back was

Unpacking replacement libimobiledevice1 ...
dpkg: error processing /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~lucid1_amd64.deb (--unpack):
trying to overwrite '/usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi', which is also in package libimobiledevice0 0:0.9.7-1ubuntu1
Processing triggers for hal ...


----------------BUT------------  I CORRECTED IT     -----------

what I did was in synaptic did the upgrade so i got the error, and libimobiledevice-utils was install which had a yellow marker and was 1.0.6, which left libimobiledevice1 1.0.1 still with an upgrade marker and deselected libimobiledevice0.

hit apply

which uninstalled only that a libimobiledevice-utils 1.0.6....

then remarkered libimobiledevice1 1.0.1, which install and upgrade nicely to 1.0.6 and reinstalled the utils 1.0.6..


its a little odd as to why this worked as i tried that 3 times early on in the day...

and now both are install correctly.

hope that helps if not sorry for wasting your time!!

p.s i also had my iphone plugged in!

---

### Post by phazixc on 2011-04-08
> **phazixc said:**
> I cann't say this will work for all, but i have been playing around for an hour trying to work this "libimobiledevice1" update and all I got back was

Unpacking replacement libimobiledevice1 ...
dpkg: error processing /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~lucid1_amd64.deb (--unpack):
trying to overwrite '/usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi', which is also in package libimobiledevice0 0:0.9.7-1ubuntu1
Processing triggers for hal ...


----------------BUT------------  I CORRECTED IT     -----------

what I did was in synaptic did the upgrade so i got the error, and libimobiledevice-utils was install which had a yellow marker and was 1.0.6, which left libimobiledevice1 1.0.1 still with an upgrade marker and deselected libimobiledevice0.

hit apply

which uninstalled only that a libimobiledevice-utils 1.0.6....

then remarkered libimobiledevice1 1.0.1, which install and upgrade nicely to 1.0.6 and reinstalled the utils 1.0.6..


its a little odd as to why this worked as i tried that 3 times early on in the day...

and now both are install correctly.

hope that helps if not sorry for wasting your time!!

p.s i also had my iphone plugged in!


iphone 4 4.2.1 works like a dream... good luck!!

---

### Post by richardh9936 on 2011-04-08
Thanks.  #151 worked for me today.
ipod touch 2g model MB531zp (ios 4.2.1)

---

### Post by jaxomnia on 2011-04-12
well done, I have to say I am no expert in Ubuntu or other Linux distro yet... this is one big lesson learnt :)  Thanks guys!!!!!

---

### Post by nathan28 on 2011-04-14
FWIW in 11.04B as of 13-04-2011, the iPhone (3g iOS 4.2.1 jailbreaked) mounts fine. Fedora 14 has the same dbus issue as 10.10. Have SSH'd into the phone many times today, altered some .plist files. I get the same looks-like-it's-syncing issues in Banshee--Banshee has crashed a couple times. I'm going to try Rhythmbox though it'll take a long time to discover my library and report back.

It's too bad that PwnPlayer app went all infinite development, really, I could have been happy with that.

While I was playing electrical engineer today my wife mentioned something about total cost of ownership earlier today. "But I only paid $30..."


EDIT: What do you call an 8GB USB stick that costs $699? Answer: An iPhone! Time to dirty up my package list trying to fix this, hopefully the pair/unpair trick will be all I need.

Both Banshee and Rhythmbox looked like they were loading. Both froze, up X, but that's to be expected in a beta.

---

### Post by Elvish Legion on 2011-04-17
I have an issue that doesnt seem like it wants to be fixed

I plug my ipod touch 3rd gen running unjailbroken 4.2.1 in to my ubuntu 64bit 10.10 install with the latest libimobiledevice (1.0.6) and usbmuxd (1.0.7)

When I plug the itouch in nothing happens, no errors no prompts nothing its like the computer doesnt detect it is there.

I open rhythmbox and I see for a brief second an unidentified object that then errors out telling me it is unable to open iPod touch 3rd gen 

I have checked this thread for hints but nothing has made any difference.

Edit: When I issue 

```

idevicepair unpair
idevicepair pair
idevicepair validate
```

I get
 idevicepair unpair
No device found, is it plugged in?

---

### Post by ocgstyles on 2011-04-21
I tried method in #151.  I installed the relevant repositories and packages.  Then this happens:

$ idevicepair unpair
ERROR: Unpairing with device 80aac372bcfc14f76305e21722834fe912663b2a failed with unhandled error code -3

The pair and validate commands both return SUCCESS...

I believe this is a 1st gen ipod touch.
 - OS: 1.1.5(4B1)
 - Model: MA627LL

Thoughts?

---

### Post by Daveyboy79 on 2011-04-22
bump for post #172, I have exactly the same problem.  I have the same versions of the packages and also see my device for a brief second.

unable to issue the commands idevicepair unpair:
No device found, is it plugged in?

_________________
Sony Vaio VPCF13Z8E
8GB Ram | Intel i7-740QM | nVidia GT 425 M

---

### Post by ocgstyles on 2011-04-22
> **ocgstyles said:**
> I tried method in #151.  I installed the relevant repositories and packages.  Then this happens:

$ idevicepair unpair
ERROR: Unpairing with device 80aac372bcfc14f76305e21722834fe912663b2a failed with unhandled error code -3

The pair and validate commands both return SUCCESS...

I believe this is a 1st gen ipod touch.
 - OS: 1.1.5(4B1)
 - Model: MA627LL

Thoughts?

Fixed it by installing iOS3 on my ipod.  Syncs perfectly now.

---

### Post by whistlerspa on 2011-04-24
I installed ifuse and then ran Update Manager.  It now works with Rhythmbox, but F-Spot Photo Manager had a fit, so I now use Shotwell Photo Manager instead. 

[10.10 64Bit Ubuntu running gnome 2.32.0]

---

### Post by spegru on 2011-04-25
has anyone successfully put music ONTO an iphone4 with 4.2.1 firmware?
Done all the steps but still struggling.....

---

### Post by morgue on 2011-04-25
> **migmruiz said:**
> I had to run that too


just remembering: to do that you need to have libimobiledevice-utils installed, if you don't have it
```

sudo apt-get install libimobiledevice-utils

```

This did it for me.

Plus these:
idevicepair unpair
idevicepair pair
idevicepair validate 

thanks!

edit: I posted "idevice", but it's actually "idevicepair".

---

### Post by mpcsm on 2011-04-25
See Post #8 in [http://ubuntuforums.org/showthread.php?t=1670314]("http://ubuntuforums.org/showthread.php?t=1670314")

Unable to mount iPhone_ org.freedesktop.DBus.Error.NoReply DBus error: MESSAGE DID NOT RECEIVE A REPLY (TIMEOUT MESSAGE BY BUS)

How to Fix it

To correct this problem, open your terminal and copy/paste the following:

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by owenhsu on 2011-04-26
> **mpcsm said:**
> See Post #8 in [http://ubuntuforums.org/showthread.php?t=1670314]("http://ubuntuforums.org/showthread.php?t=1670314")

Unable to mount iPhone_ org.freedesktop.DBus.Error.NoReply DBus error: MESSAGE DID NOT RECEIVE A REPLY (TIMEOUT MESSAGE BY BUS)

How to Fix it

To correct this problem, open your terminal and copy/paste the following:

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade

These steps do not work for me in 10.4, 10.10 and 11.4. After some debugging the GNUTLS and libimobiledevice code, I think I found a fix.

What works for me is:

rm -rf $HOME/.config/libimobiledevice

Apparently the config and/or security certificate files in the directory is causing trouble for the new version of the imobile library to talk to iphone 4. After the file is removed, ubuntu mounts both iphone 4.2.1 and 4.3.2 automatically without any problems.

Cheers!

---

### Post by conorsulli on 2011-04-26
> **owenhsu said:**
> These steps do not work for me in 10.4, 10.10 and 11.4. After some debugging the GNUTLS and libimobiledevice code, I think I found a fix.

What works for me is:

rm -rf $HOME/.config/libimobiledevice

Apparently the config and/or security certificate files in the directory is causing trouble for the new version of the imobile library to talk to iphone 4. After the file is removed, ubuntu mounts both iphone 4.2.1 and 4.3.2 automatically without any problems.

Cheers!

Question is when will we be able to manage the actual music on it?? I have tried it in Banshee and rhythmbox with the latest natty release & updates

---

### Post by spegru on 2011-05-03
The problem with this thread is that not everyone is using the same device and some are also unclear about what they achieved.

What I would like to know is whether anyone with an iphone4 running firmware 4.2.1 or higher - has managed to put any music ONTO the phone......!

---

### Post by jobicoppola on 2011-05-04
My ubuntu (11.04) box cannot mount the hfs filesystems my ipod (1st gen nano) or my iphone (3g 4.2.1 jailbroken) as read-write, so obviously none of the software (gtkpod, rhythmbox, banshee etc) will be able to either, no? Are other people having the same problem? Just wondering if it's even possible at all to write to hfs+ journaled  filesystems from ubuntu, as all my hfs* pkgs are up to date...

---

### Post by wolfen69 on 2011-05-04
I reinstalled on my ipod touch in november, but I'm not sure what version it is. But it does work just fine with gtkpod and 11.04

---

### Post by 4manifold on 2011-05-07
I installed imobiledevice-utils and followed the instructions in 151 and that worked for me.

---

### Post by spegru on 2011-05-09
Has anyone tried this with **iphone4** with firmware **4.2.1** (upward) and successfully managed to put music ONTO it?

---

### Post by stber321 on 2011-05-09
> **Caldur06 said:**
> iOS 4.2.1 was released today. I upgraded through iTunes on a Windows machine. I had a problem that [a lot of people are having]("http://techcrunch.com/2010/11/22/ios-42-bug/") though, where all of my songs are missing. So, the workaround that other people are using involves the iTunes that you normally sync your music with. Obviously I sync my music with my ubuntu, so that doesn't work.

I came home tonight and my computer isn't even recognizing my iPhone when I plug it in. So now I've got an iPhone with no music and an OS that's oblivious to it. >_<

so you come to Ubuntu Forums?????, i mean you could get some help here but why? is there not somwhare better to go asking about proprietary software?

---

### Post by zero13th on 2011-05-10
```
 
#151
sudo add-apt-repository ppa:pmcenery/ppa  
sudo apt-get update  
sudo apt-get dist-upgrade 

```these steps are working for me

---

### Post by spegru on 2011-05-25
Has anyone tried this with iphone4 with firmware 4.2.1 (upward) and successfully managed to put music ONTO it?

---

### Post by Swagman on 2011-05-25
Weve put music onto it.. and it **IS** there.. But as others have mentioned, The iPhones Database does not show the new song is there.

**Nobody** has answered that .. ALL Important issue yet.

Perhaps this issue should be spun off into its own thread ?

---

### Post by spegru on 2011-05-26
you are right of course, it's the having the iphone  4, (4.2.1+) show the music that is the missing link. If anyone has done it please respond!

---

### Post by zeefreak on 2011-06-07
thanks for putting this thread together. got my iphone working again.

personally, i'm just waiting for my iphone to die and then i'm moving to android. i am sick of apple not caring about the linux community, and i for one can't wait to walk away from it.

with android you don't even need an app to transfer music. just drag and drop. the device compiles your music db when you unplug it. it doesn't get any more simple than that. - except that it does. i've seen some reports that folks are transferring music over wireless - no cord necessary.

---

### Post by rickyble on 2011-06-09
> **spegru said:**
> Has anyone tried this with iphone4 with firmware 4.2.1 (upward) and successfully managed to put music ONTO it?

I have tried but have not been able to so far.  Iphone4 with 4.2.1...no joy as today.

---

### Post by wolfen69 on 2011-06-09
> **zeefreak said:**
> 
personally, i'm just waiting for my iphone to die and then i'm moving to android. i am sick of apple not caring about the linux community, and i for one can't wait to walk away from it.


Indeed. The only reason I am using an ipod touch is because I got it for $40 with Dr. Dre headphones. 

But anyway, I have had no problems getting it to work in gnome-shell in ubuntu and fedora. It looks like gnome 3 includes the proper libraries. Just some food for thought.

---

### Post by zeefreak on 2011-06-10
> **wolfen69 said:**
> Indeed. The only reason I am using an ipod touch is because I got it for $40 with Dr. Dre headphones. 

But anyway, I have had no problems getting it to work in gnome-shell in ubuntu and fedora. It looks like gnome 3 includes the proper libraries. Just some food for thought.

heh, i just realized something, i'm only using an iphone because i got it for free when i took some redhat training . . . oh sweet irony.

---

### Post by serlex on 2011-06-10
Anyone got it working with Natty and iOS 4.3.3?

Banshee recognizes the phone, copies/converts the songs, however don't see it on the phone!!

---

### Post by spegru on 2011-06-11
unfortunately that is the normal problem

---

### Post by rickyble on 2011-06-14
upgrade to natty and now at least can play and get to stuff on my iphone through fspot natilus and banshee.  If I could only copy music from and to on my linux media server.  last piece....

---

### Post by serlex on 2011-06-17
> **rickyble said:**
> upgrade to natty and now at least can play and get to stuff on my iphone through fspot natilus and banshee.  If I could only copy music from and to on my linux media server.  last piece....

Which version of banshee are you using? I can't get any music to show on my iphone4

---

### Post by wolfen69 on 2011-06-17
> **serlex said:**
> Which version of banshee are you using? I can't get any music to show on my iphone4

Have you tried gtkpod?

---

### Post by wolfen69 on 2011-06-17
> **zeefreak said:**
> heh, i just realized something, i'm only using an iphone because i got it for free when i took some redhat training . . . oh sweet irony.

Free is always good. :KS

But even if linux didn't support my itouch at all, I still have a windows install I use just for games and could use itunes. But I hate itunes with a passion. It is so convoluted and bloated, it's disgusting. But thankfully, gtkpod works great for me. Nice. Simple. App.

---

### Post by jamesedwarddd on 2011-07-22
I am having the same issue with my iphone 3gs. I have tried all the codes I could find to use on here, none of them are working. It keeps coming up with the same error message:
"unable to mount iphone
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

I don't know where to go from here. Any help would be greatly appreciated.

---

### Post by Orion13622 on 2011-09-13
Sweet, thank you very much this worked for me perfectly after I did the idevicepair set of instructions through the terminal.  :)   iPhone 4 with iOS 4.3.2 works perfectly under Ubuntu 11.04.  Thank you!

Henry J. Anderson II
APS Dreamworks, Inc.

---

### Post by Ecicoder on 2011-09-24
I have all of the most updated programs and my iPod touch (4g) is not mounting with the debus error my files can be read in Shotwall but nothing else works with the iPod

---

### Post by wolfen69 on 2011-09-24
> **Ecicoder said:**
> I have all of the most updated programs and my iPod touch (4g) is not mounting with the debus error my files can be read in Shotwall but nothing else works with the iPod

Have you tried gtkpod?

---

### Post by gr1603 on 2011-09-27
I have got an Iphone 3G, jailbroken, OS 4.2.1, the device seems to be recognized by the system although no Iphone icon shows up. I have tried all of your suggestions and action but all of them failed.
If I run "ideviceconfig" I got all my Iphone data and even if I run "lsusb" my Iphone turns up to be connected but I cannot see it in "Computer" or "/media". Any suggestions?

Ps: Sorry for my English but I am not a native speaker of it.

---

### Post by gr1603 on 2011-09-28
This worked for me even though I don't know how much the solution of the issue has depended on that:

- I plugged my Iphone in before restarting my Pc with a 10.04 Lucid live Cd. The Operating System, although did recognize the device, didn't mount it.
Then, I restarted my Pc without the live Cd and the Iphone's icon showed up again. At that point I didn't manage to get my Rhythbox program to "see" my Iphone. I simply uninstalled the program and installed it again. Now all seems to work fine. I hope that even this solution helps someone else. ):P

---

### Post by d4m1r on 2011-10-21
> **zero13th said:**
> ```
 

sudo add-apt-repository ppa:pmcenery/ppa  
sudo apt-get update  
sudo apt-get dist-upgrade 

```these steps are working for me

Worked like a charm! iOS 4.3.2, iPhone 4, Natty 11.04...

---

### Post by DaveBooth on 2011-10-23
I can get the ipod to mount, opens in Rythmnbox, drag the track over, but they don't actually move onto the ipod

I think it maybe a permissions issue

ipod touch 4.2.1 and 10.04 lucid

Help

Dave

---

### Post by d4m1r on 2011-10-23
> **d4m1r said:**
> Worked like a charm! iOS 4.3.2, iPhone 4, Natty 11.04...


Bad news....after a reboot, it doesn't mount again (same -12 error) :( Repeating those commands in terminal doesn't fix the issue this time around....Advice?

---

### Post by doogiekd on 2011-12-17
hi friends, 

well, this is interesting... i finally got my ipod touch to mount correctly by doing the following:

1. plug in your iphone/ipod touch

2. let all of the boxes come up (usually error boxes) don't close any boxes until they have all finished opening.

3. close all boxes that have appeared after plugging in iphone/ipod touch.

4. open the file manager you usually use (nautilus for ubuntu, pcman for lubuntu).

5. in the left menu list, you should see two items listing your device with an iphone/ipod icon. these two will be:

 "iphone" (or "ipod touch") 

&

"document" (with an iphone icon next to the listing.

6. right click "document" and select "unmount"

7. right click "iphone" and select "unmount"

8. wait about ten seconds.

9. right click "iphone" and select "mount"

10 right click "document" and select "mount"

11. at this point the iphone or ipod touch should be mounted correctly.

12. you may have to repeat steps 6.7, 8, 9 & 10 several times before this method works - it should work within 5 attempts.

hope this helps -

---

### Post by NadirPoint on 2011-12-17
> **doogiekd said:**
> 12. you may have to repeat steps 6.7, 8, 9 & 10 several times before this method works - it should work within 5 attempts.
Well OK, but sorry I'm not going to ever characterize anything that takes repeating as "works."  If doesn't operate as advertised the first time every time, then it doesn't "work" in my book.

---

### Post by NadirPoint on 2011-12-17
> **Caldur06 said:**
> I came home tonight and my computer isn't even recognizing my iPhone when I plug it in. So now I've got an iPhone with no music and an OS that's oblivious to it. >_<
You can rest assured that as long as Apple and Microsoft are all together in bed with iTunes/OSX/IOS/and Apple hardware extending their fingers deeply embedded into your wallet, you will always face one or another variation on this theme while hosting some related system(s) on Linux.

---

### Post by lemuelbeam on 2012-02-24
I found that simply putting the iphone into recovery mode solved all my syncing issues..:o


> **jamesedwarddd said:**
> )"

I don't know where to go from here. Any help would be greatly appreciated.

---

### Post by gwm on 2012-03-11
Hi,
Recently, both my iPad 1 and a Samsung tablet (10.1" I think) have been failing to mount on my Ubuntu 11.10 (32 bit). It didn't even seem to recognise them. I have just tried d4m1r's fix, given earlier in this thread and it is working for me too. but now I have added what is for me, an unknown repository and upgraded some stuff with I don't know what. I hate fixing things when I don't know what I've done. Anyway, here is his fix again.
```
sudo add-apt-repository ppa:pmcenery/ppa  
sudo apt-get update  
sudo apt-get dist-upgrade
```
I don't know what it did other than fix my problem with both devices.
Thanks d4m1r!

---

### Post by gwm on 2012-03-11
Oops,
I just quoted d4m1r'a post numbered #208 but I hadn't read as far as post #210. I haven't got to reboot yet. I wonder if this fix will go the same way for me as it did for him?

---

### Post by gwm on 2012-03-11
Good news! :)
I rebooted, with the iPad still plugged in mind you, and it mounted immediately!
As Yogi Bear used to say (100 years ago) . . . Yaba daba dooooo!

---

### Post by d4m1r on 2012-03-11
> **gwm said:**
> Hi,
Recently, both my iPad 1 and a Samsung tablet (10.1" I think) have been failing to mount on my Ubuntu 11.10 (32 bit). It didn't even seem to recognise them. I have just tried d4m1r's fix, given earlier in this thread and it is working for me too. but now I have added what is for me, an unknown repository and upgraded some stuff with I don't know what. I hate fixing things when I don't know what I've done. Anyway, here is his fix again.
```
sudo add-apt-repository ppa:pmcenery/ppa  
sudo apt-get update  
sudo apt-get dist-upgrade
```I don't know what it did other than fix my problem with both devices.
Thanks d4m1r!


You're welcome! And yep, it is still working for me as well, iOS 5 (iPhone 4) and Ubuntu 11.10 (32 bit) :D

---

### Post by i_TheDevil_i on 2012-03-11
> **gwm said:**
> Good news! :)
I rebooted, with the iPad still plugged in mind you, and it mounted immediately!
As Yogi Bear used to say (100 years ago) . . . Yaba daba dooooo!

*terribly sorry for offtopic*
it was Fred Flintstone (The Flintstones) saying it. =))

---

### Post by neptune on 2012-03-15
> **d4m1r said:**
> You're welcome! And yep, it is still working for me as well, iOS 5 (iPhone 4) and Ubuntu 11.10 (32 bit) :D


Getting these errors when doing apt-get update


```
W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

```

---

### Post by d4m1r on 2012-03-15
> **neptune said:**
> Getting these errors when doing apt-get update


```
W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

```

Seems like the files are missing...wait a day or 2 and try again. Hopefully they were just down when you were trying to download them. Worst case = they've been removed.

---

### Post by linuxmatt7 on 2012-05-06
Apple has locked their iOS operating system up again for iDevices. I have this same problem with my iPod Touch. Their is a simple fix. Downgrade your iDevice back to iPhone OS 3.1.2. If you didn't save your SSH blobs than you are almost out of luck. If not Jailbreak your iDevice, and download iFile, and Terminal. It should show up on Linux.

---

### Post by d4m1r on 2012-05-08
Just for confirmation, it is still possible to mount your iOS 4.x or even 5.x iDevice under 12.04 Ubuntu as long as you have iFuse and libimobiledevice installed :D

---

### Post by RicSG on 2012-08-05
Hi to everybody, 
I installed ubuntu 10.04 as single boot on my MacBookPro3.1 and all is gone right.

The only problem I have is to mount the iPod Touch. When i plug the usb  the device start to recharge while, linux do not recognize its  presence.

I also used: lp-ppa-pmcenery/lucid; the pachage istalled from this source are:

gvfs
gvfs-backends
gvfs-bin
gvfs-fuse
ifuse
libgpod-common
libgpod4
libimobiledevice1
libplist1
libusbmuxd1
usbmuxd

Do you have any suggestion?

---

### Post by d4m1r on 2012-08-05
What version of iOS is it running? Also, any reason you went with 10.04 specifically? If you want better community support, I'd recommend reinstall with 12.04 LTS instead.

---

### Post by RicSG on 2012-08-06
The version I run is 4.2.1. I use the 10.04 specifically because I use the computer mainly for work and our 'boss' prefer we use this version. So I can not update my system to 12.04.

---

