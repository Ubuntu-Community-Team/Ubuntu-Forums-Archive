---
title: "Suggested Distribution for 800MHz G4 iMac"
date: 2015-02-15
forum: Apple Hardware Users
---

### Post by Martin_Srensen on 2015-02-15
As Linux newbie, I need a bit of help to cut through the fog.

We have a small "hotel" *) and now need a reception and a simple computer for it. All it needs to do is:

- run our invoicing software (browser-based)
- upload guest details to immigration (browser-based, legal requirement)
- communicate with a scanner/printer
- perhaps email

er, and that is it so far :-) Not very taxing.

As we have an [unemployed iMac]("http://lowendmac.com/2002/17-inch-imac-g4-mid-2002/") I hope to use that, as it is more elegant than a cheap portable and I do not like to throw out working hardware. 

Specs are 800Mhz, 80GB HD, 1GB RAM, 17" screen, Airport card.

What do you suggest, and what should I be aware of?

Thanks, Martin

*) 7 self-catering cottages to be precise.

---

### Post by mörgæs on 2015-02-15
[http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12707046&viewfull=1#post12707046](http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12707046&viewfull=1#post12707046)

---

### Post by Martin_Srensen on 2015-02-15
Wonderful, thank you.

Probably a case of not knowing what to search for in the forum :-/

---

### Post by Martin_Srensen on 2015-02-16
OK, I have now spent 1/2 day mucking about, and I am getting tired and with a headache :-(

Burned the ISO to a DVD, it booted and looked nice, but when I tried to install it hung - and refused to boot from the DVD again. Quite possibly the drive is dirty, but I do not have any cleaner disk around.

So, after looking at my options and available HW*) I have tried to install via a USB stick along these lines: [http://ubuntuforums.org/showthread.php?t=2225846](http://ubuntuforums.org/showthread.php?t=2225846)

I get a "can't find iso" message, obviously I did not specify where to look.

I have of course changed the filename to the one of the downloaded ISO, but I suppose I have to describe the path the USB as well - how to? It is 15 years since I last used command lines much, and I don't think it involved USB.

There may be an easier way forward, suggestions welcome. I do not particularly want to keep the OS X or any data on the machine.

Thanking in advance

Martin

*) I have an FW 10GB iPod but did not find a way forward with that.

---

### Post by rsavage on 2015-02-17
> **Martin_Srensen said:**
> 

I have of course changed the filename to the one of the downloaded ISO, but I suppose I have to describe the path the USB as well - how to? 

No you don't.  That is the beauty of the method.  As long as the partition type is supported is should find the file.  What is your file called, where have you put it on the usb drive, and what command are you using?

---

### Post by Martin_Srensen on 2015-02-17
> **rsavage said:**
> No you don't.  That is the beauty of the method.  As long as the partition type is supported is should find the file.  What is your file called, where have you put it on the usb drive, and what command are you using?

The file is lubuntu-14.04.1-desktop-powerpc.iso and is at the root of the USB, there are no other files on.

I have tried the commands 
[COLOR=#000000][FONT=Ubuntu Mono]live [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]iso-scan/filename=/downloads/[/FONT][/COLOR][/COLOR]lubuntu-14.04.1-desktop-powerpc.iso
and [COLOR=#000000][FONT=Ubuntu Mono]live [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]iso-scan/filename=/[/FONT][/COLOR][/COLOR]lubuntu-14.04.1-desktop-powerpc.iso

I get a looong wait with Lubuntu animation and end up with 

"BusyBox v1.21.1 (Ubuntu 1:1.21..0-1ubuntu1) built-in shell (ash)
…
Unable to find a medium containing a live file system"

Thanks for helping

Martin

---

### Post by rsavage on 2015-02-18
> **Martin_Srensen said:**
> 
and [COLOR=#000000][FONT=Ubuntu Mono]live [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]iso-scan/filename=/[/FONT][/COLOR][/COLOR]lubuntu-14.04.1-desktop-powerpc.iso

That should of worked I would of thought.....I can only suggest that maybe the driver for your usb drive/bridge/whatever is not included in the initial kernel/initramfs.

Clutching at straws, have your tried
```

[COLOR=#000000][FONT=Ubuntu Mono]live [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]iso-scan/filename=[/FONT][/COLOR][/COLOR]lubuntu-14.04.1-desktop-powerpc.iso

```

Also, have you tried an alternative method?  Using dd to 'burn' the ISO onto the usb drive? - [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

---

### Post by rsavage on 2015-02-18
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12707046&viewfull=1#post12707046](http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12707046&viewfull=1#post12707046)

> **Martin_Srensen said:**
> Wonderful, thank you.

Probably a case of not knowing what to search for in the forum :-/

To save you a bit more time, I should point out that that link isn't exactly great.  First it is buried in a 90 page thread which is ridiculous.  Second, it refers to lubuntu/xubuntu 12.04, and if you say you are using that on this forum, then mörgæs will be the first to pick you up and say it is not supported (which is rubbish because 12.04 proper has 5 years of support).  Third, it refers to the nv driver which only works in 12.04, and the links to download the binary are dead.

PowerPC has a wealth of wiki documentation, it is just a pity the administrators of this forum do not support it and prefer to promote their forum instead.

---

### Post by rsavage on 2015-02-18
If you have an ethernet cable, then you can do a netboot (this is what the mini iso does, like mörgæs described) by copying the appropriate files to a hard drive.

---

### Post by rsavage on 2015-02-18
> **Martin_Srensen said:**
> 
Burned the ISO to a DVD, it booted and looked nice, but when I tried to install it hung - and refused to boot from the DVD again. Quite possibly the drive is dirty, but I do not have any cleaner disk around.

The imac g4 700/800 are notorious for the graphics not working.  If it booted once and looked nice, then this could well be a freak event.  You are probably always going to have to use boot parameters to get it working.

---

### Post by Martin_Srensen on 2015-02-18
I tested the drive with a DVD movie and it seemed to work; I then thought I better try another DVD. This time DVD+R instead of DVD-R, and another brand (!)

Whatever, it booted and seemed to install fairly painless - until I got the message [FONT=Helvetica][errno 30] Read-only file system:'target/boot/vmlinux-3.2.0-23-powerpc-smp'[/FONT]
Useful info provided was that it often was due to a dodgy HD. Disk tool claimed smart status was good, but looking into details it had [FONT=Helvetica]Warnings for Reallocated sector count and Current Pending Sector Count. 

Most likely due to ancient disk (~ 2002?)

So, next step is to try to put in a slightly newer (2007) disk and see if it helps.

Funny how these things become a challenge :-)

Thanks

Martin

PS: All colours ok so far.[/FONT]

---

### Post by rsavage on 2015-02-18
Okay that is good about the colours and graphics.  It makes it a lot easier for you, believe it or not!  I see here [http://www.everymac.com/systems/apple/imac/imac-g4-flat-panel-faq/imac-g4-video-processor-second-display-non-mirrored-hack.html](http://www.everymac.com/systems/apple/imac/imac-g4-flat-panel-faq/imac-g4-video-processor-second-display-non-mirrored-hack.html) you have a better card than the smaller screen variety, so that explains why it is working.

---

### Post by Martin_Srensen on 2015-02-19
Obviously yes. I swapped the disk (in the end to one I had left over from my Cube), it is similar age but had hardly been used for years. SMART status cleared, so I hope it does the job.

I installed 14.04.1 with default settings and it seems to be running fine, browser being responsive enough. I now have to look at printer/scanner and WiFi dongle, but that may be for another thread if necessary.

I am happy - it is still a quite elegant machine for our reception :-)

If you are in the Algarve I am happy to buy you a beer!

/Martin

---

### Post by Bucky Ball on 2015-02-19
> **rsavage said:**
> ... it refers to lubuntu/xubuntu 12.04, and if you say you are using that on this forum, then mörgæs will be the first to pick you up and say it is not supported (which is rubbish because 12.04 proper has 5 years of support). 

Please check facts. Lubuntu 14.04 LTS is the first Lubuntu LTS release and is supported for three years. Xubuntu LTS is supported for three years, not five. ;)

As for Lubuntu 12.04, please see this:

> Unlike Ubuntu, Lubuntu 12.04 is not a LTS, this version will be supported for 18 months. 

From [here]("http://lubuntu.net/blog/lubuntu-1204-now-available"). Consequently, Lubuntu 12.04 reached end-of-life some time ago.

---

### Post by rsavage on 2015-02-19
> **Bucky Ball said:**
> Please check facts. Lubuntu 14.04 LTS is the first Lubuntu LTS release and is supported for three years. Xubuntu LTS is supported for three years, not five. ;)

As for Lubuntu 12.04, please see this:



From [here]("http://lubuntu.net/blog/lubuntu-1204-now-available"). Consequently, Lubuntu 12.04 reached end-of-life some time ago.

As if I didn't know that.  But telling people not to install Lubuntu 12.04 because it is not supported is poor advice.  Please show me a security update - or any update - to Lubuntu when it was in it's 'supported' period.  All updates have come from the ubuntu core which is supported for 5 years.  Other programs, for example vlc are not part of any *ubuntu, and you could argue are not or ever have been supported, but do you tell people not to install it?  Please, lets be realistic and consistent and have some perspective of what makes up a distro and what the supported tag actually means.

---

### Post by rsavage on 2015-02-19
> **Martin_Srensen said:**
> in the end to one I had left over from my Cube
I'm jealous!  I've always wanted one of those!

> 
I am happy - it is still a quite elegant machine for our reception :-)

I bet!

> 
If you are in the Algarve I am happy to buy you a beer!

One day!

Glad it is working!

---

### Post by mörgæs on 2015-02-21
A year ago we had a lot of posts about Ubuntu 10.04 desktop crashing. Only 10.04 server was supported, and an update to the server broke some functionality on the desktop. 

In spite of warnings people were still using the obsolete desktop but no bug fix targeting the desktop was to be expected. Bug reports in Launchpad got closed as fast as they were opened, as support was out. 

This could happen to Lubuntu 12.04 too and is only one among many reasons not to use abandonware. Lack of security updates to the LXDE packages is another. 

The reason that I linked to a post explaining about 12.04 is not that I recommend this version today. It was meant as an inspiration for how to get 14.04 running. If anyone is able to write a guide for 14.04 I would happily swap them.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by rsavage on 2015-02-21
> **mörgæs said:**
> A year ago we had a lot of posts about Ubuntu 10.04 desktop crashing. Only 10.04 server was supported, and an update to the server broke some functionality on the desktop. 

In spite of warnings people were still using the obsolete desktop but no bug fix targeting the desktop was to be expected. Bug reports in Launchpad got closed as fast as they were opened, as support was out. 

This could happen to Lubuntu 12.04 too and is only one among many reasons not to use abandonware. 

That is not comparable at all.

> 
Lack of security updates to the LXDE packages is another. 

The risk from this is minuscule.

> 
The reason that I linked to a post explaining about 12.04 is not that I recommend this version today. It was meant as an inspiration for how to get 14.04 running. If anyone is able to write a guide for 14.04 I would happily swap them.

Which is exactly my point.  PowerPC has already a good guide - the PowerPCFAQ and KnownIssues pages.  So why link to a post in a 90 page thread?

It's nearly as bad as a 27 page sticky "Where to download Ubuntu for PowerPC and other frequently asked questions".  We've asked repeatedly for a new shorter sticky that doesn't have outdated information in it, that people might actually read.....but have been always ignored by the mods of this forum.  It is very frustrating.

The same thing happened in the wireless section of the forum.  There used to a sticky (created by a mod) that contained the most appalling advice.  A couple of years ago I updated the Broadcom wiki page so that it answered 99.999% of problems.  I pointed out the problems with the sticky to the mod and asked instead they link to the correct wiki page.  Again this was ignored.  The result was that people kept having problems that were answered very poorly in the forums.

I consider every question asked here on the forum a failure of the documentation (or a failure to find the documentation) and I want to drive down the number of questions/threads/problems.  

The mods seem to look at it differently, they want more questions and discussion.  I've come to the conclusion, they're not interested in accurate/concise information.  Consequently, the ubuntuforums has a really bad reputation for the quality of advice in the linux world.  If I search for something on google etc, then the ubuntuforums link is always the last I try.

---

### Post by QIII on 2015-02-21
As it seems the OP was answered and this has turned into a gripe session about the Staff, this thread is closed.

---

### Post by mörgæs on 2015-02-22
Squeezing in a post though the thread is closed.

Rsavage, if a sticky needs replacing then you and everyone else are invited to 

1) post a new thread with enough contents to be considered for a sticky, and
2) post in [Forum Feedback and Help]("http://ubuntuforums.org/forumdisplay.php?f=48") pointing to the thread in 1), explaining why it should be considered. 

Keep focus on today. Referring to what someone did sometime in the past is not the way to go.

---

