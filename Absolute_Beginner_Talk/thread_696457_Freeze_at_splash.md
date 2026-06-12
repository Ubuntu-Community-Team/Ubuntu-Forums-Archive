---
title: "Freeze at splash"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by andyGILL on 2008-02-14
It's been fine for a week but now it gets to the splash and the progress bar doesn't move, then it goes to a blank screen with a blinking underscore.

I have no idea what to do, plz help :(

---

### Post by oedha on 2008-02-14
what did you do at the last time ?
what if sudo dpkg-reconfigure -phigh xserver-xorg
from terminal ?

---

### Post by andyGILL on 2008-02-14
I was installing Qemu when it froze.  How do I get to terminal?  The progress bar at the splash doesn't even move.


Sorry I'm a super noob.

---

### Post by kesman on 2008-02-14
Disable the splash and quiet options from grub menu. Hit ESC to access the menu, then press E to edit the selected boot option, and remove the words quiet and splash from the end of the line. Also do this in the /boot/grub/menu.lst -file. Now you'll be able to see what happens during the boot.

---

### Post by oedha on 2008-02-14
or...when it freeze....you can press ctrl+alt+F2 
to bring you to the console

---

### Post by andyGILL on 2008-02-14
Okay I will try those.  I think I might have done something to a header file too when I was following some tutorial but I don't remember exactly.

---

### Post by andyGILL on 2008-02-14
I removed quiet (there was no splash) and it still got to the screen with the progress bar and froze before making any progress.  I tried pressing ctrl alt f2 and nothing happened, maybe because I have wireless keyboard/mouse?

---

### Post by kesman on 2008-02-14
Try starting with recovery mode and edit the /boot/grub/menu.lst so that there is no splash or quiet in the end of the starting line. It's found from the very end of the file.

---

### Post by oedha on 2008-02-14
mm...i could be.....i am not really sure about that......sorry :(

---

### Post by andyGILL on 2008-02-14
> **kesman said:**
> Try starting with recovery mode and edit the /boot/grub/menu.lst so that there is no splash or quiet in the end of the starting line. It's found from the very end of the file.

I hit escape durin grub and it had a recovery mode so I went to that.  It said a bunch of stuff, ending with:
[ 63.645263] sd 9:0:0:0: Attached scsi generic sg4 type 0


and then I can type and stuff :\

no gui though.

---

### Post by oedha on 2008-02-14
you can type now....:)
what if you type post #2

---

### Post by andyGILL on 2008-02-14
> **oedha said:**
> you can type now....:)
what if you type post #2

Nothig.. it just gives me another line, no response to tell me if anythin even happened.

:\

---

### Post by andyGILL on 2008-02-14
Help please :(

---

### Post by andyGILL on 2008-02-14
Ubuntu has been running fine for a week but now it gets to the splash and the progress bar doesn't move, then it goes to a blank screen with a blinking underscore.  When I go to recovery mode it says a bunch of stuff and then gives me a empty line with a blinking cursor where I can type.  When I hit enter it doesn't tell me anything (if I entered a valid command, if it did anything).

I tried throwing in the liveCD but it only loaded up to the progress bar again.  The orange progress bar bounced back and forth for a few seconds and then once again gave me a blank screen with a blinking underscore.

Is there any way for me to roll back the system a day or something?  Is it hardware?

---

### Post by randy78 on 2008-02-14
> **andyGILL said:**
> Ubuntu has been running fine for a week but now it gets to the splash and the progress bar doesn't move, then it goes to a blank screen with a blinking underscore.  When I go to recovery mode it says a bunch of stuff and then gives me a empty line with a blinking cursor where I can type.  When I hit enter it doesn't tell me anything (if I entered a valid command, if it did anything).

I tried throwing in the liveCD but it only loaded up to the progress bar again.  The orange progress bar bounced back and forth for a few seconds and then once again gave me a blank screen with a blinking underscore.

Is there any way for me to roll back the system a day or something?  Is it hardware?

When this happens to me, I just restart, boot into recovery mode (Press escape to enter grub when directed to) and let it load until a prompt comes up (root@Ubuntu, yours may vary)...

Then I type: 
startx
and then press the ENTER button on the keyboard

Then after the desktop completely loads, I restart the machine and it's magically fixed.

I don't know what's happening or why it works, but it just does...

Did you install with the REGULAR Ubuntu iso?

Take Care

---

### Post by andyGILL on 2008-02-14
When I go to recovery mode it loads a whole load of stuff, I have no idea what, I'll type out the last few lines:

[ 51.780111] scsi 2:0:0:0: Direct-Access  Brother MFC-240C 1.00 PQ: 0 ANSI: 2
[ 51.839081] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[ 51.839149] sd 2:0:0:0: Attached scsi generic sg4 type 0

It's been sitting like that for 5 minutes, is it still loading?  It doesn't say root@Ubuntu or anything =|

And yeah it's regular 32-bit Ubuntu 7.10

---

### Post by kesman on 2008-02-14
Do you have an scsi removable disk installed? If you do, try removing it. This may mean any external hdd's, usb flash memory or memory sticks. Remove all of them and try bootin again.

---

### Post by randy78 on 2008-02-14
> **andyGILL said:**
> When I go to recovery mode it loads a whole load of stuff, I have no idea what, I'll type out the last few lines:

[ 51.780111] scsi 2:0:0:0: Direct-Access  Brother MFC-240C 1.00 PQ: 0 ANSI: 2
[ 51.839081] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[ 51.839149] sd 2:0:0:0: Attached scsi generic sg4 type 0

It's been sitting like that for 5 minutes, is it still loading?  It doesn't say root@Ubuntu or anything =|

And yeah it's regular 32-bit Ubuntu 7.10

Yeah, it takes a while, especially if you have an older machine, but it shouldn't take too long... it basically loads everything and is checking it for inconsistencies.

As Kesman said, try removing any external peripherals that might be plugged in, and try it again.

---

### Post by rkd on 2008-02-14
You said you just tried the Live CD and it shows the same problem.  Did the Live CD work before? Did you install from the Live CD?

If yes, then it seems as if some hardware change has occurred that keeps Ubuntu from booting properly.  It can't be a software change because booting from the Live CD isn't affected by what software is on the hard drive.

Can you think of any hardware change you made just before the problem started?  Connected something new? Disconnected something?

Could it be low batteries in the wireless mouse or keyboard?

---

### Post by andyGILL on 2008-02-14
I disconnected all of my USB drives and tried booting up normal, in recovery mode, with liveCD, and liveCD with safe graphics and every time I get to a blank screen with a blinking cursor where I can't type.

The LiveCD worked before, I tested it for errors before I used it the first time and it ran fine.  It ran fine on 2 of my friends' computers too.  I don't think it's the CD, I'm sure it has to be my system or the OS.

---

### Post by rkd on 2008-02-14
Did you try fresh batteries in the wireless keyboard and mouse?

---

### Post by andyGILL on 2008-02-14
No, what difference would that make?  I will try it now.

I can't think of what would cause the problems.  I installed Nexuiz and Qemu after doing a system update.  A few minutes later my computer froze and now it has been like this for 2 days :(

---

### Post by rkd on 2008-02-14
I don't know that it will make any difference, but if the batteries are low, that might make communication with the computer act just like flaky hardware and cause the operating system to misbehave.  Or not.

---

### Post by andyGILL on 2008-02-14
Switching batteries didn't do anything.  Right now the only things plugged in are: Wireless receiver, monitor,  power, and sound.

Is there anything else I can do to get my system working?  This is so gay cause I just got it out of repair last week.  **** >: (

The progress bar always moves 1/2" before it switches to the black screen with the blinking cursor.  Does that mean anything?

The forum thread I've read usually talk about a configuration file having the wrong video hardware config or something, I have an 8800GTS if that helps at all.  Is there anything I can do?

---

### Post by rkd on 2008-02-14
From what you describe, your problem is occurring long before the xorg.conf file comes into play. It is failing rather quickly if the progress bar moves that little before the boot dies.

You said the computer was in for repair a week ago. Maybe whatever was repaired has failed again (the replacement may not have been good and failed after just a week). Or maybe some other component failed (is the computer getting old?). Or maybe some connector wasn't seated firmly and has worked loose.

It might be useful to run the memory test from the Live CD. It is near the bottom of the boot menu. If that runs, it shows that a bunch of things are working, at least to some degree. I don't know much about the memory test, but I have a feeling that if it doesn't show an error within a couple of minutes, it probably won't find any problem.

You could try to check the CD for defects again. They do sometimes go bad after a while.

If the memory test and the CD check are both okay, try the second boot option -- starting in safe graphics mode. I don't know what it does differently, but the option is there and I can't think of much else to try. If the Live CD works in safe graphics mode, then we can inquire what it does differently and that may lead to the answer to your problem. 

I doubt it is worth trying any of the special boot options at the bottom of the boot menu. Those are to adjust Ubuntu to hardware that was designed a bit differently than usual, but your hardware worked before without those adjustments, so it doesn't seem likely they'd be needed now.

If the Live CD fails the same way in safe graphics mode, we won't have learned anything, and I'd guess it would be time for another trip to the repair shop. But maybe someone else will have some ideas.

---

### Post by confused1 on 2008-02-14
I have been having the same problems too. I have tried Live CD and Alternate CD.
I am putting Ubuntu on an older system, so what I have done is  
I have swapped CD ROM drives putting in a newer one in the older system. I redownloaded Alternate CD and I burned with Nero 6.
And, so far so good. I get all the way to the partitioning screen and I get a message about no root files.
I have two hds, one 120GB with WinXP on it  and another 20GB that I have partitioned with EXT3 and a swap file.
heres the screen 
                                       PARTITIONING METHOD
Guided - Resize IDE1 master  partition #1(hda1) and use freed sp
Guided- use entire disk
Guided- use entire disk and setup LVM
Manual
IDE1 Slave hdb 20GB
#3 Primary  1.6 GB  F swap  Swap
#2 Primary  17.3 GB  K ext3   /media/hdb2
#1 primary   1.2 GB   Kntfs

Now I'm not sure which way to go?
sure could use some help:confused:

---

### Post by andyGILL on 2008-02-14
> **rkd said:**
> From what you describe, your problem is occurring long before the xorg.conf file comes into play. It is failing rather quickly if the progress bar moves that little before the boot dies.

You said the computer was in for repair a week ago. Maybe whatever was repaired has failed again (the replacement may not have been good and failed after just a week). Or maybe some other component failed (is the computer getting old?). Or maybe some connector wasn't seated firmly and has worked loose.

It might be useful to run the memory test from the Live CD. It is near the bottom of the boot menu. If that runs, it shows that a bunch of things are working, at least to some degree. I don't know much about the memory test, but I have a feeling that if it doesn't show an error within a couple of minutes, it probably won't find any problem.

You could try to check the CD for defects again. They do sometimes go bad after a while.

If the memory test and the CD check are both okay, try the second boot option -- starting in safe graphics mode. I don't know what it does differently, but the option is there and I can't think of much else to try. If the Live CD works in safe graphics mode, then we can inquire what it does differently and that may lead to the answer to your problem. 

I doubt it is worth trying any of the special boot options at the bottom of the boot menu. Those are to adjust Ubuntu to hardware that was designed a bit differently than usual, but your hardware worked before without those adjustments, so it doesn't seem likely they'd be needed now.

If the Live CD fails the same way in safe graphics mode, we won't have learned anything, and I'd guess it would be time for another trip to the repair shop. But maybe someone else will have some ideas.

Hmm, it was in repair cause it wouldn't load the OS (in this case it at least loads the screen with the progress bar and Ubuntu logo).  All they did wasa remove my IDE controller that I was using to connect my IDE hard drives and connect them directly to the motherboard's 2 IDE connections.  Then they removed the IDE DVD drive and threw up a SATA one.

I'm gonna try the memory test now, but when I got it repaired they ran tests too and found no problems.  I've also tried booting in graphics mode before but I will try that again too.

If I did end up just corrupting some OS files, what are my options?

When I do recovery mode the last 5 or so lines are:

[ 71.410168] Attempting manual resume
kinit: No resume image, doing normal boot...
Done.
[ 71.421714] EXT3-fs: INFO: recovery required on readonly filesystem.
[ 71.421761] EXT3-fs: write access will be enabled during recovery.
[ 71.460173] kjournald stating. Commit interval 5 seconds
[ 71.460176] EXT3-fs: sdc1: orphan cleanup on readonly fs

and it doesn't change.  I get a blinking cursor and I can type but I get no response.

---

### Post by rkd on 2008-02-14
confused1:

It is better not to hijack another's thread -- you are past the problem that was like this one and now are asking about a different question.  I'll answer here, but next time you have a question, it probably would be best to start a new thread.

It seems that you want to leave Windows on the first disk and use the second disk for Ubuntu, but I don't know what you want the NTFS partition on the second disk for. 

To get Ubuntu onto that second disk, choose the Manual option. On the next window, it will list the partitions on the disk. Click on the ext3 partition then click the Edit partition button. On the pop-up, change the mount point to "/" (should be the first option). Click the OK button. Back in the  partition list, put a check in the box under Format? on the line for the ext3 partition. You shouldn't have to do anything more. Click the Forward button to go on to the next window of the install setup.

---

### Post by rkd on 2008-02-14
Do the CD test, too. They DO go bad sometimes.

It seems a bit odd to me that the computer had an add-on IDE controller and wasn't using the onboard IDE ports. Do you know the history of that? Could it be that the onboard IDE ports caused some problem in the past and the add-on IDE controller was put in because of that?

Tests often don't show up problems, but they are worth trying for the occasional time when they do point directly to a problem.

Let's see what the memory test and CD test show. When you mentioned booting in graphics mode, did you really mean safe graphics mode? If you already tried that and it failed, no point trying that again.

---

### Post by andyGILL on 2008-02-14
> **rkd said:**
> Do the CD test, too. They DO go bad sometimes.

It seems a bit odd to me that the computer had an add-on IDE controller and wasn't using the onboard IDE ports. Do you know the history of that? Could it be that the onboard IDE ports caused some problem in the past and the add-on IDE controller was put in because of that?

Tests often don't show up problems, but they are worth trying for the occasional time when they do point directly to a problem.

Let's see what the memory test and CD test show. When you mentioned booting in graphics mode, did you really mean safe graphics mode? If you already tried that and it failed, no point trying that again.

I finished the CD test and it passed fine.

The IDE controller was added by me when I realized my old storage drives were IDE and my parents had bought me a computer with a SATA mobo.  Nothing is wrong with the mobo that I know of.

Yes I did mean safe graphics mode heh.

Do any of those messages from recovery mode mean anything?

---

### Post by rkd on 2008-02-14
If the motherboard is SATA and had no place to plug in the IDE drives, forcing you to get an add-on IDE controller, how was the repair shop last week able to take out the add-on IDE controller and plug your IDE drives into the motherboard? That might not be important to understand your problem, but it shows that I'm confused about your hardware configuration, which might make me overlook something important.

The last few messages you saw in recovery mode occur right about the time the boot is done with the preliminaries and is starting things up in earnest. Something that is getting started at that point is going horribly wrong and killing everything.

An interesting experiment would be to boot in recovery mode four or five times and see whether the last few messages are exactly the same each time, or does it fail at different points each time. If it stops at different points each time, the problem might be a flaky power supply -- they can cause weird problems. But that wouldn't be definite. The quickest way to find hardware problems is to swap in known-good components and see when the problem goes away. That's not easy for an individual to do.

Since I'm confused about your hardware, how about describing what it is? Maybe something will trigger an idea.

---

### Post by andyGILL on 2008-02-14
The mobo had 2 IDE inputs that the tech support didn't tell me (my mom had no idea what the specs of the hardware were).

Restarting it in recovery a few times is a cool idea, I will try it after dinner.

My system specs are

Intel Core 2 Duo E6600 Dual Core Processor LGA775 Conroe 2.40GHZ
ASUS P5B ATX LGA775 Conroe 965P DDR2 PCI-E16 3PCI-E1 3PCI SATA2 Sound GBLAN Motherboard
OCZ Gold XTC PC2-6400 2GB 2X1GB DDR2-800 CL5-5-5-12 240PIN DIMM Dual Channel Memory Kit
BFG GeForce 8600GTS OC 710MHZ 256MB 2.0GHZ GDDR3 PCI-E Dual DVI-I HDCP HDTV DIRECTX10
Western Digital Caviar SE16 250GB SATA2 7200RPM 16MB 8.9MS Hard Drive
Pioneer DVR-112D Black DVD-RW 18X6X18 DVD+RW 18X8X18 DL 10X SATA
Arctic Cooling Freezer 7 Pro LGA775 2500RPM 45CFM
Corsair HX520 CMPSU-520HX 520W ATX Triple 12V 40A Continuous 24PIN ATX Modular 120MM Power Supply

I think it might be the power supply because it only came with one power cable that is being used to run all of the hardware.  ******* modular power supply.

---

### Post by rkd on 2008-02-14
The power rating of that power supply seems generous enough for your system, assuming it is operating up to spec, but I don't actually know the power needs of that motherboard and video card.  Have you checked what the manufacturer says they need and the total is well under the power supply's capacity? 

Does that motherboard have an extra power connector that isn't being fed? How about the video card -- is it one that has an extra power connector and if so, are you feeding it? Those are potential ways something might be underpowered.

Before buying any new components, go over the system to make sure all the cables are properly plugged into their connectors and remove and replace the video card, to make sure it is seated properly in its connector.  Sometimes it is the little things that cause trouble.

If you decide to try swapping in new components, I think the power supply would be the first thing to try, then the video card.  You don't have to put in the same model of video card. Trying an inexpensive card should be good enough to tell whether the existing video card is causing problems.  Of course, an inexpensive video card probably would draw less power, so if replacing the video card fixed the problem, that doesn't necessarily mean the original video card is bad.

I didn't see any IDE disks in the list you posted. Have you taken them out of the computer for the moment?

---

### Post by andyGILL on 2008-02-14
No they're in as storage drives and they never caaused any problems.  I couldn't find any invoices for them in my email and I can't remember what their manufacturer is.

I will try re-connecting devices and I will also see if I can get more power cables.

---

### Post by andyGILL on 2008-02-14
I restarted 3 times in recovery mode recording the last few lines each time:

1st restart
[ 50.838946] sd 6:0:1:0: [sdc] Write Protect is off
[ 50.838957] sd 6:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 50.838958] sd:<7>ext3_orphan_cleanup: truncating inode 3457083 to 0bytes
[ 50.860224] sdc1
[ 50.860287] sd 6:0:1:0: [sdc] Attached SCSI disk
[ 50.860308] sd 6:0:1:0: Attached scsi generic sg3 type 0

2nd restart
[ 43.380352] sd 6:0:1:0: [sdc] Write Protect is off
[ 43.380363] sd 6:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 43.380364] sd:<7>ext3_orphan_cleanup: truncating inode 3457083 to 0bytes
[ 43.402387] sdc1
[ 43.402592] sd 6:0:1:0: [sdc] Attached SCSI disk
[ 43.402822] sd 6:0:1:0: Attached scsi generic sg3 type 0

3rd restart
[ 40.443381] Attempting manual resume
kinit: No resume image, doing normal boot...
Done.
[ 40.455898] EXT3-fs: INFO: recovery required on readonly filesystem.
[ 40.455945] EXT3-fs: write access will be enabled during recovery.
[ 40.493608] kjournald stating. Commit interval 5 seconds
[ 40.493658] EXT3-fs: sdc1: orphan cleanup on readonly fs

---

### Post by rkd on 2008-02-14
Well, it looks like it is stopping pretty close to the same place each time. I think that doesn't tell us anything definite, unfortunately.

---

### Post by andyGILL on 2008-02-15
I have a couple hours free tomorrow so I'll run the beast down to the repair shop, it should be under warranty now.

---

