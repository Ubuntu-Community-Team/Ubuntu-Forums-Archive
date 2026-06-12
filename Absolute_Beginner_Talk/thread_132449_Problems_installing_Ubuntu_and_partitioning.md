---
title: "Problems installing Ubuntu and partitioning"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by SegaFan on 2006-02-18
Hi, I should introduce myself. I've got quite a bit of Windows and mac experience, but no Linux experience - so I hope this is appropriate here because it looks like I'll go back to being a complete beginner with Linux... Since last summer I've been building a PC, mostly as an experiment; its taken this long because of lack of time and funding, but I'm under no pressure with this. Given that I don't really know what I'm doing, I was amazed the other day when it actually powered up and showed the bios first go, and I haven't seen any smoke yet! This was always meant to be an educational project, so I can try things and learn from my mistakes. I had always intended to install Linux, because thats something else I have always wanted to learn and try.

I have an Ubuntu Hoary Hedgehog (5.04) disk from a magazine a while back. I successfully installed it sometime last year on an old laptop; it installed and only had a few problems, but I didn't have time to experiment then, so I never used it for any more than a few minutes and didn't really learn anything.

Now I'm using the same Ubuntu disk on my new machine and when installing it gets to the point with partitioning the hard drive. I select to do it automatically, and it chooses two partitions (a root and a swap) and starts saving the partition and at 13% complete it freezes. I've tried it several times, and it always stops at 13%, mostly it just freezes, but once it reboot when it got to 13%, and one time the display became distorted.

I realise theres also a good chance this might be a problem with my own hardware and not really anything to do with this forum, so I will keep looking into it; but any advice you can give would be appreciated.
I'm running an AMD Sempron 3300+ (2GHz), 512MB RAM. If you need any more specific details about the hardware I can go and check but I can't remember it all off the top of my head. It would be nice to get it working, but like I said, this is supposed to be partly an experimental project, I expect things to go wrong and amazed at getting this far; I'll get there eventually.

---

### Post by martin-per on 2006-02-18
[QUOTE=SegaFan]Hi, I should introduce myself. I've got quite a bit of Windows and mac experience, but no Linux experience - so I hope this is appropriate here because it looks like I'll go back to being a complete beginner with Linux... Since last summer I've been building a PC, mostly as an experiment; its taken this long because of lack of time and funding, but I'm under no pressure with this. Given that I don't really know what I'm doing, I was amazed the other day when it actually powered up and showed the bios first go, and I haven't seen any smoke yet! This was always meant to be an educational project, so I can try things and learn from my mistakes. I had always intended to install Linux, because thats something else I have always wanted to learn and try.

I have an Ubuntu Hoary Hedgehog (5.04) disk from a magazine a while back. I successfully installed it sometime last year on an old laptop; it installed and only had a few problems, but I didn't have time to experiment then, so I never used it for any more than a few minutes and didn't really learn anything.

Now I'm using the same Ubuntu disk on my new machine and when installing it gets to the point with partitioning the hard drive. I select to do it automatically, and it chooses two partitions (a root and a swap) and starts saving the partition and at 13% complete it freezes. I've tried it several times, and it always stops at 13%, mostly it just freezes, but once it reboot when it got to 13%, and one time the display became distorted.

I realise theres also a good chance this might be a problem with my own hardware and not really anything to do with this forum, so I will keep looking into it; but any advice you can give would be appreciated.
I'm running an AMD Sempron 3300+ (2GHz), 512MB RAM. If you need any more specific details about the hardware I can go and check but I can't remember it all off the top of my head. It would be nice to get it working, but like I said, this is supposed to be partly an experimental project, I expect things to go wrong and amazed at getting this far; I'll get there eventually.[/QUOTE]
Hi I'm martin and I've got as well problems with the installation. better: the installation of the  Ubuntu Hoary Hedgehog (5.04) disk is completed but when I want to boot it for the first time it shows me 1.username-fine 2. password fine, 3. a new mail adress from ubuntu and there I can't continue. anyone who can help me at this point?

greeting martin

---

### Post by SegaFan on 2006-02-18
OK, I have tried a SUSE Live disk which I also had, and also dosn't work, it freezes this time when it says "initialising hardware", so its probably not a problem with Ubuntu then. Does anyone know where best to get help with this kind of thing?

---

### Post by Jedeye on 2006-02-18
well if its a hardware problem and you don't know what the problem is then if you have some extra parts you can try switching them out... Put some ram in that you know is good and then try... if you still have a problem try switching something else out. Im not great at trouble shooting though, but that may help.

---

### Post by nixclusive on 2006-02-18
[QUOTE=martin-per]Hi I'm martin and I've got as well problems with the installation. better: the installation of the  Ubuntu Hoary Hedgehog (5.04) disk is completed but when I want to boot it for the first time it shows me 1.username-fine 2. password fine, 3. a new mail adress from ubuntu and there I can't continue. anyone who can help me at this point?

greeting martin[/QUOTE]
You can try:
```
$ mail
```
and press enter again to see more of the mails. That's probabely the internal mailing system (Postfix I think).

---

### Post by SegaFan on 2006-02-19
[QUOTE=Jedeye]well if its a hardware problem and you don't know what the problem is then if you have some extra parts you can try switching them out... Put some ram in that you know is good and then try... if you still have a problem try switching something else out. Im not great at trouble shooting though, but that may help.[/QUOTE]
Yeah, unfortunatly I don't have any spares, even from this machine (I'm on a mac at the moment). That makes it difficult.

The BIOS has detected all of the hardware I can think of, it tells me how much RAM I've got, and the model names of all my drives. So does this mean that they all work? My monitor is plugged straight into my graphics card, so I take it the graphics card is working fine (but thats the least of my worries now).

Could it be to do with the BIOS? I set the clock and made sure everything looked ok, but didn't alter any settings or anything, I don't really know much about this. I get this message whenever I boot up "BIOS is not installed" or something like that, I can look up the exact message if you would like... it dosn't sound right. Again, it looks like its not a problem with Ubuntu anymore, if its not a simple fix, if anyone knows where else I could look to get help with this kind of thing I'd be greatful.

Thanks for your help.

---

### Post by *desk* on 2006-02-19
My problem was....and still is my SATA drive.
I have attempted to install five Distros and have had the same problem with all of them. It's to do with the drivers for the SATA raid controller. I have two drives, the other is an IDE. If I disconnect the SATA drive then I have no trouble at all, on any of the Linux distros. 
Incidentally XP has no problems with the SATA.
There are many people in the various forums have the same problem, but I have not yet found a solution. 
Please, you experts out there, have you an answer?

---

### Post by newbie_jhay on 2006-02-19
hey segafan, i'm not yet an expert, but i've encountered that problem several times before (though not with linux, but with windows, a long time ago)... and the cause is either the RAM or the hard drive itself.... 

if you do not have any spare RAM which you could use, you could try to get your RAM tested on other pc's, say, like a friend's test pc, or maybe have it tested by techs from where you bought that RAM. if ever your RAM is good, you could try this one:

if you have any bootable diskettes (i'm assuming you have a floppy drive), which you could use to boot to dos, then, you could try running 

A:\>scandisk c: 

on your hard drive.... the last part of the scandisk is a thorough disk surface scan which could check and detect bad sectors on the drive...

by the way, let me just ask, is your hdd already formatted to atleast FAT? coz the downside to this is that you must first have your hdd formatted to FAT before it could run the scandisk... 

if you would attempt to format your hdd to FAT and it still fails, then, the problem lies in your hdd...

anyway, hope this info would help you =)

---

### Post by Jimmey on 2006-02-19
I'd reccommend getting Ubuntu 5.10 Breezy Badger from Shipit. It will take patience, but it's one way of finding out for sure if it's a hardware problem or not. And if it's not, you've got a more up-to-date version of Ubuntu :P

---

### Post by ChocoPanda on 2006-02-19
um, hello there, i too am a complete newbie to linux systems.. so.. please don't mind the stupid things i say:p 

i tried using ubuntu because i was quite fed up with windows ME.. the thing just keeps crashing... when i was installing ubuntu, i got about... 17gb for the OS, but i left another 22gb untouched because it has quite alot of my backup files that i dont want gone...

the installation was successful and went without a hitch, but i cant seem to find that 22gb of data... i chose 'do not use' while partitioning the hdd, and now it doesnt show up at the computers option.. what can i do to find it again? if possible, can i get all the data again?

please mail me at [email]king_of_panda@hotmail.com[/email] if ya know how to deal with this... thanks.

---

### Post by Mustard on 2006-02-19
[QUOTE=ChocoPanda]um, hello there, i too am a complete newbie to linux systems.. so.. please don't mind the stupid things i say:p 

i tried using ubuntu because i was quite fed up with windows ME.. the thing just keeps crashing... when i was installing ubuntu, i got about... 17gb for the OS, but i left another 22gb untouched because it has quite alot of my backup files that i dont want gone...

the installation was successful and went without a hitch, but i cant seem to find that 22gb of data... i chose 'do not use' while partitioning the hdd, and now it doesnt show up at the computers option.. what can i do to find it again? if possible, can i get all the data again?

please mail me at [email]king_of_panda@hotmail.com[/email] if ya know how to deal with this... thanks.[/QUOTE]

You need to mount the partition that you have your backups on.

Try reading over the instructions for mounting FAT and NTFS paritions on this link...

[http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)

---

### Post by SegaFan on 2006-02-19
> I get this message whenever I boot up "BIOS is not installed" or something like that, I can look up the exact message if you would like... it dosn't sound right.
OK, I looked up the full message.

At some point just after you power it up it says *"Serial_CH0 master: No device", "Serial_CH1 master: No device"*, I don't know if this is relevent. Then a bit later I get the message *"No drive attatched to fast-track controller. BIOS is not installed".*.

Straight after that it appears to behave normally. It just loads the Ubuntu CD from my CD drive (since I have nothing to load from my HD yet or my floppy drive). Then, as I said, it works as normal until 13% through the drive partitioning.

[QUOTE=newbie_jhay]hey segafan, i'm not yet an expert, but i've encountered that problem several times before (though not with linux, but with windows, a long time ago)... and the cause is either the RAM or the hard drive itself.... 

if you do not have any spare RAM which you could use, you could try to get your RAM tested on other pc's, say, like a friend's test pc, or maybe have it tested by techs from where you bought that RAM. if ever your RAM is good, you could try this one:

if you have any bootable diskettes (i'm assuming you have a floppy drive), which you could use to boot to dos, then, you could try running 

A:\>scandisk c: 

on your hard drive.... the last part of the scandisk is a thorough disk surface scan which could check and detect bad sectors on the drive...

by the way, let me just ask, is your hdd already formatted to atleast FAT? coz the downside to this is that you must first have your hdd formatted to FAT before it could run the scandisk... 

if you would attempt to format your hdd to FAT and it still fails, then, the problem lies in your hdd...

anyway, hope this info would help you =)[/QUOTE]
Thanks, I'll see if I can borrow some RAM from someone. How similar was your problem, by the way? Did it fail in exactly the same place as mine?

The hard drive is brand new, whether it comes formatted or not I don't know, I haven't done anything to it other than what I described. One thing that really suprised me building this PC is how little documentation you get with anything. I mean, I was kind of expecting all these different components to come with thick instruction manuals covering every techincal detail of what you've bought, but you hardly get anything; basic installation instructions at most, sometimes nothing.

---

### Post by Coelocanth on 2006-02-19
[QUOTE=*desk*]My problem was....and still is my SATA drive.
I have attempted to install five Distros and have had the same problem with all of them. It's to do with the drivers for the SATA raid controller. I have two drives, the other is an IDE. If I disconnect the SATA drive then I have no trouble at all, on any of the Linux distros. 
Incidentally XP has no problems with the SATA.
There are many people in the various forums have the same problem, but I have not yet found a solution. 
Please, you experts out there, have you an answer?[/QUOTE]

I'm no expert, but do you have your drives set up in a RAID configuration? If not, then check your BIOS and make sure the RAID option is turned off. It may be the cause of your problems. (You shouldn't need the SATA RAID drivers if you're not using RAID).

When I built my rig (just a few weeks ago), I got a lot of conflicting info about SATA drives. Some said I had to install the SATA RAID drivers during the OS install to get it to work (I was installing XP Home at the time),  others said no.

The truth of it is, if you're not setting up a RAID array, you don't need the drivers for RAID (depending on your mobo) and you should make sure the RAID option is off in your BIOS or you may run into all kinds of funky problems with your hardware.

---

### Post by newbie_jhay on 2006-02-23
[QUOTE=SegaFan]OK, I looked up the full message.

Thanks, I'll see if I can borrow some RAM from someone. How similar was your problem, by the way? Did it fail in exactly the same place as mine?

The hard drive is brand new, whether it comes formatted or not I don't know, I haven't done anything to it other than what I described. One thing that really suprised me building this PC is how little documentation you get with anything. I mean, I was kind of expecting all these different components to come with thick instruction manuals covering every techincal detail of what you've bought, but you hardly get anything; basic installation instructions at most, sometimes nothing.[/QUOTE]

hi, sorry for the delayed reply.... well, when i've got the problem with RAM while installing winxp before is, i usually get to the point where it is loading all the needed setup files, just before it starts formatting; but there was one time when it was in the formatting part.... but when the problem was in the hard drive, it's often in the formatting part - though i could'nt exactly remember at how many percent it stopped.....

by the way, just want to make sure... what type of hard drive do you use, is it a regular ide hard drive or a sata hard drive? coz by the error that you indicated, it seems that you're mboard supports sata drives but none is attached (or, it couldn't detect the sata hard drive that might be attached to it). and with the "bios not installed" error, there are mboards where you would still need to update or install a sata bios (where you could configure your sata drives properly and setup raid if needed. it is also separate from the regular bios which you see on all the other systems)....

if ever it is a sata drive, you could try to check on any disk provided with the mboard (most are usually bootable). most sata bios can be installed from the disk/s they provide with the mobo.... and if you want to search for further documentations for your board, you could try visiting the manufacturer's website (though some could be disappointing coz they lack the needed info, but still, some can be very helpful)....

hope u'l be able to resolve your problems with your pc.....

---

