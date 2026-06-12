---
title: "GRUB Error 21 = Broke PC"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Village on 2006-11-13
Hello,

I tried installing Ubuntu onto a separate hard drive on my computer, I kept Windows installed on another HDD and all my Windows Docs on a third HDD (a big storage one). 

After the install I was able to get it all working and even got Windows to be the default load. As I want to experiment with Ubuntu, but I'm not ready to jump in fully just yet.

Anyway all was working fine for a short while. And then windows chrased. Now when I switch on my PC I get;

GRUB loading, please wait...
Error 21

This pops up after about 10 seconds. 
Does anyone know what this is and how to fix it? 

If you need more info then please let me know and I'll post it. 

Thanks in a advance.

Village

---

### Post by an.echte.trilingue on 2006-11-13
Grub error 21 means that grub (the grand unified bootloader) is looking for its configuration file on a disk that does not exist.  This may mean that your BIOS is not detecting the hard drive that you put ubuntu on any more...

---

### Post by Village on 2006-11-13
Hmm, ok, 
So do I unplug my Ubuntu HDD and just let it find the old windows one?
Thanks

---

### Post by an.echte.trilingue on 2006-11-14
Nope, because GRUB is written to the MBR one the first disk, its config file is on the second disk.  I would put the windows recovery CD in the drive, boot it, and type "FIXMBR" into the prompt.  That should take care of you.

---

### Post by bulldog on 2006-11-14
> **an.echte.trilingue said:**
> Nope, because GRUB is written to the MBR one the first disk, its config file is on the second disk.  I would put the windows recovery CD in the drive, boot it, and type "FIXMBR" into the prompt.  That should take care of you.

He stated he got windows to boot first,if he's not selecting Ubuntu in GRUB,it implicates his windows hdd is not accessable.

At least that's what I'm reading :D could be totally wrong ofcourse....:cool:

But a crashing windows and disk not existing..............Think you have to buy a brand new hard-disk.
Hope there wasn't important data on it though.

---

### Post by Village on 2006-11-15
Alright,

I was able to put the windows CD in and the boot menu loaded, showing Windows and Ubuntu, with windows to load after 10 seconds, just as before. I was able to load windows, and both my windows HDD's were there, with data on them. So I was able to get at the most important stuff, however as there is about 80Gb of info I haven't backed it all up. That's why I have two HDD's, one for programs and one for data. 

After getting into windows I took the CD out and restarted the PC. Error 21 appeared again. 
Anyone got any ideas how to fix this, keeping the windows CD in the drive doesn't sound like a good idea. 
Thanks

Village

---

### Post by bulldog on 2006-11-15
It's not clear to me at all.

You put in the windows cd and see both Ubuntu and Windows? you mean your GRUB I suppose?
Where is the windows cd needed for,or is it when you start windows from GRUB it only loads with the cd in your player.

Can you boot Ubuntu?

---

### Post by Village on 2006-11-15
What currently happens is. 

I switch PC on, BIOS starts to load, then but before it gets going it pops up with;
GRUB loading, please wait...
Error 21

If I put my Windows XP CD into the drive it does not show the GRUB loading and instead takes me to the GRUB menu. where after 10 secs Windows loads, or I can load Ubuntu if I like (I think). 

Whilst I'm fretting about the broke PC I am glad to hear that I'm not the only one who is stumped.

Thanks for any advice I'm getting worried now. Do you think I need to try and get rid of Ubuntu and reinstall Windows? 

Village

---

### Post by Steve Baker on 2006-11-15
I've had some similar problems recently.  Silly question - how old is the PC?  Maybe a CMOS battery would help.  It could be that the CMOS setup info is being lost/corrupted when the power is off ???  Just tossing out ideas here.  :)  I mean - am I right that you said everything was working then it wasn't?

---

### Post by Village on 2006-11-15
Computer is now 4 years old. 

It was working in the sense that I had only switched it on/off a couple of times after installing Ubuntu and getting Windows to be the default OS. 

I was then using Windows and it crashed (nothing out of the ordinary there). 
When I switched it on again it popped up with Error 21. 

If I was to try and remove Ubuntu, and reinstall Windows what would I have to do, any ideas before I start trying to unplug the Ubuntu HDD and format C and reinstall? 

Thanks,

Village

---

### Post by Steve Baker on 2006-11-15
Before doing anything drastic I would, very seriously, replace the battery.  4 years is about their life expectancy.

It isn't a big deal or expense - I bought one at my local CVS and it was only a few dollars.  If all else fails - Amazon.com.  Make sure you know which battery you need.

---

### Post by Village on 2006-11-16
I'll get hold of a new battery, I just think its surprising that it would start to cause problems now, just after I've been playing around with the GRUB and other parts of my computer. 

Village

---

### Post by Village on 2006-11-17
I just thought that I would show everyone what I see when I switch my PC on. see if that helps the situation because I'm still at a loss and now getting desperate. I can't even figure out how to start taking my PC back to before I installed Ubuntu. 

==

ALi RAID BIOS V0.96 (M5283)
(c) ALi Corporation 2003, All Rights Reserved. 
Identifying IDE drives .x.x.x.x

Channel 1 Master: None
Channel 1 Slave : None
Channel 2 Master: None
Channel 3 Master: None

Press Ctrl-A to enter ALi RAID BIOS Setup Utility 

GRUB loading, Please Wait...
Error 21

---

### Post by rabidsnakemonkey on 2006-11-18
I installed ubuntu today.
I put it on a secod hard drive, the first having windows.
It successfully istalled, had me take out the disk, and reboot the system. When it restarted, I got the same error message:
> GRUB loading, Please Wait...
Error 21
I changed my BIOS settings, but i got the same error message.
It may be because my hard drive with ubuntu is in the secondary slave slot, but then it wouldn't have installed it, right?

---

### Post by Village on 2006-11-18
Wish I knew, I'm going to have a play around tomorrow. I'll let you know how I get on. 

Although right now I'm looking at the last resort of re-installing windows and taking Ubuntu off.

Sorry I couldn't be of more help.

village

---

### Post by gn2 on 2006-11-18
If you have access to an external USB hard drive enclosure and another PC, you can easily find out if the drives are functioning and what files are on them.

Are you using RAID?

Are you using SATA IDE or a mix, what type is each OS on?

Have you read this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Error 21 needn't mean the hardware has failed.....

---

### Post by unbuntu kid on 2006-11-18
REINSTALL UBUNTU!
It is that simple!!!!!!!!!!!!!!
I had the same problem!
NO HARD AT ALL TO FIX
Sorry about all of the previous confusion:

---

### Post by ridgeback on 2006-11-18
I had the same GRUB Error 21, and I had to enter the CMOS setup, where my second hard drive was disabled, and change it to the auto setting.  I don't know if you've tried that, but our situations were the exact same, so I think it may help.  Again, go into BIOS settings by hitting Del or whatever the keystroke is on startup, choose the CMOS option (one of the first options on mine) and change whatever hard drive slot your ubuntu drive is on to auto from disabled.  Hope this helps!

---

### Post by Buck2348 on 2006-11-18
I also had the same situation when I installed Ubuntu on my second drive, though it existed from the first--I was unable to boot anything on the hard drives.  I entered the Microsoft Recovery Console from the Win XP CD and ran "fixmbr" (fix master boot record) which enabled Windows to boot again.  I then googled the problem and found the fix ridgeback suggests, which worked just fine, though I think I had to reinstall Ubuntu because I had messed up Grub with the fixmbr command.

Hope this helps.

Buck

---

### Post by Village on 2006-11-20
Ok, for the record:

I've been able to get back into Windows, though Safe Mode and back up what I needed. I've since formatted C drive and reinstalled MS Windows, as I'm still going to need it for things. 

Now I'm going to try and set it all up. Windows as default with a storage Hard Drive and then also have Ubuntu to play around on. 

Wish me luck and thanks for all the help.

Village

---

