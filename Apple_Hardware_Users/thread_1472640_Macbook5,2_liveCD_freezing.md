---
title: "Macbook5,2 liveCD freezing"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by wandaa on 2010-05-04
[SOLVED: don't know how to change the topic... :(]

Hi everyone,

I have tried to install 9.04 on this laptop before, had no luck with that forever ago and just gave up (had the exact same problem back then).

Noticed a while ago that 10.04 is here and now I truly want to get this done. My problem is as follows:

I have a "working" liveCD which I can basically boot into, once I get past the purple screen (not sure what should I call it, doesn't have much on it, some smallish logos at the bottom center of the page) it just gives me a blinking "cursor" ("_") and does not continue after that. CD stops spinning and nothing happens. Just before this blinking "_" appears there is a very small "flash" of some colorful blocks (happened at least a few times, can't notice them everytime) here and there on the screen, relating possibly to a problem with Nvidia (drivers?)?

I have tried going into the boot commands menu or what ever it is called (holding down the shift key) and can get to the point where it asks me do I want have "boot graphics y/n: y" but I get absolutely no input from my keyboard, have also tried a USB keyboard with the same result.

An other, slightly smaller, problem is defragging. My computer is fragmented to bits, and just creating the space for the future install is absolutely impossible at the moment (at least with the boot camp assistant) so need to get this defragmented, any suggestions what should I use to do this? 

My goal would be to have a dual boot of OSX and Ubuntu. My laptop is updated, has the latest firmware of everything and I'm at loss of what the problem could be at this point.

---

### Post by linuxopjemac on 2010-05-05
You are trying something new. There is not yet a lot of documentation for installing Lucid Lynxz on MacBooks. Normally I refer people to the [starting page]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"). But there is not a lot of info about 10.04 yet. So, maybe you can try the advize as given for Karmic MacBook 5,2:

> Basic Installation Instructions

Booting the kernel from the (Live)CD has to be changed. Or else you get a black screen and does nothing at all after 2 seconds of kernel boot. Hit F6 to change the boot options after you selected the language. Then disable acpi enter  acpi=off  in the boot line. I also added,  noapic nolapic irqpoll vga=771 . If you don't want to loose acpi functions you can add this other option  maxcpus=1 .

---

### Post by wandaa on 2010-05-05
Well.... I've gotten it to boot a few times now. Trying to choose to boot into the CD from the OSX "start disk menu" or what ever does NOT work. Choosing it by holding down the option key seemed to not work at first, but then out of good luck it just happened to get through.

I was trying to hold down all the buttons I knew that should/would respond to something and holding down "c" during bootup (AFTER choosing to boot from the CD, as in not just telling the laptop to boot from a CD) seemed to magically get me through. Now I'm stuck with the dilemma of what does this button actually do?!

After choosing which language to use I quickly checked acpi=off and it did boot into the liveCD. I cleared out some space on the disk and have it formatted into free space atm. Just kind of (very) scared to install the OS at the moment due to the fact that I have no clue what is going on when I hold down the "c" button. "It just works" is kind of a scary notion at this point...

And well, aware of being kind of an explorer into this install, and if I find out something credible, will definitely write about it. :)

---

### Post by xouns on 2010-05-05
If I recalled correctly, holding down the c-button just tells the Bios to boot from CD, that's all. Since it's a bootable cd, that works, so you're fine.
[http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.shtml](http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.shtml) Will help you.

I've used the c-key on my girlfriends powerbook when her hdd broke, to get her throught the time when we where waiting for the new one to arrive. I figure it does nothing to the harddisk since it's a live-cd.

---

### Post by xouns on 2010-05-05
By the way, holding down the mousepad button will eject the cd/ dvd from the drive without booting from it. Helped me too.

---

### Post by wandaa on 2010-05-05
Was aware of both of them (and have had to use both of them quite a lot :D). But thanks for the suggestions anyway.

Right now I'm in quite a pickle, this time this might actually be something slightly more serious...

I was in OSX, decided that what the hell! Let's just go for it, let's see what happens. Worst case, gotta reinstall... And want to point out that at this point everything had worked, I had been able to reboot into Ubuntu a few times last night (still not 100% how it happened), repartitioned (AND everything worked afterwards as well.) OSX worked like a charm.

Boot from the disc, get nowhere, yet again... :S

Boot over and over again, nothing. Try going back into OSX and it won't boot there either! After a while of the grey screen showing the apple logo, it just shows a "cancel" logo (O with a dash through it O/ kinda combined... A quick #mac channel query on IRC revealed it to be a possible directory error, can't say since I don't know anything about OSX or macs) and the loading screen just continues forever and ever. Had a nap and it was still doing this. After some time got quite desperate and just tried holding down keys (this is kinda my thing... :D) and held down the shift key to get into safemode (I think/hope. Actually just read about it and it turns out to be booting without the "boot extensions" which would probably mean something along the lines of this problem being caused by rEFIt.) and am here writing this from there.

The LiveCD was booting no further than the very first screen. "ISOLinux, debian (c) blahblahblah..." And no other lines were coming after this. What can cause something like this? No input, no output (besides that), CD stopped spinning after some time. After this trying to boot into OSX seemed impossible as well. Any ideas?

edit/add: The shift key trick does not work every time either. I checked the LiveCD for faults with its built in checker thing and it came back clean. Told me to reset and I did, and the same old problem occured.

---

### Post by agr3 on 2010-05-05
I can confirm that when the 10.04 LiveCD fails to boot, the next attempt to boot Mac OS X can fail with the "is forbidden" symbol (circle-slash) being displayed.

To fix that, reboot again, but this time hold down the four keys Command-Option-P-R simultaneously until you hear the startup chime a second time, then release those keys.  Now the MacBook will boot all the way into Mac OS X again.  (At least, that worked for me.)

Holding down Command-Option-P-R during bootup is sometimes called "zapping the PRAM".  PRAM stands for "Parameter RAM".  It's special RAM that's maintained by your Mac's battery between boots and holds various settings, including info that helps the Mac boot.  So if you ever suspect the PRAM info has gotten corrupted, you can use the keyboard shortcut above during booting to reset the PRAM info back to factory settings.

---

### Post by wandaa on 2010-05-05
> **agr3 said:**
> I can confirm that when the 10.04 LiveCD fails to boot, the next attempt to boot Mac OS X can fail with the "is forbidden" symbol (circle-slash) being displayed.

To fix that, reboot again, but this time hold down the four keys Command-Option-P-R simultaneously until you hear the startup chime a second time, then release those keys.  Now the MacBook will boot all the way into Mac OS X again.  (At least, that worked for me.)

Holding down Command-Option-P-R during bootup is sometimes called "zapping the PRAM".  PRAM stands for "Parameter RAM".  It's special RAM that's maintained by your Mac's battery between boots and holds various settings, including info that helps the Mac boot.  So if you ever suspect the PRAM info has gotten corrupted, you can use the keyboard shortcut above during booting to reset the PRAM info back to factory settings.

Thanks for that key combo, will definitely be important. Since after it fails, it won't work again even with the LiveCD.

I'll report back soon.. Let's see what happens! :D

---

### Post by agr3 on 2010-05-05
I found a bug report posted online complaining that the MacBook 5,x models were unable to successfully boot the 10.04 beta 1 LiveCD.  So maybe that bug didn't get fixed during beta testing -- before the official 10.04 LTS iso was released.  If that's the case, that would explain why we're still having this LiveCD trouble.  We may need to wait for a 10.05 update unless someone has found a workaround.  Is there one?

I'm brand-new to Linux, so I don't know if there's any other way to get Ubuntu 10.04 installed onto a MacBook 5,x laptop if the LiveCD doesn't boot.  Is there?  If someone has found a way, please post the details.

Just as another data point, I was able to boot the PowerPC version of the Ubuntu 10.04 LiveCD on an iBook G4 with zero problems.

---

### Post by wandaa on 2010-05-05
Found out an error message it spews out during boot from the LiveCD (this is during the graphical phase, when it is loading Ubuntu).

Error message goes as follows: [ 73.188007 ] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 8, Type 4, Revision 4)

From what I understand that might/could mean some HW isn't recognized or at least not being supported. What it might be is out of my knowledge.

Anyway, I believe I got it installed, haven't been able to boot into it yet, still have to fiddle around a bit with the MBR, rEFIt and so on.

Never got the LiveCD to boot up without holding the C key down, does anyone really have ANY clue what it might do? :D I mean odd coincidence doesn't exactly satisfy... My guess would be that it skips something, since the loads went WAY faster when I did that as well.

It took a long while before I decided to come to OSX, Linux just wouldn't load and the MBR seemed fine according to rEFIt. Have to try something else I guess...

And just noticed the wiki had gotten a Macbook5,1/Lucid article as well. :)

---

### Post by wandaa on 2010-05-05
Sorry to be posting over and over and over again to this thread. But just here with the answers.

Got it working, am writing this right now from a working install of Ubuntu! *yay*

To get it installed I had to do manual partitioning to get GRUB to install where I wanted it to (not that that matters, I always do manual partitioning... But some kind of a "bug" perhaps? (Me not being able to choose where to install grub since the new partitions hadn't been created yet..)). After getting that done I tried to boot into this from the rEFIt bootloader, which turned out to not work out. Plan B did though, just use the built in bootloader. Jam down the alt button during bootup and choose to boot into "windows" from that.
   At GRUB I had to edit the boot options to add apci=off, still haven't gotten that to stick, but I'll do that an other time.
   To begin with, not much was working, but after a few minutes of updating and upgrading I was up and running...

So my biggest problem by far was getting the LiveCD to just boot up. No clue how or why it was or was not working, but eventually I got it done. Biggest problem was the PRAM being corrupted time after time, and the computer being completely unusable at that point. If anyone is having this problem make sure to check that out.

Next task is to get rid of the useless rEFIt bootloader, I had it installed to fix the MBR issues, which didn't happen. They were configured automagically, no clue by what, when or where, but is just worked. Not sure that installing rEFIt is necessary 
anymore? At least for me it wasn't. Can someone confirm it being useful for something still?

I have a bit of configuring and so on to do, but that's normal. Thanks for all of your quick replies. Does someone know how to set this to being resolved?

---

