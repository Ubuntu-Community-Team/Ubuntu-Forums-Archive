---
title: "dsl install help"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ccfjeff on 2007-06-05
Hi,

I burned and used my first LiveCD a couple of days or so ago (Feisty).  It worked fine on my main computer, though I need to play around with it a little to verify that it will work with all of my peripherals etc.

It is too big for an older computer I am trying to hook up to my cable router/modem, however.  Even Xubuntu is apparently a little to much for it to handle.  333 Mhz 96 Meg of Ram, and 8 Gig hard drive.

I decided to try and install using [Damn Small Linux]("http://damnsmalllinux.org/wiki/index.php/Minimum_Hardware_Requirements"), which has significantly lower hardware requirements.  As I understand it, DSL is based off of Knoppix which is based off of Debian so it should be very much like Ubuntu.

I registered and confirmed my email address on their forums but still cannot log in so I hope someone here might be able to help me with what I hope are easy questions as I don't know what to do and don't know where to find tutorials or what to do next.

I put in what I figured was a LiveCD, but am afraid it might be trying to install to the hard drive.  If it does and works correctly I can live with that, though I would have preferred to try and preserve some of the old files from it first.

It currently has/had Win 98 1st edition on it, but some of the files had apparently been corrupted.  The sound quit working and it keeps trying to load drivers for it, but I can't seem to locate the CD for the OS.  It also will not recognize the ethernet board which is more critical for me as I would like to set this machine up for my kids to browse the internet & play games on PBSkids.org etc.

It looks like I could have done a regular install after looking at the system requirements again, but I picked the "dsl 2" install option which was text only.  I was hoping for some sort of menu, but that doesn't appear to be how it works.

I have attached a screenshot (from a digital camera, as I don't know how to do a "real screenshot").

[http://img9.imagepile.net/img9/20591dsllinuxscreenshot.jpg](http://img9.imagepile.net/img9/20591dsllinuxscreenshot.jpg)

I looked at [a Linux/Debian HOWTO]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo") but it doesn't seem to match up with what I am seeing on the screen.  Anyone know where I can proceed from here?  Even a link to an online idiot's guide to text installation would be much appreciated.

Thank you.

---

### Post by smoker on 2007-06-05
hi, i think you need at least 128mb of ram to run dsl as a live cd, so i think it will be trying to install,

you can still access the dsl forums, though you won't be able to post. there is some info here which may hopefully help:
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=5;t=18526](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=5;t=18526)

personally i found puppy linux easier to install and set up than dsl, so it may be worth a try if you cannot get dsl up and running. i'm not sure of the min specs for puppy, but you will find info here:
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

---

### Post by GrueTamer on 2007-06-05
I've installed DSL from the livecd with only 64mb of ram...I can pretty much guarantee that it works.  As for that screen, try typing "startx".  It looks like X isn't starting.  If X isn't even installed, for some reason, try typing ```
apt-get install xorg
```.

---

### Post by ccfjeff on 2007-06-06
> **smoker said:**
> hi, i think you need at least 128mb of ram to run dsl as a live cd, so i think it will be trying to install,

you can still access the dsl forums, though you won't be able to post. there is some info here which may hopefully help:
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=5;t=18526](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=5;t=18526)

personally i found puppy linux easier to install and set up than dsl, so it may be worth a try if you cannot get dsl up and running. i'm not sure of the min specs for puppy, but you will find info here:
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

Thanks for the info and the links Smoker.  I had heard about Puppy in a couple of threads, but thought dsl might be a little lighter on the resources.  It is about 50 meg on the LiveCD vs. 70 meg on the Puppy.  I had also heard the Knoppix is supposed to be one of the best at recognizing and running hardware and dsl is derived from or a branch or whatever off of Knoppix as I understand it.  I also read that they were using [the older 2.4.x kernel]("http://damnsmalllinux.org/wiki/index.php/FAQ#Will_DSL_ever_use_the_2.6_kernel.3F_Has_it_even_been_considered.3F") as it support more of the older "legacy" hardware and this machine is probably *at least* 5 years old.

Maybe dsl uses more resources when booted from the LiveCD than if it is installed on the hard drive, but according to [the dsl main page]("http://damnsmalllinux.org/") it can run on a 486 with as little as 16 Meg of Ram!

[COLOR=DarkRed] Damn Small is small enough and smart enough to do the following things: [/COLOR][LIST]
[*][COLOR=DarkRed]Boot from a business card CD as a live linux distribution (LiveCD)[/COLOR]
[*][COLOR=DarkRed]Boot from a USB pen drive[/COLOR]
[*][COLOR=DarkRed]Boot from within a host operating system (that's right, it can run *inside* Windows)[/COLOR]
[*][COLOR=DarkRed]Run very nicely from an IDE Compact Flash drive via a method we call "frugal install"[/COLOR]
[*][COLOR=DarkRed]Transform into a Debian OS with a traditional hard drive install[/COLOR]
[*][COLOR=DarkRed]Run light enough to power a 486DX with 16MB of Ram[/COLOR]
[*][COLOR=DarkRed]Run fully in RAM with as little as 128MB (you will be amazed at how fast your computer can be!)[/COLOR]
[*][COLOR=DarkRed]Modularly grow -- DSL is highly extendable without the need to customize[/COLOR][/LIST]It may be that a total noobie such as myself shouldn't have tried the easier on the resources text only installation.  Or it may be that the older bios on that machine wouldn't handle the newer ISO bootloader.  There are a few different versions of the dsl LiveCD and according to their [Which File Do I Download page]("http://damnsmalllinux.org/wiki/index.php/Which_File_do_I_download%3F_%28long_version%29") my computer may be somewhere along the age border where perhaps I should have used a version for machines older than roughly 5 to 6 years old:

[COLOR=DarkRed]HOWEVER, there are some older computers with old BIOSes that don't work properly with ISOLINUX. So the DSL team has created an alternative livecd image that uses the old SYSLINUX bootloader, dslxxx-syslinux.iso In order to make this linux kernel work with SYSLINUX, some newer driver modules were deleted from the mini root in order to make everything fit, which could be a problem for some of the newer computers. [/COLOR]
[COLOR=DarkRed]So the rule-of-thumb is: [/COLOR]
 [LIST]
[*][COLOR=DarkRed] For newer computers (last 5-6 years or so), try the regular dsl.iso [/COLOR]
[*][COLOR=DarkRed] For older computers, you may need to use the dsl-syslinux.iso if the regular dsl.iso does not work properly.[/COLOR][/LIST]In any event, it certainly sounded like everyone was full of praise for Puppy on the thread you linked to.  If I can't get dsl to work I'll have to decide whether to try their version for the older machines or perhaps try Puppy.

---

### Post by ccfjeff on 2007-06-06
> **GrueTamer said:**
> I've installed DSL from the livecd with only 64mb of ram...I can pretty much guarantee that it works.  As for that screen, try typing "startx".  It looks like X isn't starting.  If X isn't even installed, for some reason, try typing ```
apt-get install xorg
```.

Thanks for the reply, GrueTamer!

Unfortunately, since I've never tried or even seen booting in text only mode I'm not sure what it's supposed to look like.  Is "X" a text menu?

I tried typing "startx" and got an error message. 

I then tried ```
apt-get install xorg
``` and got another error message.  -- See [the new "screenshot"]("http://img9.imagepile.net/img9/84898dsllinuxscreenshot2.jpg").

Although I have an ethernet cable hooked up to the cable modem/router, I'm not sure I have internet access.  I did when the computer was hooked up to a network at work a few years back, but some drivers may have been messed up and when I hooked it up here it wasn't working under Win 98 1st edition.  The sound card's drivers are apparently messed up, so I don't know if that is the issue or the ethernet card isn't working properly.  When I look in Win 98's control panel it lists that device as not working properly.

There might also be issues with the actual ethernet cable itself.  I tried a couple of different ones but a little piece of the plastic clip was broken off so it could be pulled out of the female plug without much effort.  I'm guessing that wouldn't make the ethernet card show up as being invalid in the control panel, but I don't know much about that type of stuff.  I also tried holding it in tight while others tried to surf but it didn't seem to make any difference.

I may have also messed up the ethernet board when I had plugged the ethernet cable directly from that computer to my other computer not too long ago.  I didn't realize until I was told later by someone that there are different types of ethernet cables for plugging into a router as opposed to plugging directly from computer to computer.  As I understand it they are reversed for one type, but not another.

We had never plugged them into computer to computer directly before, so I'm guessing the cables are at least the correct type to plug into the cable modem/router.  Curiously, one day we found my son using the internet from that old computer via an older version of Firefox.  They had previously only been able to play a few simple Linux games ported to Windows that I had downloaded and installed on there to give them something to do when I was using "my" computer.  That was the only time we had an internet connection, though, and it has never worked since.  I had not checked the control panel prior to that to see if the board showed up OK there, so it may have pooped out since then or maybe the drivers were just good enough to work under certain conditions?

My hope was that it was a driver issue and it would work fine under Linux.

Unless you have any other ideas, perhaps I'll just try to reboot it again tomorrow using a GUI interface.  If I can't get that to work maybe I'll try the "syslinux" for older machines, or maybe Puppy to see if I can get it to work.

Thank you both for your time and your help!

---

### Post by ccfjeff on 2007-06-06
I'm amazed.

I turned it off last night and this morning when I turned it on with the LiveCD still in it it just worked.  I'm not sure why it bypassed giving me the option of which install method I wanted to use.  It must have some sort of idiot detector that decided I didn't know what I was doing and just did the dsl 5 installation method instead.

It popped up to a nice clean desktop and it appears to be quite fast from what I can tell so far.  It is certainly blowing away the Win '98 that is/was installed.  No internet connection, though.  Bummer.

---

### Post by Shazaam on 2007-06-06
I managed to install DSL on a Compaq LTE 5000= 75mhz proc, 16megs of ram, and a 500MB hard drive. No cdrom and using dialup. DSL is different but it is a lot of fun.

---

