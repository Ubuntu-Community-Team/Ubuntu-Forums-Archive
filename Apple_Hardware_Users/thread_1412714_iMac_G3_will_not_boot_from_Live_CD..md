---
title: "iMac G3 will not boot from Live CD."
date: 2010-02-21
forum: Apple Hardware Users
---

### Post by donaldmartin on 2010-02-21
Hi - I can't install **any** flavour of Ubuntu 9.10 onto my *new* iMac G3. Here are its specs:

iMac G3 New World (Indigo)
350MHz G3 Processor
192MB RAM
6GB Hard Drive
Slot Loader (CD only - not DVD)
Mac OS 10.3 Panther

The drive does work - I've played music from CDs on it, and it does allow me to view PDF files stored on data CDs. I can even view the Ubuntu CD through the Finder on the desktop. It just really doesn't want to boot from the CD.

I've tried multiple Linux distributions (all of them PPC compatible). Any suggestions, please?

---

### Post by northrup on 2010-02-21
Does it actually try to boot from the CD, or does it go straight to the hard drive?

On a PC, you'd be able to check the boot device priority by entering the BIOS menu.  I don't know if there's a pre-boot EFI menu or any other way of configuring the EFI's boot order.  If there is, check that.

Also, make sure you're using a PowerPC install CD (it seems like it's a PowerPC-based iMac and not an Intel-based), NOT the x86 or the x86-64 (AMD64) versions.  You can find all you need to know about the community-supported PowerPC port at [https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC).

---

### Post by donaldmartin on 2010-02-21
I've tried all the PPC editions of all the flavours of Ubuntu - when I push and hold "c" it thinks about it for a few seconds, then carries on to boot from the HDD. However, it does spin the CD a few times, then gives up.

---

### Post by Sef on 2010-02-21
Moved to Apple Users.

> I've tried all the PPC editions of all the flavours of Ubuntu - when I  push and hold "c" it thinks about it for a few seconds, then carries on  to boot from the HDD. However, it does spin the CD a few times, then  gives up.

1) Did you md5sum the download?

2) Did you burn it at 4x or less?

---

### Post by donaldmartin on 2010-02-21
I don't know how to use MD5SUM, and I've used 4x speed (slowest I can on my Dell computer).

---

### Post by marshag63 on 2010-02-21
Did you burn your CD in windows?  If so, did you burn it as a ".iso"?

MarshaG.

BTW, command to check md5checksum in linux:
md5sum nameof.iso   
then compare output with md5checksum of file posted where you downloaded it from.

---

### Post by donaldmartin on 2010-02-21
Yeah - I'm currently on a dual-booted Dell computer (Kubuntu 9.10 and Windows 7), and I was on Windows when I downloaded the files. They were all downloaded as ISOs and then burned to CD-Rs using Roxio Creator at 4x speed.

---

### Post by marshag63 on 2010-02-21
Also, did you clear PRAM when trying to boot?
Hold down: Command, Option, P and R keys - let it chime at least three times before you try booting from the CD by holding down the "C" key.

MarshaG.

P.S.  You could also try burning your CD in Kubuntu

---

### Post by donaldmartin on 2010-02-21
Tried resetting PRAM and everything - I looked on another forum and it gave me 3 things to do in the Firmware.

Is there any way I could install it straight from my Dell, such as a netinstall?

Oh by the way - the iMac in my avatar is the Mac in question - silly Apple won't learn from it's UNIX brother Linux :D

---

### Post by marshag63 on 2010-02-21
Before you try the firmware fixes, I would recommend trying a CD burned through Kubuntu - I hear K3B is good (I'm a Gnome user - love Gnomebaker).  Then you can at least say you tried everything before you mess with firmware.

Good luck!

MarshaG.

PS, Don't forget to clear PRAM at least three times when booting the Kubuntu-burned CD

---

### Post by donaldmartin on 2010-02-21
Thanks - I'll need to try tomorrow since it's very late and I'm in an exam tomorrow. Thanks for your help and I'll let you know how it goes.

PS This is why Linux is so much better than Windows. With Windows - I'd need to wait 48 hours for a reply from a technician who will tell me to buy something else - community = so much better.

---

### Post by donaldmartin on 2010-02-22
No - unfortunately it completely failed the CD I created in Kubuntu. It spun a few times, but still proceeded to load up Mac OS X.

I'd rather I got Ubuntu onto this iMac because I'm more comfortable with it, and unlike Mac OS, it's open source. :P

---

### Post by tiresia on 2010-02-22
Just to check that your CD-Rom is working and recognized by OpenFirmware: Do you still have a MacOS Installer? Can you boot from it?

Can you check in MacOSX which kind of CD your CD-Rom support?

---

### Post by donaldmartin on 2010-02-22
Unfortunately I don't have an installer CD (I bought it from eBay) - I'll have a look around and try and find out which kind it is in Mac OS X.

I think it does recognise it in Open Firmware - seeing as it reads and plays CDS.

---

### Post by tiresia on 2010-02-22
> **donaldmartin said:**
> I think it does recognise it in Open Firmware - seeing as it reads and plays CDS.
Sometimes it can happen that a CD is recognized by MacOSX but not by the OpenFirmware.
BTW the iso image of Ubuntu 9.10 is oversized, you can still burn it to a CD but it could be a problem for your CD-Rom - not sure.
Have you tried 9.04 or Debian Lenny (which is anyway more suitable to your Hardware)?

---

### Post by donaldmartin on 2010-02-22
I've been trying many different versions.

At first I tried Karmic Koala (9.10) and it failed to work no matter how hard I tried. Then I've tried Edgy Eft (6.10) and it won't work either. I've even gone to the extent of trying Debian on its own - and still nothing.

I'm beginning to think I'm not going to get far with this iMac.

---

### Post by tiresia on 2010-02-22
> **donaldmartin said:**
> I'm beginning to think I'm not going to get far with this iMac.
Please, check within MacOSX which kind of CDs your CD-Rom supports.
It can be that the CD-Rom is not original, and as such not Mac compatible, because Open Firmware does not recognize it.

But don't worry, you can always install Linux booting the Installer from an USB Stick.

---

### Post by The Brick on 2010-02-22
On a mac, to boot from a CD you need to hold the C key when you hear the BBBRRRRP and before the Screen fires up. Make sure the disk is in before you try this.
It worked when I installed Tiger and Lepoard.
If not the Command key  (The one with the apple on it) might work???
 
Hope this works.

---

### Post by donaldmartin on 2010-02-22
Sorry - I don't know how to tell what kind of CD drive it is. I can tell it's not a DVD-drive, since it doesn't read DVDs. I think it's a CD-ROM drive, because when I insert blank CDs, it either spits them back out (computer says no :p) or just doesn't do anything with them.

I've tried all sorts of key commands to get it to work. The "C" key is the most common one I try - though I have tried the "option" key to give a list of bootable devices, and it only shows the HDD.

The operating system that came with it is Mac OS X Panther (10.3).

---

### Post by tiresia on 2010-02-22
> **donaldmartin said:**
> Sorry - I don't know how to tell what kind of CD drive it is. I can tell it's not a DVD-drive, since it doesn't read DVDs. I think it's a CD-ROM drive, because when I insert blank CDs, it either spits them back out (computer says no :p) or just doesn't do anything with them.

I meant just that you should check in MacOSX if your CD-Rom can read/write CD-R/+R. May be you are using a wrong CD for your old Drive.

Last idea: have you tried to burn the iso image in MacOSX with the Apple Disk Utility?

After that I would go with USB Stick installation, because it is clear that either Open Firmware does not recognize your CD-Rom at boot up, or it does not accept the CDs the way you are burning them

---

### Post by donaldmartin on 2010-02-22
I've tried blank CDs - it just rejects them all. It doesn't even let me look at them in Finder, instead whirling them round a few times before giving them back to me. So I can't burn anything from the iMac.

Can an iMac G3 definitely boot from a USB flash drive? I've heard they're too old for that sort of thing. If they can, what button do I press on startup?

---

### Post by tiresia on 2010-02-22
I don't remember anymore, but you should have a look in MacOSX System Profiler>Disc Burning to see which kind of CD you CD-Rom reads. Right now are you using CD+R?

---

### Post by donaldmartin on 2010-02-22
How strange? The System Profiler doesn't actually show my CD drive anywhere. :confused:

---

### Post by tiresia on 2010-02-22
Can you have a look in System Profiler > Boot ROM Version?

---

### Post by donaldmartin on 2010-02-22
Boot ROM Version: 4.1.9f1

I'm guessing that's very old and outdated :D

Sorry for the long reply - totally forgot I was on forums for help, and I keep switching it off :D

---

### Post by tiresia on 2010-02-22
Firmware is up to date (the last for those imac)

It is not sure that your iMac can boot from USB
[http://forums.mactalk.com.au/10/16485-imac-g3-350-usb-boot.html](http://forums.mactalk.com.au/10/16485-imac-g3-350-usb-boot.html)
Not sure, because I don't have such iMac
maybe someone else...

You can try also an Hardware Boot or netboot
Here a good link
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

---

### Post by donaldmartin on 2010-02-22
Thank you - I'll need to try tomorrow. Hopefully I can set up a bootable USB drive and boot off of that. Failing that - I'll trudge through a netboot from my Dell (not looking forward to that) because I have both Linux and Windows dual-booted on it. 

Thanks for your help tiresia.

:D

---

### Post by marshag63 on 2010-02-22
I found another post about G3's.

Two more things to check:

Do you have two video outputs on this G3? If so, try plugging your monitor in the other video plug.

[http://ubuntuforums.org/showthread.php?t=610050](http://ubuntuforums.org/showthread.php?t=610050)

In another link within the above thread, someone said they used a Q-tip and rubbing alcohol to clean the cd-rom lens (dry it with the dry end of the Q-tip) and where then able to boot - couldn't hurt.

Also, regarding CD's - just in passing - these arent' CD-RW's - just CD-R's.

RE: Booting from usb - PPC's can't boot from a usb, but can boot from a firewire drive.

I'm thankful my G4 iMac didn't have these problems.

My G4 iMac had manufacture date info - did I miss clarification of that?

MarshaG.

---

### Post by donaldmartin on 2010-02-23
If I do boot it while using an external monitor, does that mean I need to stick to using that monitor, or will it work on the old CRT screen after I've installed it?

---

### Post by tiresia on 2010-02-23
> **marshag63 said:**
> Also, regarding CD's - just in passing - these arent' CD-RW's - just CD-R's.
Yes, but I was asking which kind of CD he is using - maybe the CD-Rom is so old that it does not support CD+R

> RE: Booting from usb - PPC's can't boot from a usb, but can boot from a firewire drive.
That's definitely not true. The question is if _his_ imac g3 can boot from USB. Some old imac g3 were reported to be able to boot from USB after firmware upgrade even if Apple did exclude that

---

### Post by donaldmartin on 2010-02-23
Sorry this is causing *so* many problems - I tried the external VGA port and was "amazed" to find it didn't exist. However, Apple was kind enough to leave me the same shape as the port I was looking for.

[IMG]http://photos-a.ak.fbcdn.net/hphotos-ak-snc3/hs363.snc3/23452_1137184288119_1782727017_260761_2574236_n.jpg[/IMG]

---

### Post by B_Free on 2010-02-23
Did you download the PPC version? Every version I've tried on the iMac G3 does start to load then I just get a dark screen. How much ram do you have? You need a minimum 256. Does your (date) PRAM battery keep the date and time accurately?

---

### Post by donaldmartin on 2010-02-23
> **B_Free said:**
> Did you download the PPC version?

Yeah - I downloaded the PPC and alternate PPC versions of Ubuntu, Xubuntu and Debian, and none of them have succeeded. All that's worked is I managed to make the CD spin a few times, and Mac OS X takes longer to start up. Nothing much else. Also - I can't actually view those CDs in Finder in Mac OS X for some bizarre reason.


> **B_Free said:**
> How much ram do you have? You need a minimum 256.

I've got 192MB of RAM, but I've read on other forums that 128MB is sufficient for the PPC versions of Ubuntu - especially Xubuntu. I know 9.10 (Karmic Koala) probably requires a minimum of 256MB, but I thought 6.10 (Edgy Eft) would work on lower-spec machines. Also - I tried plain and simple Debian, which I'm sure requires less.


> **B_Free said:**
> Does your (date) PRAM battery keep the date and time accurately?

Not at all. I've set up the system to download the date and time from the internet every time it switches on because I've given up setting it up all the time. If the iMac is disconnected from the internet, it returns to 00:00, 1 January 1970. I didn't think that's much of a problem.


I'm very interested in this idea of launching the installer from the hard disk. It's only a 6GB HDD, so I have **no** intentions of keeping Mac OS X Panther (10.3) on it. I'd rather just have full Ubuntu or Xubuntu. I've read the tutorial, but it doesn't say anything about downloading an actual installer - just Yaboot, VMLinux and a few other things. Is that really all I need?

Any help appreciated

:confused:

---

### Post by B_Free on 2010-02-23
Ubuntu is very sensitive to time. When you try to start a machine that has been shut down improperly or the power went off and crashed the computer, you may have a hard time starting up even if you were successful installing Ubuntu. I have an old iMac 266. I'll try installing 5.10. Maybe that will work. Will get back to you. You will need the entire 6 gigs to install Ubuntu. You don't need to download a separate installer.

---

### Post by DougieFresh4U on 2010-02-23
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)
The link can be a start for booting from hard disk :)
Have been trying for the longest to get my G3 and Ubuntu together, and so all I have managed to do is kill my screen on the G3 and now have to use external monitor. 
I get as far as cd loading and after boot: prompt appears, screen goes black and stays there until I eventualy shut it down and start over. I have 512RAM and 20GB hard drive running os 10.3

---

### Post by donaldmartin on 2010-02-23
Is there any step-by-step guide to follow to complete this process, because I am totally confused. I see parts saying "*Copy (not move) the following four files which you downloaded earlier from the Ubuntu archives*" - **there is no earlier**. I must admit I'm rather confused.

:P

---

### Post by donaldmartin on 2010-02-23
> **DougieFresh4U said:**
> all I have managed to do is kill my screen on the G3 and now have to use external monitor.

At least you got some VGA port - look at my earlier post - they actually took that privilege away from me by giving me the metal grill (or *chassis*). I can't actually boot from the CD - **full stop** (*period* if you're American).

---

### Post by DougieFresh4U on 2010-02-23
> **donaldmartin said:**
> Is there any step-by-step guide to follow to complete this process, 

:P
I wish! What you read is about as step by step as it gets. I have yet to see Ubuntu on my G3. Never even got the live-cd to work. Would be nice if some one can make an actual cd that would boot and run and maybe even install and finishing with a desktop with out fiddling with this or that :P

> **donaldmartin said:**
> At least you got some VGA port - look at my earlier post - they actually took that privilege away from me by giving me the metal grill (or *chassis*). I can't actually boot from the CD - **full stop** (*period* if you're American).
I saw that. For all my effort, I wish to see live-cd in action and it just isn't happening.

---

### Post by donaldmartin on 2010-02-23
Damn - I thought Microsoft were bad for keeping everything closed up and sealed off from the user, but Apple have taken it to absurd heights with the iMac G3. It's a lovely computer, looks a lot better than most, but it's far too complicated to mess with. Especially when you've got so many variants (200/300MHz - Tray/Slot Loaders - Different RAMs - Different Disc Drives etc).

Why the hell did Canonical think it was a good idea to stop commercially supporting PowerPC processors?

---

### Post by tiresia on 2010-02-23
> **DougieFresh4U said:**
> I get as far as cd loading and after boot: prompt appears, screen goes black and stays there until I eventualy shut it down and start over. I have 512RAM and 20GB hard drive running os 10.3
If you are using the live CD, have you tried typing ```
live-nosplash-powerpc video=ofonly
```

---

### Post by marshag63 on 2010-02-23
Maybe you should move on to try booting from a USB key.  Unetbootin works great!

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


I'd go alternate install - just because you will have more ram free for the install.

Good luck and let us know how it goes.

MarshaG.

---

### Post by B_Free on 2010-02-23
I can identify with you frustration. You sound like myself in my first post. The live CD will NOT work. The alternative install disk will probably work. But I still worry about the date and time being off. It may not start because of this. If you decide to put a new battery in, maybe RAM, you should google how to take apart iMacs (the videos help) I've taken apart iMacs of this age and it can be tricky not to break tabs and reinstalling the guts because the CD ROM has to be held taught on the spring that is located over the HD.
If you wish to continue with the install try [http://old-releases.ubuntu.com/releases/breezy/](http://old-releases.ubuntu.com/releases/breezy/). ONLY the install CD. Start holding down the C key. Just follow all the instructions. Agree with everything. Let it partition your drive the way it wants to. The install takes a long time. It first copies the files, then it installs them.

---

### Post by DougieFresh4U on 2010-02-23
> **tiresia said:**
> If you are using the live CD, have you tried typing ```
live-nosplash-powerpc video=ofonly
```

Not exactly sure, but the code you provided is very close or same as what I had typed in and caused me to  lose screen on my G3 and now stuck using external monitor.

---

### Post by B_Free on 2010-02-23
DougieFresh4U, this may work on other Macs but not the old iMacs. I can't speak on the newer iMacs.
donaldmartin
I forgot to say earlier, when the info comes up on your screen type help, press the return key. Type install, then the return key. This is only if you wish to install from the install CD.
DougieFresh4U
What type of computer do you have? It is not an old iMac.

---

### Post by tiresia on 2010-02-23
> **DougieFresh4U said:**
> Not exactly sure, but the code you provided is very close or same as what I had typed in and caused me to  lose screen on my G3 and now stuck using external monitor.
I don't understand why you are wasting your time with an external monitor if the 'internal' monitor is not broken. You have a graphic problem, that you should get solved with video=ofonly at least to install.

donaldmartin has a different problem, because his CD-Rom is not detected by OpenFirmware. And he should try other alternative methods to boot the installer as explained in the link I mentioned before

Both of you should use the alternate-cd (and read the powerpc faq and issues)

(Unetbootin does not fit to ppc)

---

### Post by marshag63 on 2010-02-23
See tiresia's link in post #26 -i know how confusing it can be, but you will get past it.  Its been a while since I installed 8.04 on my g4 iMac - i had lots of problems with HFS+ - it was my first experience with a Mac ever.  

This has gotten me curious how 9.04 would run on my G4 iMac, but i dread the wifi setup.

I'm keeping my fingers crossed for you that the open firmware boot will work - looking forward to seeing this post marked as "SOLVED"  :)

MarshaG

---

### Post by donaldmartin on 2010-02-24
I think I'm gonna try UNetbootin since I've got nothing else to lose. I've tried the "boot from hard disk" setup, and it's far too complicated - I don't even know where to get those files from, or what it means by the "Ubuntu Archive".

Also, I've tried the alternate CDs - to no avail. I'll try UNetbootin and let you know how it goes.

PS - I'm downloading Karmic Koala Ubuntu - is this a bad idea? I originally saw the Lucid Lynx daily image and thought "If they've not got it working right, like hell is it gonna work properly on my iMac". What one should I try, the full-blown desktop CD, or the alternate install? It *may* take some time, since my internet's playing silly-buggers and downloading at **2kbps**. I'll try and get back to you as soon as I can.

---

### Post by donaldmartin on 2010-02-24
Some good news for all:

I've managed to boot to Yaboot and am currently performing a net-install of Ubuntu 9.10 PPC :D

HAPPY DAYS!!!!

:D:D:D

Thanks for your help

PS - This is the link that worked = [http://gn.iohazard.net/wiki/GN/UbuntuG4](http://gn.iohazard.net/wiki/GN/UbuntuG4)

---

### Post by tiresia on 2010-02-24
> **donaldmartin said:**
> Some good news for all:

I've managed to boot to Yaboot and am currently performing a net-install of Ubuntu 9.10 PPC :D

HAPPY DAYS!!!!

:D:D:D

Thanks for your help

PS - This is the link that worked = [http://gn.iohazard.net/wiki/GN/UbuntuG4](http://gn.iohazard.net/wiki/GN/UbuntuG4)

Glad to hear it! (btw it is one of the method it is suggested in the links I mentioned before)
You could have problems with your xorg. Visit the best link about imac 
[http://forums.debian.net/viewtopic.php?f=16&t=20481](http://forums.debian.net/viewtopic.php?f=16&t=20481)
and osvaldkelso's blog
[http://oswaldkelso.blogspot.com/](http://oswaldkelso.blogspot.com/)

---

### Post by rockhopper on 2010-04-06
Is there any way to adjust the monitor brightness/contrast settings in Linux or through OF?

Within one hour of receiving an iMac G3, I erased Mac OS 9, installed Debian netboot; and then could not find a way to adjust monitor settings in linux. Tried xvattr, but it has no effect.

The current brightness level is hurting my eyes, and also the CRT monitor. Besides the contrast settings are making it unusable for most purposes.

---

### Post by linuxopjemac on 2010-04-06
Oswald had this idea:
> You may want to try xbacklight

```
debian800:~# apt-cache search xbacklight
```
xbacklight - simple utility to set the backlight level

xbacklight =50 to set the screen brightness to 50%

xbacklight +10 to increase

xbacklight -10 to decrease

> I have resolved the problem.
First i had to take off the clear plastic part of my imac, and adjust the CRT screws to sharpen it and change the brightness levels. The resolution and color were still off, and i used xvattr to correct the color levels. Now it looks pretty good, not brand new, but definately operational. Thanks!

---

### Post by natgab on 2010-04-07
I want to add some information for others that will find this thread trying to install Ubuntu PPC on their iMac G3.  I have a iMac G3 400MHz and had Debian working on it.  I currently have Ubuntu 9.04 loaded on my Powerbook G3 400MHz which shares most of the same hardware.

As best as I can tell from Mac sites such as [www.lowendmac.com](www.lowendmac.com) & [www.everymac.com](www.everymac.com), all the old Macs from the G3 era only used CD-ROM, not CD+ROM.  **[COLOR="Red"]The CD has to be a CD-ROM (negative)[/COLOR]**, this was what Apple chose back when there were seperate drives for CD- & CD+. PowerMacs came with DVD-RAM.  So if you have a iMac with enough memory & HD space, you still need to pay attention to what CD you use.

These old Mac have USB 1.1, so if you are trying a USB boot, it will be slow.  Unless its a PowerMac and has a USB 2.0 card added.  I have never tried a USB install.  But wanted to add this information.

And if anyone has a spare one that is working with Linux, it seems like a great candidate to repurpose for kids / grandparents.  All-in-one and virus free for the newbies in our families.  :lolflag:

Hope this helps someone else so they can enjoy a classic.

---

