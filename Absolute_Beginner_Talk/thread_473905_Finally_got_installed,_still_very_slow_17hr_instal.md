---
title: "Finally got installed, still very slow 17hr install on alternate cd"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by phenn on 2007-06-14
Hi guys, 

I've been looking through for a while trying to find a similar problem to mine but just haven't been successful so I'll have to just post.  I'm pretty much new to linux, I've installed linux in the past and played around with it a little bit but it never really stuck.  Here I am giving it another go. 

When I tried running the live cd it was just incredibly slow, and I really just couldn't install. The machine also gave me an error about gnome daemon not working and how themes etc. might not work.  So I tried the alternate install and it was still VERY VERY slow.  It took me 24 hours to actually get it all done, though that includes sleeping during the partioning so I'm sure it could have been done in less.  No less than like 16 though it was ridiculous.  I put this down to a slow CD rom drive for some reason though I now know this was a stupid assumption.  My CD rom drive is also a dvd/ cdrw drive and the actual cd rom reading was pretty slow I guess but still that's way too long. 

Anyway bottom line even with it on the hard disk now it still crawls along.  Sometimes on loading I get a hardware error about usb_load_firmware not working, and sometimes I don't.  Which boggles my mind, obviously. I still get the same daemons error message and in general it runs unusably slow and really very poorly.  Eventually I am able to shutdown but no joke it takes about 20 minutes from startup to when I can shut it down. 

I'd really like to run this OS so I'm looking for help.

Specs:
AMD Athlon 64 3200+ 2 Ghz processor
1 gig RAM
nvidia GeForce 6600 GT
80 GB SATA hard drive (right now I think the linux partition is around 20 GB)
Dvd/CDRW/CD Rom Drive
USB Microsoft laser mouse
Standard keyboard
onboard sound nforce audio drivers
Wireless Compact G usb card from linksys

And that's all I really know.  If it makes any difference I was going through the BIOS (i didn't build this machine a friend did) and the cdrom/etc. drive is on IDE 0 and the hard drive is on IDE 2.  Both are Master on their respective channels or whatever, I believe.  If that makes no sense I can double check but that's what I remember.  I have very little idea of what this means but sense it might be important.  Or not. 

Thanks a lot for any help.

---

### Post by Seisen on 2007-06-14
It shouldn't have taken you 24 hours to install it on that setup either, I would be checking connections and other things inside the computer to make sure everything is working properly.

---

### Post by drs305 on 2007-06-14
Your specs should get you decent performance and someone on this forum will help you get it from your machine. One thing that will eliminate a lot of possibilites is how it performs outside of linux.

Do you have some brand of windows installed on the machine, and if so, does everything work correctly and at normal speeds when running that other os?

Which version did you install (feisty, edgy, dapper) and is it 32 or 64 bit? If you don't know how to tell, run the commands:
```

uname -r
lsb_release -a

```

---

### Post by phenn on 2007-06-14
Yeah I have XP running on this system just fine.  The only problem is my graphics card, which I think is halfway fried.  I say this because I can't play 3d games on it without extreme artifacts, yet it runs most other things completely fine, including most flash games etc.  Basically it can't use OpenGL I think and maybe Direct 3d too, though with dxdiag the direct3d test works fine. 

I installed the latest one (Feisty?) which I burned off the website.  Yes, I did check the CD and it was fine. I'm actually not sure if it's the 32bit or 64 bit version.  I remember trying the 64 bit version when I came to the realization that I actually had a 64 bit processor (let's face it in windows it doesn't matter) and was still having the same slowness problems. Sadly I didn't label some of the later burns (out of frustration) so I honestly can't say. Would it be doing this if I were trying to run 32bit on a 64 bit machine?

I really do think it has to be something goofy hardware wise.  I haven't really worked on computers in years though I basically can follow manufacturers instructions to install a new graphics card now and then.  Should I literally just open it up and try and tighten everything?

By the way these replies are wicked fast.

---

### Post by drs305 on 2007-06-14
Installing the 32 bit version on a 64 bit machine won't cause a problem. Many are doing that until more 64 bit programs become available. 

As to which version you have, when I run 'uname -m' on my 32 bit machine, the response is "i686". I don't have my 64 bit machine fired up at the moment but I'm pretty sure the command produces 'x86-64"

I'm not savvy enough to help with hardware issues but maybe someone who is can help you out here. Good luck.

---

### Post by schorsch on 2007-06-14
Perhaps you could try the parameter "acpi=off" when booting grub .....

---

### Post by phenn on 2007-06-15
hi guys.  

i opened up the computer and made sure everything was tightly connected etc. and it seemed to be fine.  I actually got my floppy drive working again though apparently that wasn't the problem.  Ah well. 

Anyway I also tried the acpi=off parameter when booting and it didn't do the trick either. 

Right now I'm getting an error when loading the hardware drivers.  it says fail, but that's it. 

that and when loading hald it givesme run-parts:/ then a path, then return 2.  I don't know what this means but it takes a long time to do it (i couldn't write the rest down if it would be that important but it looked like just a path). 


Other than that it takes a minute to find a frequency which works on my monitor, then shows Ubuntu with the bar loading up a little bit then just shows me what it's doing like I wrote above. 

For some reason I feel like the culprit has to be either my hard drive or onboard sound.  I can't imagine any other problems.  That said, it does play the drums (eventually) so I guess onboard sound is out?   But the hard drive is a SCSI hard drive (long story the guy who was building computer may have not known exactly what he was doing but he charged me very little).  It's not connected by one of those big cables to the motherboard (IDE cables unless I've completely lost it) but by I think a Serial cable (it's smaller and yellow). I really don't know why I'm focusing on this but it seems strange and relevant for some reason.  I guess because other than that my setup is so vanilla I can't fathom why I'm having these problems. 

I did a memtest yesterday for a few hours and came up with like 5 or 6 passes and 0 fails in 2 hours.  Does this seem right?  I mean when are those things done?  Could it be a memory problem if it's passing those tests like that?

Thanks for the help so far guys I really appreciate it and really do want to get this running.  If I can't get ubuntu I'll try another distro but I'm afraid I have some kind of bigger problem that another distro won't fix.

---

### Post by Azakus on 2007-06-15
Run this command
```
dmesg >> dmesg.log
```
then post the dmesg.log file created. Then we can all see if there's a big glaring error in your boot-up or something.

---

### Post by phenn on 2007-06-15
how can i post that log if i can't use the internet in ubuntu?

i use wireless and was just going to set it up once i got the thing installed instead of during the installer but obviously i can do next to nothing in the system.

---

### Post by candtalan on 2007-06-15
just throwing in a thought: 
Is there a way of verifying the clock speed or processor speed?

It seems that things are working as far as you can tell, but everything is just 20 (?) times too slow. If the hardware is actually ok (? hope so) then an interesting theory might be speed of something like a clock speed  - I do not know much about such things, except there are various busses with clock/s.  With a special PC build could it be that a setting on a speed related item is ok for windows but is somehow non standard and linux is not happy with it?

Speeds have lots of zeros in the number so it would be easy (?) to loose a couple of zeros and it would still work mostly but 100 times slower when the problem/s hit.

A bit of a wild theory I must say but hope it might help?

---

### Post by phenn on 2007-06-15
Well the system is not overclocked at all so hopefully it's all standard, but if it is I wouldn't know how to fix it at all without getting the guy who built the system to check it out and he built it a couple of years ago so that would be a bit of a stretch. 

and like I said there is a problem with hardware drivers failing, I know posting a log would make all the difference in the world but I can't figure out how I can do that without being able to get to the internet... though maybe I could put it on a floppy then boot up windows and post... hmmm...

for the record if I'm going to do this how do I get to a command line where i can run dmesg and once there how could i put it on a floppy.  GNOME seriously almost doesn't work it lags at literally a few minutes to open a menu sometimes... so "messing around" looking for it could take literally an hour or two.  I know this is ridiculously noob but I was really hoping I could get my feet wet a little slower getting this damn thing to work haha.

---

### Post by phenn on 2007-06-15
a little update, I tried running a live cd from PCLinuxOS and it too was very slow in loading. So it's probably something with the system.

---

### Post by phenn on 2007-06-15
K so I'm still chugging along trying to get this darn thing to work.  Bottom line it booted up eventually and I saw two error messages upon loading up to GNOME (eventually) 

One was the Daemons wouldn't load and so my themes etc. would be screwy, the other was that HAL had an interal error and wouldn't load. 

HAL not loading seems like a big problem, I noted before that when it was loading in verbose mode it gave me a "return 2" when trying to load HAL, I don't know what that means but it didn't say OK. 

For some reason the last time I tried to boot up it found all my hardware drivers trying to boot. 

Really once I click through those boxes things work, just very very slowly I think. 

I'm working on getting a log up.

---

### Post by MetalMusicAddict on 2007-06-15
Maybe play with your jumper settings on the drives? Move them to or from cable-select. Ive had PCs boot or act odd with different jumper settings. Just a thought.

---

### Post by Golyadkin on 2007-06-15
Does your harddrive have SMART functionality you can check in your BIOS? This really sounds like a defective harddrive, or a faulty connection to the motherboard / IDE Port.

---

### Post by phenn on 2007-06-15
I'm sorry I don't know what SMART functionality is.  Let me stress it does work in Windows without any problems that I've noticed.  Would Linux notice some problems that Windows doesn't?  Also I've been through my BIOS looking at things that seem like they might be odd to my very untrained eye (and consulting the internet if I see something because Lord knows I probably know what half the stuff in the BIOS means max). 

Is there any way I can test to make sure my hard drive is perfectly fine?  Some sort of program I can run etc.?

As for the jumper settings... yeesh.  I have no idea where to start with that, I'd have to find the MB manual to start with and then pray from there.

---

### Post by Jimmyfj on 2007-06-15
> **phenn said:**
> Hi guys, 

I've been looking through for a while trying to find a similar problem to mine but just haven't been successful so I'll have to just post.  I'm pretty much new to linux, I've installed linux in the past and played around with it a little bit but it never really stuck.  Here I am giving it another go. 

When I tried running the live cd it was just incredibly slow, and I really just couldn't install. The machine also gave me an error about gnome daemon not working and how themes etc. might not work.  So I tried the alternate install and it was still VERY VERY slow.  It took me 24 hours to actually get it all done, though that includes sleeping during the partioning so I'm sure it could have been done in less.  No less than like 16 though it was ridiculous.  I put this down to a slow CD rom drive for some reason though I now know this was a stupid assumption.  My CD rom drive is also a dvd/ cdrw drive and the actual cd rom reading was pretty slow I guess but still that's way too long. 

Anyway bottom line even with it on the hard disk now it still crawls along.  Sometimes on loading I get a hardware error about usb_load_firmware not working, and sometimes I don't.  Which boggles my mind, obviously. I still get the same daemons error message and in general it runs unusably slow and really very poorly.  Eventually I am able to shutdown but no joke it takes about 20 minutes from startup to when I can shut it down. 

I'd really like to run this OS so I'm looking for help.

Specs:
AMD Athlon 64 3200+ 2 Ghz processor
1 gig RAM
nvidia GeForce 6600 GT
80 GB SCSI hard drive (right now I think the linux partition is around 20 GB)
Dvd/CDRW/CD Rom Drive
USB Microsoft laser mouse
Standard keyboard
onboard sound nforce audio drivers
Wireless Compact G usb card from linksys

And that's all I really know.  If it makes any difference I was going through the BIOS (i didn't build this machine a friend did) and the cdrom/etc. drive is on IDE 0 and the hard drive is on IDE 2.  Both are Master on their respective channels or whatever, I believe.  If that makes no sense I can double check but that's what I remember.  I have very little idea of what this means but sense it might be important.  Or not. 

Thanks a lot for any help.

One thing  I noticed is that your system-bus is SCSI? Knowing that I noticed your device sequence: Being the CD-ROM/DVD drive on SCSI port 0? Can't be that in your case, because this would cause you a non-starting system. The SCSI controller itself MUST be jumped as SCSI device 0 (1). Then your hard drive comes in as SCSI device number 1 (2), CD-ROM SCSI 2 (3) and so on. In good will, you might say that the SCSI controller itself is Master and all the other devices on that bus are "slaves" (Slave 1, 2, 3 and so on).

My reason for pointing out your device sequence on the SCSI bus is that I can't get several different distributions to install if my distro-test-drive is jumped as slave. I know that both your drives are master on each bus ( bus 0 and 1 ). But device sequence DOES matter on my system.

First thing to try would be correcting the sequence of devices so that your hard drive is mounted on the bus BEFORE the CD-ROM drive on the SCSI bus. On SCSI your hard drive cable would be a wide cable, wider than that of an IDE cable. Your are able to see the difference in size with the naked eye.

But from reading your later input in this thread I noticed that you said your hard drive cable was thin and yellow thus indicating that your hard drive IS NOT a SCSI device but a SATA drive. There is a significant difference between those two. But IS your hard drive connected to your motherboard through a thin yellow cable then the drive is SATA and the CD-ROM will then be an IDE or EIDE drive and therefore mounted on two totally different buses which are only interconnected through either your north or south bridge on your chipset.
Just as an example: My 200 GB Maxtor SATA hard drive is found by Linux as SCSI but it IS SATA. In /dev my SCSI (SATA) drive is found as sda.

The first solution to go for will be entering your BIOS and load the BIOS Default Setup. Save these settings and exit BIOS to reboot the computer. If the computer reboots correctly try to find out if this has increased system speed. If it doesn't boot up correctly check BIOS boot sequence to see if your first boot device is your hard drive/ CD-ROM / CD-ROM/hard drive. Either one of those two settings will do for an already installed system.

If loading BIOS default settings doesn't increase system speed then your next step will be the process of elimination. Try disconnecting one device at a time. Reboot the system after each unmounted device in the computer to update BIOS automatically - You should get something like "Updating ESCD .... Update success - each time you disconnect a device.

This process of elimination can very well show which device is the bottleneck in your system. And once found it's time to replace it and start fine-tuning your BIOS for further optimization. Remember: If you have a 256 MB graphics card the BIOS setting "Graphics aperture size = MUST be equal to the amount of RAM mounted on your graphics card, here Graphics Aperture Size=256.

If the above doesn't solve the problem go to Windows and run a benchmark program. There's a lot of different programs that'll stress test your computer reveling the bottleneck obviously present on your system. Just remember one thing - Stress testing your computer in a burn in test may cause a faulty device to stop functioning. Also remember that a burn in test takes a V E R Y long time to complete so do the test while you sleep or does not reacquire the use of your computer. 

As for your question about whether your system memory, RAM, could be the problem? It could, but if you go to your Windows and run all tests in Sisoft Sandra you'll soon find out. Eventually take a screen shot of  the test results and post it here.

---

### Post by stchman on 2007-06-15
> **phenn said:**
> Hi guys, 

I've been looking through for a while trying to find a similar problem to mine but just haven't been successful so I'll have to just post.  I'm pretty much new to linux, I've installed linux in the past and played around with it a little bit but it never really stuck.  Here I am giving it another go. 

When I tried running the live cd it was just incredibly slow, and I really just couldn't install. The machine also gave me an error about gnome daemon not working and how themes etc. might not work.  So I tried the alternate install and it was still VERY VERY slow.  It took me 24 hours to actually get it all done, though that includes sleeping during the partioning so I'm sure it could have been done in less.  No less than like 16 though it was ridiculous.  I put this down to a slow CD rom drive for some reason though I now know this was a stupid assumption.  My CD rom drive is also a dvd/ cdrw drive and the actual cd rom reading was pretty slow I guess but still that's way too long. 

Anyway bottom line even with it on the hard disk now it still crawls along.  Sometimes on loading I get a hardware error about usb_load_firmware not working, and sometimes I don't.  Which boggles my mind, obviously. I still get the same daemons error message and in general it runs unusably slow and really very poorly.  Eventually I am able to shutdown but no joke it takes about 20 minutes from startup to when I can shut it down. 

I'd really like to run this OS so I'm looking for help.

Specs:
AMD Athlon 64 3200+ 2 Ghz processor
1 gig RAM
nvidia GeForce 6600 GT
80 GB SCSI hard drive (right now I think the linux partition is around 20 GB)
Dvd/CDRW/CD Rom Drive
USB Microsoft laser mouse
Standard keyboard
onboard sound nforce audio drivers
Wireless Compact G usb card from linksys

And that's all I really know.  If it makes any difference I was going through the BIOS (i didn't build this machine a friend did) and the cdrom/etc. drive is on IDE 0 and the hard drive is on IDE 2.  Both are Master on their respective channels or whatever, I believe.  If that makes no sense I can double check but that's what I remember.  I have very little idea of what this means but sense it might be important.  Or not. 

Thanks a lot for any help.

I have a similar setup and it took me approx 45 mins to install and update Ubuntu.  Sounds like you have some faulty hardware issues.

---

### Post by Jimmyfj on 2007-06-16
I forgot to mention that in order for you to fine-tune your computer's BIOS you'll need the manual for your motherboard. If you do not have a phycical manual to the board go to the motherboard vendor's homepage and download the manual as a PDF-file. Reading the manual ***will*** help you understand your computer and teach you how to force even more performance from your system's setup.

---

### Post by phenn on 2007-06-17
Alright I've been fudging around for a while and to be honest I'm running out of steam.  Chaintech's website didn't have the manual for my mobo anymore (damn them) so I'm just trying to do a process of elimination at this point.  Pretty much unless it's my mouse or keyboard I've got nothing.

I'm really guessing the hard drive is the big problem here.  It's SATA (as I've learned from this thread) and it seems like Linux has had some problems with these drives in the past.  I don't really know why my friend got me a SATA hard drive since it's the only one in the system, I put it down to not really knowing exactly what it was for I guess they were faster or something but I haven't noticed anything, whatever it's treated me fine until now but I really do think with a normal HD I wouldn't be having this problem.  Does anyone think I may be on the right track here and if so is there anything I can do about it?

Other than that literally I'm working to get this manual but god knows what that will be like.  This has been intensely frustrating. 

In other news I think my multipurpose disc drive runs at like 24x, which isn't that fast but I don't think it should be causing these kinds of headaches booting of the hard drive.  Argh.

---

### Post by nickaj on 2007-06-17
I can't give an explanation, but I had more or less the same problem with installing Ubuntu on my old laptop.  It couldn't start Gnome, and I didnt actually have the patience for a 17hr install so I gave up and did Xubuntu instead, which worked fine.  On my PC (faster hardware) Ubuntu worked just fine.  This surprised me a bit as I didn't think Gnome had such high hardware demands, hopefully someone else has an idea of the reason for this.

---

### Post by phenn on 2007-06-18
Ah and my motherboard is a chaintech VNF4 Ultra which runs Nforce 4 drivers (tricky I know). Again no idea if that helps but I'm just casting a wide net here.  Damn this system. Funds are low at the moment so going out and buying some new hardware is really an "it better be necessary" deal right now.

---

### Post by Jimmyfj on 2007-06-18
Here's a few sites you might find useful for your mobo:

[http://www.opendrivers.com/freedownload/230624/chaintech-sigmatel-codec-on-borad-audio-driver-linux-download.html](http://www.opendrivers.com/freedownload/230624/chaintech-sigmatel-codec-on-borad-audio-driver-linux-download.html)

[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)

Should you how ever decide to change your motherboard I'd suggest you look for a MSI board that fits your CPU - I have only good experiences with their boards with VIA chipset onboard. Works very well with both my AMD Athlon XP and my AMD Athlon 64 (my server). Both runnig without flaws at all. And BOTH have a SATA drive that just do their job.

---

### Post by candtalan on 2007-06-18
> **phenn said:**
> Alright I've been fudging around for a while and to be honest I'm running out of steam.  Chaintech's website didn't have the manual for my mobo anymore (damn them) so I'm just trying to do a process of elimination at this point.  Pretty much unless it's my mouse or keyboard I've got nothing.

I'm really guessing the hard drive is the big problem here.  It's SATA (as I've learned from this thread) and it seems like Linux has had some problems with these drives in the past.  I don't really know why my friend got me a SATA hard drive since it's the only one in the system, I put it down to not really knowing exactly what it was for I guess they were faster or something but I haven't noticed anything, whatever it's treated me fine until now but I really do think with a normal HD I wouldn't be having this problem.  Does anyone think I may be on the right track here and if so is there anything I can do about it?

Other than that literally I'm working to get this manual but god knows what that will be like.  This has been intensely frustrating. 

In other news I think my multipurpose disc drive runs at like 24x, which isn't that fast but I don't think it should be causing these kinds of headaches booting of the hard drive.  Argh.

Sata cable is quite thin, the older PATA type is broad and big - with about 40 wires in a flat strip. SATA drives are not unusual now at all, they are quite usual.
Are you sure it is set as master with its jumper short?

A 24x cd drive is easily fast enough no problem - particularly if you have tested the CD in the actual drive for errors (in CD or drive). You probably know to use the live CD and its start menu to do this.

If your mainboard has IDE sockets (for the wide flat cables) too you could consider using a PATA drive maybe (?) I think this is ok with sata being used too. Anyway, pata drives of say, 6GB or more, are two a penny or maybe even just discarded nowadays. It might be a useful test anyway.

When (if) you try another hard drive, go look at the bios screens first, to verify the hd has been recognised, then continue booting
good luck

---

### Post by phenn on 2007-06-18
Further bit before I go after the mobo manual again, the computer hangs on booting when I run acpi=off.  I get a console for ash and it says it can't load tty or run tty or find it or whatever.  I thought this might be of interest.

---

### Post by phenn on 2007-06-18
I just tried a safeboot off the livecd for pclinuxos and it worked perfectly.  Does this mean my hardware is out of the woods and now it's just a matter of boot options until I can finally run linux?

---

### Post by phenn on 2007-06-18
ok bottom line I can boot and run everything just fine if I add noapic acpi=off vga=normal in grub when I boot.  Is running any of these things a big problem or am I home free?

---

### Post by Azakus on 2007-06-18
> **phenn said:**
> ok bottom line I can boot and run everything just fine if I add noapic acpi=off vga=normal in grub when I boot.  Is running any of these things a big problem or am I home free?

Realistically, there is no downsides to running without acpi. ACPI is just a feature that allows the operating system to control power management instead of the BIOS, which allows laptops to use software settings to decide when to power down, hibernate, etc. There is no real downside to running without it. I'm not really sure what "noapic" does, but I think it has something to do with peripherals. Congrats on a working boot!
[http://en.wikipedia.org/wiki/Acpi](http://en.wikipedia.org/wiki/Acpi)

---

