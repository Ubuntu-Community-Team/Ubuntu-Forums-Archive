---
title: "Edgy hangs on 'starting kernel event manager'"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by neslot on 2006-11-02
Got my new HP Pavilion 1GB, nvidia, dv6000z, AMD Turion 64 X2 Mobile LT-56 1.8 GHz.
Tried to load the 64 bit disto via download/write cd but botched the partitioning and fried XP.  so recovered XP then partitioned (correctly this time) with 4G for root, 2 G for swap, and 25G for /home.  Went to the CD again and selected the OEM option (where I partitioned as above).  Install went fine with no complaints.  Went back to windows and it did a chekdisc with no complaints and booted fine.  I shut down and tried to boot edgy but it hangs up at 'starting kernel event manager.'  ](*,) 
I tried nolapic and noacpi but it still hangs the same every time.

Any suggestions?  I searched the board but could find nothing on this subject.

Thanks in advance!
Tony Olsen

---

### Post by SophusL on 2006-11-05
Could it be that it does not hang up completely, but uses a lot of time? On my system(a T41p) the boot is normal until "starting kernel event manager". This takes about 3 minutes, and then the boot proceeds normally again. I don't know what is causing this, but it sure is frustrating.

SL

---

### Post by neslot on 2006-11-05
I waited 20 minutes and it still hung,  Here's what I did to get past it.  Found this on the web from various people.  After grub screen appeared, I hit escape.  Selected the kernel it was going to boot and hit 'e' to edit it.  Then moved the highlighted bar down to the kernel line again and hit 'e' again to edit that.  At the end of the line was 'quiet splash' I took that out and put in "nolapic noapic keybrd=us" without the quotes of course.  
Then I hit 'enter' then 'b' for boot. that worked fine so I went and set up the stuff it wanted then edited the grub menu list by:
sudo gedit /boot/grub/menu.lst
and added that line permanently behind 'splash' I also took 'quiet' out so I could see some action when I hit the power button.  While editing the grub, I did the same thing to the boot safe mode line..


Hope this helps

Tony

---

### Post by bl00dnu7 on 2006-11-07
I have exactly the same problem as SophusL on my thinkpad t40.  I have attached the output of bootchart showing the hang.

---

### Post by SophusL on 2006-11-07
I was not able to solve this problem. Instead I did a fresh install, and now everything works perfectly. The system also seems to be much more stable now. I recommend not using apt-get to upgrade to 6.10

---

### Post by bl00dnu7 on 2006-11-07
I don't really want to do a fresh install... Seems like giving up to me and I'm just too stubborn.  Also have quite a few extra apps and servers etc. installed, which I don't feel like re-installing.

It looks like it freezes when udev starts and then waits for something to timeout, which should provide some clues to someone knowledgeable.  Possibly this thread is in the wrong forum for this level of debugging... :)

---

### Post by neslot on 2006-11-11
I decided to go with dapper, but lost audio in that distro, so went back to edgy and used the noapic nolapic to get booted up.  All was going well, but the USB thumb drive didn't work so went back and tried booting with just 'nolapic' and it hung again so went back and tried 'noapic' only.  Now all is working with no boot issues and no missing components.  After this worked so well, I edited the /boot/grub/menu.lst and added 'noapic' to the boot line so I don't have to edit it on bootup everytime.
code:
> $ sudo gedit /boot/grub/menu.lst
hope this helps anyone with the same set of events.
Tony

edit:
I found that 'quiet' and/or 'splash' also interfered with the usb so have gone back into menu.list and edited those options out.  thumb and external HD are now working after sever boot ups.
Tony

---

### Post by MrGreen on 2007-01-05
My T12 hangs on Kernel Event Manager so far adding your lines has not helped ACPI modules load just before then starts System log manager then locks. ...

I can sometimes log in via recovery .. but its hit and miss 

Any ideas

MrG

---

### Post by wilberfan on 2007-01-26
I've just started having this problem in the last few days...

I used to boot up in about a minute and 15 seconds or so (?), but now there's a big lag at "Starting kernel event manager".

I timed it and it stays there for 53 seconds!

I don't relish the idea of doing a clean install!  (That's *one* of the reasons I wanted to stick with NOT-Windows!)

---

### Post by wilberfan on 2007-01-26
> **wilberfan said:**
> I've just started having this problem in the last few days...

I used to boot up in about a minute and 15 seconds or so (?), but now there's a big lag at "Starting kernel event manager".

I timed it and it stays there for 53 seconds!

I don't relish the idea of doing a clean install!  (That's *one* of the reasons I wanted to stick with NOT-Windows!)

[COLOR="Red"]**SOLVED!! **[/COLOR]  In my case (can't speak for the other folks in this thread) it was (apparently) being caused by a ***failing power supply!***  :shock: 

I booted in verbose mode, and saw something about a USB device that wasn't responding... For some reason, I decided to check the cables on my (internal) hard-drives (don't ask me why).   The computer wouldn't restart after that!!!    

I went out, dropped $90 on a new Antec 500W "Earthwatt", and everything is back to normal--including normal boot-up times!    =D>

---

### Post by Quite Interesting on 2007-01-27
I'm also getting this problem but for me at least it isn't something that happens every time. It happens fairly often on boot and my standard fix is just to restart the computer until I get it to boot. I'll check my power cables later and see if that has any impact on the problems.

---

