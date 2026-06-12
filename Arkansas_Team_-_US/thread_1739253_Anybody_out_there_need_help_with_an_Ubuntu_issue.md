---
title: "Anybody out there need help with an Ubuntu issue?"
date: 2011-04-25
forum: Arkansas Team - US
---

### Post by Drate on 2011-04-25
I'm opening this thread as an invitation for anybody to ask questions and hopefully get the answers they are looking for and with a personal, local touch.

---

### Post by Bobrm2 on 2011-06-05
Well sir, I'm from north of Harriet, Ar. Recently assembled a new computer, that I partitioned  ./  ./Boot ./Data ./swap. All primaries and except for ./  /dev/sda/ ext4.

  After I partitioned the HDD with Gparted and attempted to install Ubuntu 10.10, maybe also tried 11.04 have made startup disks, with new downloads of the respective ISO. Anyway, attempting to install the program all I have now is black screen with a flashing cursor in the upper left (since yesterday).  I can just barely make out "Checking NVRAM" before the BIOS page flashes by.

  I obviously don't have a terminal and don't know how to wipe the hard drive, that's all I can figure to do, but how.

  I take you up on your offer of assistance. It's a good think my hair is only about a 1/2 inch long.

Bob

---

### Post by kwadroke on 2011-06-05
Sounds like GRUB is hosed.

---

### Post by Bobrm2 on 2011-06-05
So, how can I start over? Will resetting CMOS do it?

---

### Post by roadrawts on 2011-06-05
I'm reading the GRUB 2 documentation about this problem but I don't understand it all.  It says to use a LiveCD and pick the Repair of the Computer Boot option with "I want to reinstall the bootloader (Grub2)".  But it looks like an Ubuntu 10.10 function which I don't have (I have Ubuntu 10.04).  I just want to move my Ubuntu partition using GPARTED but will encounter the same problem that you have because Grub wont find the OS. I need some guidance also.

---

### Post by Bobrm2 on 2011-06-05
I've gone back trying to load 10.4 ISO, with no success, and 11.04 won't git pass this black screen with white cursor.  I'm going to see if I can find a way into the "Terminal". Anyone know how, pls speak up.

Bob

---

### Post by Drate on 2011-06-05
Okay, well, first things are first, I don't want to recommend anything that would result in you losing any valuable data, or your existing 1/2 inch of hair, so:

Do you have any valuable data on this computer?  If not, my recommendation would be this:

Don't try to partition the drive manually.  Start with an Ubuntu 11.04 live CD, let it come up into the installer, choose all the default options.

There are sometimes some visual problems at bootup, don't let that bother you too much.  There is supposed to be a fancy boot splash with colored orange dots.  In my experience they are always there on OTHER people's computer, never mine, I've gotten used to it.  It shouldn't take but a minute for Ubuntu to be up at a login screen.

If you DO have valuable data you need to protect, then the first step is going to be making sure that data is backed up.  Let me know where we stand with this and I can make more informed recommendations.

---

### Post by Bobrm2 on 2011-06-06
There is nothing on the HDD. This is brand new install, so anything goes. First, and I don't remember why, the tech at ECS motherboards, had me remove the CMOS battery, and since last evening I learned what NVRAM is, and  that is the flashed message at the bottom of the BIOS screen, (it took a while for me to see the message) "Searching NVRAM". I'm going back and see if the battery is installed correctly and then I'll Change the CMOS header, move from pins 1 and 2 to pins 2 and 3 for ten seconds, and then back to pins 1 and 2, resetting CMOS.
  When I came on the computer, with the HDD not connected to the mother board, and using 11.04 installed on the memory stick all was fine. Realizing that the HDD was not connected is when things began. The GForce memory may be defective and I intend to make sure it is seated correctly.

  Glad to meet you, and appreciate you stepping, I'll be back to you pretty quick.

  Reset the CMOS jumper all appears to be functional. Will install the 11.04 ISO.

Bob R

---

### Post by Bobrm2 on 2011-06-06
Ok, I've set the system, saved and exit, computer rebooted on it's own and I'm back to the           BLACK screen with flashing cursor. My question is this normal on initial setup?

---

### Post by Drate on 2011-06-06
It's not representative of the normal install experience.  It is a normal thing to see when there is no boot device.

I am not sure what led to the resetting of CMOS and whatnot, I don't typically find that those sorts of issues really come up all that often.  But hopefully you are where you need to be now now from a hardware standpoint?  Hard drive connected and all that?

So you are installing from a USB stick?  You will want to make sure booting from USB is enabled in your CMOS.  Sometimes it is by default, sometimes not.  Sometimes it is easy to spot the right options, sometimes it is cryptic and weird.  I personally recommend trying this from a CD simple because it's the most common and thus simplest format.

---

### Post by Drate on 2011-06-06
Roadrawts:  Apologies if you feel you've already given this information, but can you restate for me what you need help with?

What are you trying to do specifically, do you have critical data that needs to be preserved, are there any other details that you can think of that might help in determining the nature of your problems?  And remember!  I can always ignore an irrelevant detail, but I cannot divine an unspoken one.

---

### Post by Bobrm2 on 2011-06-06
All brand new conponents. Unable to install because of "Searching NVRAM" Was unable to get past the BIOS AmeriMega Trends screen. Always stopped and hung up with a Black screen and a flashing white cursor in upper left corner.

   Am able, by changing the CMOS jumpers, Resetting as it were. By moving the jumper on the CMOS header from pins 1 and 2 to pins 2 and 3, waiting ten seconds then returning the jumper to pins 1 and 2 resets everything back to zero. 

  The "error" message says "searching NVRAM". Looking up NVRAM I found that it means "Non Volatile RAM".

  That gets me to where I can press F1 and get where I change the BIOS settings. 

  Correcting and saving settings, exiting program gets me back to a black screen and white flashing cursor. Back to square one. ???

---

### Post by Bobrm2 on 2011-06-06
I re sat the CMOS because I had no way to communicate with the computer, only the black screen/white cursor. At that point all I could do was turn the box off/on. I could hit the front power button for a restart, but it always led me back to Black screen/white button.

  This box is attempting to locate NVRAM, at least that is the message flashed on the bottom of the MEGA-trends banner screen, i.e. "Searching NVRAM".

   Now I am back, by resetting CMOS jumpers, to the American Mega trends screen, where I can enter BIOS setup. i.e. press F1 to enter Setup. How ever until I understand what is causing "Searching NVRAM", I can't make a logical change.

  I don't know what NV(non-volatile) RAM means. Is it on the video card, the mother board etc.

  Have you an inkling as to what this is means "Searching NVRAM)?

Bob

---

### Post by Bobrm2 on 2011-06-06
Maybe this is a little clearer. and from another forum this link helped


1. Reset jumpers on CMOS header, by moving jumper from pins 1-2 to pins 2-3, waiting 10 plus seconds and returning to original position.

Boot and boot stops on the AMEITrends front page, saying use F1 to enter Setup. Also indicating that system clock needs to be reset.

Make time setting changes and pressing F10 to save. Brings me back to a reboot and then the Black Screen with white cursor in upper left of the screen. 

So back to step one ad infinitum

Further:

NVRAM is an acronym for Non-Volatile Random Access Memory. NVRAM is a type of Random Access Memory (RAM) that retains its information when power is turned off. The NVRAM is a small 24 pin DIP (Dual Inline Package) integrated circuit chip and is thus able to obtain the power needed to keep it running from the CMOS battery installed in your motherboard. It keeps track of various system parameters such as serial number, Ethernet MAC (Media Access Control) address, HOSTID, date of manufacture, etc. NVRAM is therefore a type of non-volatile memory that offers random access.

Bad NVRAM

When NVRAM is failing, it generally means that your computer hardware is not retaining the necessary specialized settings that it ought to though the default BIOS settings remain. Since the BIOS relies on the settings stored in NVRAM in order to handle the particular hardware you have, performance may lack in stability. The contents of the NVRAM chip can become corrupted for a variety of reasons:

A failure of the embedded battery. If the battery embedded in the NVRAM chip fails, then this means that your system clock will stop running and important system configuration information may not be maintained.

A failure of the CMOS (BIOS) chip on your motherboard. If the CMOS chip is going bad or is not making proper contact with the motherboard's contacts, then the NVRAM will fail.

When you get an error message about your NVRAM:

You may need to purchase a new CMOS battery at your computer store to replace your current one. It is advisable to have a technician observe the battery first and determine whether you really need a new one.

If the BIOS chip was the problem, then you will need to contact your hardware manufacturer who may give you a replacement chip depending on your warranty. If not, then you will need to replace your motherboard.

You could also try to reprogram the NVRAM chip with a hostid and Ethernet address. You should only attempt to do this if you know exactly what you are doing; otherwise you should seek a technician's guidance.

Maybe this will help, and I will post progress reports.

Bob

---

### Post by Tommy on 2011-06-07
> **Bobrm2 said:**
> I re sat the CMOS because I had no way to communicate with the computer, only the black screen/white cursor. At that point all I could do was turn the box off/on. I could hit the front power button for a restart, but it always led me back to Black screen/white button.

  This box is attempting to locate NVRAM, at least that is the message flashed on the bottom of the MEGA-trends banner screen, i.e. "Searching NVRAM".


One thing I'm not absolutely clear about and I was hoping you would clarify... when and how did it fail? My reading of your initial post was this:

1) Booted the system (Using Ubuntu 11.04?)

2) Used gparted (instead of the Ubuntu installer) to set up a complicated set of partitions on a boot drive.

3) Installed Ubuntu (Did you actually complete this? Were there any error messages?)

4)Rebooted and the screen was mostly black. Now you cannot even boot the system as you did in step 1?

SO Is this correct? Please spell out what steps completed.

P.S.: I have heard of an NVRAM issue in Ubuntu 11.04 where the installer does something weird to the NVRAM and the motherboard has to go in for factory repair, but so far the only systems I have heard of where this happens are late-model Macintosh systems. Just in case you might do a couple of Google searches with your motherboard and Ubuntu NVRAM failure, just in case the bug is biting more than Apples.

EDIT: I think the following is what I had read, and this probably doesn't apply to your situation exactly:

[http://ubuntuforums.org/showthread.php?t=1743664](http://ubuntuforums.org/showthread.php?t=1743664)

and 

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089)

---

### Post by Bobrm2 on 2011-06-07
Let's see since I first posted, we've (motherboard tech and I) have decided that it's not the motherboard. I've installed an old HDD still having XP-Pro formated. It loaded to the point of asking for files. and past the "black screen/white flashing cursor"(BSWFC)
  So, that eliminated the motherboard, also installed an old DVD writer and attempted to load the operating system on to the New HDD, BSWFC once more. 
   Disconnected HDD from motherboard and using a memory stick brought up Ubuntu 10.10 ISO, then reconnected the HDD and got the BSWFC. 
  The HDD is a Seagate Barracuda 7200-12 SATA. The old HDD is WD IDE. Old DVD is IDE. 

  Currently waiting arrival of new Seagate Barracuda, but I not satisfied that I didn't create the problem. This is my first attempt to assemble a computer. There is no Master/Slave on  the new drive as were with the old IDE's. The other header is a Jumper to another HDD, I suppose. Anyone constructive thoughts are appreciated. Now, if I haven't closed the subject, I'll go back and see if I can answer your questions with the hope they may assist in determining the problem.

  "	
Re: Anybody out there need help with an Ubuntu issue?
Quote:
Originally Posted by Bobrm2 View Post
I re sat the CMOS because I had no way to communicate with the computer, only the black screen/white cursor. At that point all I could do was turn the box off/on. I could hit the front power button for a restart, but it always led me back to Black screen/white button.

This box is attempting to locate NVRAM, at least that is the message flashed on the bottom of the MEGA-trends banner screen, i.e. "Searching NVRAM".
One thing I'm not absolutely clear about and I was hoping you would clarify... when and how did it fail? My reading of your initial post was this:

1) Booted the system (Using Ubuntu 11.04?)

2) Used gparted (instead of the Ubuntu installer) to set up a complicated set of partitions on a boot drive.

3) Installed Ubuntu (Did you actually complete this? Were there any error messages?)

4)Rebooted and the screen was mostly black. Now you cannot even boot the system as you did in step 1?

SO Is this correct? Please spell out what steps completed.

P.S.: I have heard of an NVRAM issue in Ubuntu 11.04 where the installer does something weird to the NVRAM and the motherboard has to go in for factory repair, but so far the only systems I have heard of where this happens are late-model Macintosh systems. Just in case you might do a couple of Google searches with your motherboard and Ubuntu NVRAM failure, just in case the bug is biting more than Apples.

EDIT: I think the following is what I had read, and this probably doesn't apply to your situation exactly:

[http://ubuntuforums.org/showthread.php?t=1743664](http://ubuntuforums.org/showthread.php?t=1743664)

and

https://bugs.launchpad.net/ubuntu-re...es/+bug/774089"

----------------------------------------------------------------------------------------
  #1 Never had 11.04 installed, 
  Originally, I Ran Gparted.  I wished the following partitions
    ./      For Security
    ./Home so, I can change with the upgrades, with out so much trouble.
    ./Data   For just that i.e. everything accumulated day to day.
    ./Swap  For system speed.

  This is just a home office situation for my own research about the many subjects I'm interested in, so I think the partitioning will should work my needs? 

  After the partition effort, and I assume it did partition as I desired, I made the attempt to install 11.04. Gparted is an ISO DVD, *remember this it's a clue. I made the attempt to load the Ubuntu 11.04 ISO and got the BSWFC problem.

  Never got the system installed, after many reboots. Finally figured out, that I could CTR/ALT/DEL at system start would get me to "BIOS setup". So, at least I could select hardware position.

2# May be running Ubuntu installer and coming back to partition would be easier, I don't know. It seems easier the way I attempted to do it??

3# as I said never got Ubuntu installed, due to what I believe is a hard ware problem.

4# Disconnect the HDD and use the memory stick I can go on-line wirelessly, gather mail, etc. This by it's self tells me  that the motherboard is not the problem.

   As to NVRAM (Non-volitial RAM), it has something with CMOS time setting. I would change the jumpers on CMOS (motherboard) and restart the box American Mega-trends screen would appear complaining the date/time was incorrect press F1 for setup. I would change the time/date settings F10 (save/exit) reboot ending up at the BSWFC screen, giving me the impression that the battery, or the CMOS chip was bad. Very confusing.

   I'm going back to the links you provided, for another look.
   Hope I haven't muddied the water any further. Thanks for your effort, Tommy.

Bob R

---

### Post by Tommy on 2011-06-08
> **Bobrm2 said:**
>  #1 Never had 11.04 installed, 
  Originally, I Ran Gparted.  I wished the following partitions
    ./      For Security
    ./Home so, I can change with the upgrades, with out so much trouble.
    ./Data   For just that i.e. everything accumulated day to day.
    ./Swap  For system speed.

  This is just a home office situation for my own research about the many subjects I'm interested in, so I think the partitioning will should work my needs? 

  After the partition effort, and I assume it did partition as I desired, I made the attempt to install 11.04. Gparted is an ISO DVD, *remember this it's a clue. I made the attempt to load the Ubuntu 11.04 ISO and got the BSWFC problem.

  Never got the system installed, after many reboots. Finally figured out, that I could CTR/ALT/DEL at system start would get me to "BIOS setup". So, at least I could select hardware position.

2# May be running Ubuntu installer and coming back to partition would be easier, I don't know. It seems easier the way I attempted to do it??


No, the Ubuntu installer can do a pretty complicated partitioning arrangement, and I would actually trust it OVER gparted, as I have had some major bugs bite me in gparted. (I have NEVER had the terminal parted utility cause me trouble, however.)

SO I would recommend booting from an Ubuntu desktop USB stick or CD. The desktop should be completely functional. You can do a simple installation to your hard drive and see whether it reports a problem. You can do the complicated partitioning if you want -- at the point where it suggests what it is going to do to the drive, you tell it you want to do something different and it lets you define and identify all the partitions. (The Ubuntu installer is a front end to the old reliable Debian installer and you can invoke the Debian one instead if you need to but you shouldn't need to.)

A "standard" Ubuntu installation has just a swap and a root partition, but it's common enough to have others too, so the installer can handle those just fine. 

You said you wanted a root partition for "security" but the root filesystem is not optional (the rest of the filesystem attaches to it), so maybe I'm misunderstanding. 

I suggest you just start with the standard installation with root and swap and maybe add a separate data partition on your next installation. If you want to have other OSes on the drive the installer and grub will detect them and leave them alone.

---

### Post by Bobrm2 on 2011-06-08
Tommy,

 I've removed what I believe to be the culprit, the HDD, and await it's replacement, by the end of the week hopefully. Then I view your instruction and have another go at it.
 Going have to get the texts out, I thought that ./  was protection, that ./home was always there to keep me from having the major problems in the past with new releases, anyway looking forward to another challenge. I'll be back.\\

Bob R.

---

### Post by x.algorithm on 2011-06-08
I've had the same problems with windows refusing to install on a particular hard drive.  I stuck it in a linux box that already had an OS setup.  I jumped in the terminal and used partd. I removed the boot sector, deleted all partitions. I then unmounted the drive, shut down (all power) and started again. Went back into term, used partd again, created a partition, formated it the long way, and then put it back in the windows box and windows then installed correctly.  

I have suspicions that the boot-sector wasn't being flushed properly, and therefore not being written properly. 
 
Hope this helps, I'll watch this thread for updates.

---

### Post by Bobrm2 on 2011-06-08
I pulled the HDD, and another is on the way. Little tired now, but what I plan is to stick the Gparted ISO into the new HDD. What I want and correct me if things have changed or I could help myself by doing the partitioning another way. I'd like ./   ./home ./Data and of course the ./swap all /dev/sda1 thru 4.  I'm not the sharpest knife in the box. Appreciate any assistance. This started out as a "Skype" project. Now, I'm not sure that is possible? Anyway I'll have a great computer, to write my Biography on ;)

Bob

---

### Post by Bobrm2 on 2011-06-10
Well the new HDD arrived. I went into setup setting the DVD as 1st boot device, and the HDD as the second.

  I am trying to boot off the 11.04 ISO, not set as a startup disk, just a plain ISO.

  "Reboot and select the proper Boot device, or insert boot media in selected Boot device and press a key."

   Hit "space" bar and the above request is displayed once more??

   HDD is 500 GB SATA Seagate. SATA and motherboard cables connected. Connection to MB is #1 and DVD is #2.

   Must be something in the way BIOS is configured?

---

### Post by Bobrm2 on 2011-06-10
Adding, that I can briefly, on the American Mega Trends screen see that position one is listed as an IDE HDD, NOT a SATA drive?

---

### Post by Bobrm2 on 2011-06-10
I'm just a little red in the face, but a good lesson for all. Just cause a disk has a label, doesn't mean there any data on it.

Thanks for the assistance men, sorry for the false alarm.


Bob R

---

### Post by Drate on 2011-06-10
Apologies for getting side-tracked this week.  I am confused about two things though:

What was the culprit?

And why were you using GParted to partition the disk instead of letting Ubuntu use it's own recommended default? (just curious)

---

### Post by Bobrm2 on 2011-06-10
I think the "culprit" was my thinking that I had a valid ISO. Don't know why I didn't and now it's just water under the bridge.

  As far as the partitioning, I had always, back 8.xx, partitioned my computers that way. Don't know if the habit was developed from "Running Linux" O.Reilly. I'm not sure that I like the fact that there is not ./ ./home etc. But, I'll do some study, or someone will clue me in as to the security features of the newer editions. When did one just install the ISO. You still run sudo, so there is "root" directory I guess. I still GParted in and see how the disk is partitioned, that will solve some things.

  Say, thanks once more. I do appreciate your efforts. Maybe I can be of assistance to someone later down the road.

Bob R

---

### Post by junglecrus on 2011-06-10
My installation hangs at,

kernel_thread_helper

from a cd and a usb stick

---

### Post by Bobrm2 on 2011-06-11
I did a IxQuick search and came up with this link. I think it's a good place to start.

[http://www.absolutelytech.com/2010/11/10/solved-kernel_thread_helper0x70x10-during-ubuntu-boot-process/](http://www.absolutelytech.com/2010/11/10/solved-kernel_thread_helper0x70x10-during-ubuntu-boot-process/)

Bob R

---

### Post by Bravo.I on 2011-06-11
> **Bobrm2 said:**
> Ok, I've set the system, saved and exit, computer rebooted on it's own and I'm back to the           BLACK screen with flashing cursor. My question is this normal on initial setup?

Hi I do use ubuntu 10.04 and to me just before startup the flashing cursor is normal... But its only for a few seconds and then it starts up the graphics and asks me to login so its quite normal to me... Maybe its something wrong with your new computer... Thats usually rare... Or maybe its because if your using a cd the CD is corrupt.

---

### Post by badraven on 2011-08-02
Hello all!  
I am still new to ubuntu I am running Ubuntu 10.04 LTS - the Lucid Lynx  On a Compaq SR1911X AMD64 w/ 1.5gigs mem

I have an issue with the mouse.  I am using a Logitech MX700
It has most of the features available under Windows but lately there is an issue that comes and goes.  Not sure what causes it but it seems to get bad if I have to many programs running.  Doesn't seem to take more than a few though.

When I right click on something and then move the mouse to choose a menu item, the menu disappears.   I can use the down arrow and then hit enter but if I move the mouse, it's curtains for the menu. 

Once this happens you would think it would be that way till I reboot but no, if I am patient, many times it will stop doing this. 

When it happens there is always a tell tail sign, I will right click and nothing happens.  As if the computer is thinking about it, even though there is no audible sound from the hard drive like I have learn to hate under Windows. 

There is one more thing.  Sometimes I go to less than desirable websites that tend to screw windows computers up.  This is one of the motivations for running linux.  I know there is something in the configuration file(s) because something new happens that started a month or so ago.  A screen comes up with a message: something to the effect of do I want to scan the computer.  If not hit C .  The quicker I hit the C the better.  I am pretty sure it is something I picked up and isn't working because this is a linix computer.

I know that makes me a butthole at least on some level but I am being honest here.  Not trying to hide it.


This is really frustrating though and I really don't know where to look for the issue.  I read a book on linux to try and understand more of the inner workings but when I get into the configuration files I gotta tell you, I am still pretty lost.  

Can someone help please?

Jeff
Greenwood Arkansas

---

### Post by Tommy on 2011-08-21
> **badraven said:**
> I am running Ubuntu 10.04 LTS - the Lucid Lynx  On a Compaq SR1911X AMD64 w/ 1.5gigs mem

I have an issue with the mouse.  I am using a Logitech MX700
...
When I right click on something and then move the mouse to choose a menu item, the menu disappears.   I can use the down arrow and then hit enter but if I move the mouse, it's curtains for the menu. 


I think I know what you are describing, but you might want to notice whether it happens more in a particular application or in all applications. It may be a setting with the window manager, or (since you seem to think it might be the mouse) you might try changing the tracking settings to be a little less sensitive. Sorry I can't be more precise but if it's a problem with a particular application you might see if others have complained about that application's menus disappearing.

> 
A screen comes up with a message: something to the effect of do I want to scan the computer.  If not hit C .  The quicker I hit the C the better.  I am pretty sure it is something I picked up and isn't working because this is a linix computer.

Are you describing something that comes up in the web browser, or are you describing the automatic hard drive check that comes up when you start the computer? If it's when you start the computer, just let it complete. It will happen about every 30 times you reboot the computer, or you can turn it off with a setting.

If you are talking about something that comes up when you are running your web browser, you may have a script that's gotten inserted into your browser (because even on a linux computer the browser IS still vulnerable to unsafe practices, such as installing unsafe browser addons). The easiest way is to delete or create a new Firefox profile. There are a couple of ways to do that... a Google search will turn up a couple of ways to delete the profile -- the easiest would be to close FireFox, then rename the ("hidden") .mozilla directory in your home directory. Rename it from ".mozilla" to something like "oldmozilla" and when you start FireFox it will create a new empty one.


P.S.: AS YOU CAN TELL this isn't the forum for QUICK responses -- if you haven't already, use the beginners forum to get faster responses. I will try to watch this one over the next few days to see if you respond.

                  --Tommy in Conway, AR

---

### Post by maroism on 2011-11-13
I'm running 10.10 on a VM running under Windows 7 pro 64-bit, is there an easy way of changing my screen resolution in the grub loader to utilize more of my monitor?  Currently I'm using the 788 parameter on the nosplash line.  I've allocated 2gig of ram and 150gig of dedicated disk space to the Ubuntu VM.

TIA, Mike

---

### Post by StygianAgenda on 2012-02-27
> **Bobrm2 said:**
> Ok, I've set the system, saved and exit, computer rebooted on it's own and I'm back to the           BLACK screen with flashing cursor. My question is this normal on initial setup?

The most likely answer here is actually a BIOS setting afterall.  Grub does not do well with SATA drives that are configured to use AHCI mode.  To eliminate that possibility, check your BIOS to determine if you can change the SATA controller to use 'IDE' or 'Legacy' mode (they're one and the same, but called differently by various CMOS/BIOS manufacturers).

One of my hobbies is installing Linux into anything that will run a kernel.  I also work with Ubuntu, Red Hat, and embedded Linux systems professionally at my day job (Network Systems Analyst), and have had extensive experience in advanced systems integration, such as integrating Active Directory support to Ubuntu systems used for development so that domain users can simply login with their Windows UserID via the built in Microsoft Terminal Services client (this is achieved via xrdp + xinetd + gdm + vnc4server + centrifydc).  

If I might be of further assistance, feel free to contact me via Facebook under the same Username I've posted under here the Ubuntu Forum.

---

