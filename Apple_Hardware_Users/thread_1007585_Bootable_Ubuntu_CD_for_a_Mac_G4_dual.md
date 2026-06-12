---
title: "Bootable Ubuntu CD for a Mac G4 dual?"
date: 2008-12-10
forum: Apple Hardware Users
---

### Post by Steve M on 2008-12-10
Hi all,

Where can I get a download which I can burn on my PC to make a bootable disc for a PowerMac G4 AGP Dual Processor which has an ancient Apple OS on it?

Cheers,
Steve

---

### Post by doctorbighands on 2008-12-10
Hi Steve,

This ([http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)) should cover everything you need. You can find a Live CD as well as the alternate ones, and for pretty much every release.

Hope that helps!

---

### Post by Steve M on 2008-12-10
Hi again,

And what program do I use within my PC to create a bootable CD for the PowerMac from the download? (I have downloaded "ubuntu-8.04.1-desktop-powerpc.iso" and need to turn it into a disc for the Mac)

I had downloaded something last year when playing with Ubuntu for the PC but cannot remember what it was I had to download and use to create the bootable PC disc?

Steve

---

### Post by ayoung on 2008-12-10
The bootable CD is an .iso image, so you should be able to use the standard Disk Utility with these instructions: [http://www.macosxhints.com/article.php?story=20060619181010389](http://www.macosxhints.com/article.php?story=20060619181010389) .

I got Dapper Ubuntu installed on an Old World G3 Mac, and I can't remember the details of generating the bootable disk.  I'll post if it comes back to me.

---

### Post by Sturgis on 2008-12-11
> **Steve M said:**
> Hi again,

And what program do I use within my PC to create a bootable CD for the PowerMac from the download? (I have downloaded "ubuntu-8.04.1-desktop-powerpc.iso" and need to turn it into a disc for the Mac)

I had downloaded something last year when playing with Ubuntu for the PC but cannot remember what it was I had to download and use to create the bootable PC disc?

Steve

If you have not done so, check the information here. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

It pretty much covers all operating systems and methods.

---

### Post by Steve M on 2008-12-11
Hi

I have burned the disc, and it seems to go well up until session user appears on the top bar and the internet convention appears with an exclamation. 

The system seems to crash at that point, as it all freezes.

The Powermac is not connected to the internet, does it have to be for me to load this disc?

---

### Post by Steve M on 2008-12-12
I have tried 7.10 and 8.04 both desktop and alternative with no luck, it either keeps freezing with 8.04, and 7.10 displays h_disp too large?

Any ideas?

---

### Post by stream303 on 2008-12-12
Because you may be facing display issues right off the bat, I'd recommend booting from the "alternate" images, which installs with text-only.  This can get the distro on the disk before trying to fix any display issues later.

You'll have a full desktop later, but for now the text-based "alternate" installer will bypass some graphics issues.

And burn at a low speed - low enough for your cdrom to handle - typically I burn at 4x or even less regardless.

---

### Post by Steve M on 2008-12-12
> **stream303 said:**
> Because you may be facing display issues right off the bat, I'd recommend booting from the "alternate" images, which installs with text-only.  This can get the distro on the disk before trying to fix any display issues later.

You'll have a full desktop later, but for now the text-based "alternate" installer will bypass some graphics issues.

And burn at a low speed - low enough for your cdrom to handle - typically I burn at 4x or even less regardless.

Hi,

I have both Desktop and alternative discs of both Hardy and Gutsy. I take it you mean use the alternative disc? 

If so only Gutsy gives me the option of graphics resolution, but fails to boot, instead giving me a black screen with text awaiting command promps or such.

Alternative Hardy 8.04 seems to load up fine up to a point, I had a blank drive which it loaded onto OK, allowing me to see what I see on my PC with Ubunto,. Once loaded onto the HD, I get to input user, password and it looks correct. It freezes at the desktop once the twin monitors indicating no network appear in the top tool bar, is this indicative of a graphics problem? If so why do I get to see everything up till that point? (This is the same problem I get with the desktop version too)

How does the "alternate" image disc bypass graphics problems? As I said I have successfully created four discs. 

I guess I will try again with a different graphics card?

---

### Post by stream303 on 2008-12-13
Oh man, you are almost there.  Sorry about the confusion on my part.  You were already doing things right and I must have been sleeping while typing.

Anyway, - you've got a gui up once past the login, (does the resolution look ok, or is it huge or too small), but perhaps when the network comes up, it just hangs since it isn't connected to the net.

Can you get to a virtual terminal via ctrl-alt-f2 ?

If so, you might be able to run 'top' to see if there is a process that is just hogging the system at 100% or so.  Maybe network-manager, but that is just a wild guess.

I'm also wondering if you have the ati or nvidia card in your machine:

[http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html](http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html)

---

