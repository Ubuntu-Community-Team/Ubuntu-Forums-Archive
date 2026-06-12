---
title: "Install Lockup - 'Uncompressing Linux... Ok, booting the kernel' - total lock up.."
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by PepDogFSU on 2006-06-16
Greetings,

Fairly savvy computer programmer here, new to Linux/Ubuntu - picked up a used box on ebay to use to tool around with Linux, read the initial post about 'not forcing' one Linux distro if you have problems with it etc... not sure if the problems I am having with the server install constitute a 'cut and run' situation... :-)

I pop in the latest Ubuntu server install cd, and it boots up to a 'boot:' prompt with an opportunity to press F1 for special options etc... but I press enter for the default server install and it looks like it is loading until I get to the point where the screen goes black for 2 seconds and then I see

Ready.
Uncompressing Linux... Ok, booting the kernel.

At this point the keyboard is locked up and as far as I can tell the computer has locked up...

Any ideas? 

Computer hardware....
- HP x4000 Workstation
- 1GB of RDRAM PC800 45ns
- Dual Intel Xeon 2.0Ghz Processors w/ Hyper Threading
- ATI Fire GL4 128 MB Video Card with Dual DVI output 
- (2) IDE connectors on the mother board 
- 73 GIG Hard Drive Ultra 160 SCSI (10,000 RPM) 
- CD (IDE) and Floppy drives

Much appreciated! Everything I have read/saw so far about Ubuntu makes me eager to find a home w/ it - otherwise I'll push on to the next distro if you guys feel like it is a lost cause...

Kind regards...

---

### Post by Dilligaf on 2006-06-16
I have this problem when my usb printer is turned on. I have to make sure the printer is off in order to boot. (Epson stylus photo R320). I think it has to do with the card reader in the printer but I'm not sure,

Mike

---

### Post by PepDogFSU on 2006-06-16
Greetings Mike,

Nothing USB wise is hooked up to the computer...

Could the DVI graphics card or the DVI to SVGA converter I have installed cause any trouble?

[QUOTE=Dilligaf]I have this problem when my usb printer is turned on. I have to make sure the printer is off in order to boot. (Epson stylus photo R320). I think it has to do with the card reader in the printer but I'm not sure,
Mike[/QUOTE]

---

### Post by PepDogFSU on 2006-06-17
Greetings,

Well I played around with the BIOS settings trying to disable everything I did not need - no luck. 

Then I yanked another video card from another computer and popped it in and everything worked great. The server cd booted up to the graphical version of the boot menu (I assume this means it 'liked' this card better) and did not lock up at all.

Now - I want to install the graphical interface, so I go to install the 'desktop' Ubuntu cd, and it hangs after I press enter for 'Loading' - I think the CD is bad as i can hear the disc spinning up and down over and over again.

Am I on the right track though (i.e. use the 'desktop' install cd to install the graphical elements)? 

FYI - Video card that locked up Ubuntu install is (just going to type in everything I can find on the card)

FGL Graphics, ATI Technologies Inc
Fire GL4
3902B621
Has a sticker on the top of the fan that says 'FOXCONN'

Kind regards....

---

### Post by frankO on 2006-08-24
Hi, I have exactly the same machine - HP X4000 and exactly the same problem.
The funny thing is is that the earlier Kubuntu - Hoary Hedgehog will load up fine. I would love to load Ubuntu dapper. Has anyone worked out how to do that or is changing video card the only way.

---

### Post by napzilla on 2007-01-20
The ATI graphics cards do not seem to like Ubuntu at all. I've been having random lockups since I switched from XP two months ago. My post at:
[INDENT]Ubuntu Forums > New to Ubuntu? Look Here First!  > Absolute Beginner Talk>random lockup[/INDENT]
summarises everything I've been able to learn about the issue thus far. I'm either going to keep looking for a solution or start looking for a new graphics card.

Hmm... Maybe one of the Windows machines in my lab has a different video card.

---

### Post by stevetsc on 2008-07-01
Well, I just got one of the HP x4000's today, I'll have to see what graphics it has in it, but the driver for ATI is far less problematic now that ATI/AMD has open-sourced it.  On my desktop I have a Radeon 5200 with Ubuntu 8.04 and it runs flawlessly with compiz enabled.  I will see if I can offer more help tonight, but mine might have a 3dlabs card in it.

---

