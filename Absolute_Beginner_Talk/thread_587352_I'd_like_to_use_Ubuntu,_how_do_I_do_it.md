---
title: "I'd like to use Ubuntu, how do I do it?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by WillJeffery on 2007-10-22
Hello there,

I've been a Mac user for about 16 years (nearly all my life) and I absolutely love the OS. I've tried Windows on a number of occasion but never warmed up to it (I couldn't deal with the complications of protecting it, among other things) I was chatting with one of my more "techie" friends the other day, and we were debating the best OS on the market. I, of course, argued OS X, while he argued Ubuntu. He said that it is much better, although it has its fault like any OS. He also said it is basically like OS X, but on a more "pro" level. So, here I am.

I want to try it out, and hopefully migrate to it, partially or fully. But, having a bit of a older Mac, I'm not sure if I can *do* it. 

First of all, let me list my hardware:

[B]Apple iMac G4 1.25 Ghz (17" flat panel LCD)
[/B]CPU: PowerPC G4 (3.3) (1.25 GHz)
Motherboard: Dunno, doesn't say
Bus: 167 MHz
GPU: nVidia GeForce FX 5200
Display: iMac Built-In LCD 32-bit
RAM: 768 MB DDR SDRAM
Audio: Texas Instruments TAS3004
HD: ST380011A (I think it's a SeaGate) (80.0 GB [listed])
External HD: LaCie "Porshe" 160GB
Keyboard: Apple Pro Keyboard
OS: Mac OS X 10.4.10 (8R218 )
Kernel: Darwin 8.10.0
CDR/DVDR: PIONEER DVD-RW DVR-106D
Wireless: AirPort Extreme (405.1 (3.90.34.0.p18 ))
Modem: Dash2

I hope that's enough info :P


I have no idea how to install Ubuntu, or partition (is that the right word? :S) my HD for two OSs. Can anyone point me in the right direction? I have DVD-Rs coming out the ying-yang so I'm good on that front.

Yeah so hopefully one of you guys can help me. :)

Thanks in advance!!!!


-----Any other information available by request-----

---

### Post by Pumalite on 2007-10-22
[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

---

### Post by cfaulkner on 2007-10-22
While I agree with you that OSX is a great OS and I don't wish to start a flame war or call you a forum troll.  But, with this in mind.  OSX is just like linux but looks pretty.  Only thing I don't like about the Macs is the hardware, using Sub-standard parts and charging outrageous fees for them and charging you for the design is not my cup of tea.  

However, back on topic,  Looks like there's not a Installer cd recent for powerpc.  the newest release is 6.06.1

[http://mirrors.kernel.org/ubuntu-releases/6.06.1/ubuntu-6.06.1-desktop-powerpc.iso](http://mirrors.kernel.org/ubuntu-releases/6.06.1/ubuntu-6.06.1-desktop-powerpc.iso)

burn that to a cd and give it a shot.

---

### Post by WillJeffery on 2007-10-23
> **cfaulkner said:**
> While I agree with you that OSX is a great OS and I don't wish to start a flame war or call you a forum troll.  But, with this in mind.  OSX is just like linux but looks pretty.  Only thing I don't like about the Macs is the hardware, using Sub-standard parts and charging outrageous fees for them and charging you for the design is not my cup of tea.  

However, back on topic,  Looks like there's not a Installer cd recent for powerpc.  the newest release is 6.06.1

[http://mirrors.kernel.org/ubuntu-releases/6.06.1/ubuntu-6.06.1-desktop-powerpc.iso](http://mirrors.kernel.org/ubuntu-releases/6.06.1/ubuntu-6.06.1-desktop-powerpc.iso)

burn that to a cd and give it a shot.


Hmm I downloaded that, burned on a DVD, and tried to boot off it and my computer just spat it out. It mounted right after I burned it with toast, but after I tried to boot from it, I won't even mount on the desktop anymore....

---

### Post by bobpur on 2007-10-23
It sounds like you burnt the ISO image straight to a cd. You need a burning program capable of converting an ISO image to a bootable cd image, burn that to a cd and boot from that. CDBurnerXP Pro 3 is a good one for that. There are others, but that is my preference.
When you are ready to burn, select a low burn speed for a better quality cd. 4X to 12X is a good speed. Some will argue that normal burn speeds (48X to 52X) are good nowadays, but most of us prefer the slower speeds.

                                                                                             Good Luck.

---

### Post by WillJeffery on 2007-10-23
> **bobpur said:**
> It sounds like you burnt the ISO image straight to a cd. You need a burning program capable of converting an ISO image to a bootable cd image, burn that to a cd and boot from that. CDBurnerXP Pro 3 is a good one for that. There are others, but that is my preference.
When you are ready to burn, select a low burn speed for a better quality cd. 4X to 12X is a good speed. Some will argue that normal burn speeds (48X to 52X) are good nowadays, but most of us prefer the slower speeds.

                                                                                             Good Luck.


Yes, this is what I did. Can Toast Titanium 7 do that? I'm pretty sure it can... So let me get this strait. I download the ISO, mount it, THEN burn it onto a CDR? (is a DVDR OK?), then I reboot holding the "C" key?

---

### Post by Sef on 2007-10-23
> So let me get this strait. I download the ISO, mount it, THEN burn it onto a CDR?

Not quite.  Download it, check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM"), then burn it to a CD-R.  Once that is done, you can reboot, but make sure your BIOS is set to check the cd-rom/rw before the hard disk.

---

### Post by steve.horsley on 2007-10-23
The file is an **image** of a CD, both the filesystem and its contents. 

You don't mount it and burn the contents to CD as this will lose the boot-code which is part of the filesystem and not part of the files inside the filesystem.

You don't just burn the file to CD as a file as this just gives you a bootable filesystem inside another filesystem. 

.ISO Image files have to be treated differently to any other file type. If you don't have a burner that can do this, maybe you can get your frend to burn the CD for you?

All the above is true of CDs for x86 systems. I don't know how Macs boot - it may be very different.

---

### Post by WillJeffery on 2007-10-23
> **steve.horsley said:**
> The file is an **image** of a CD, both the filesystem and its contents. 

You don't mount it and burn the contents to CD as this will lose the boot-code which is part of the filesystem and not part of the files inside the filesystem.

You don't just burn the file to CD as a file as this just gives you a bootable filesystem inside another filesystem. 

.ISO Image files have to be treated differently to any other file type. If you don't have a burner that can do this, maybe you can get your frend to burn the CD for you?

All the above is true of CDs for x86 systems. I don't know how Macs boot - it may be very different.

Just quickly, Mac PowerPC G4s **are** x86 :)

I have a Pioneer DVD/CD burner (its ~4 years old, see OP for more details) and Toast Titanium (semi-profession OS X burning software [[http://roxio.com]](http://roxio.com])) so I'm pretty sure that isn't the case (meaning it burns the .ISO fine.) ----- Additionaly I have Disk Utility, which is what is used in the Ubuntu "How To Burn" Tutorial.

So maybe I just need to try a high quality burning speed? Or is DVD+.iso = unbootable? I also just downloaded 7.01 or 7.10 or w.e it is for PPC, so I'll see if that works when I get home.


If anyone has any pointers please let me know.

Cheer! :)

---

### Post by WillJeffery on 2007-10-24
Yeah so that didn't work. I've downloaded Ubuntu 6.06.1 PPC (ubuntu-6.06.1-desktop-powerpc.iso), verified the md5sum or w.e, burned it with Disk Utility @ 1X speed (highest qualitity) and it STILL spits out the disc (which I burned onto a DVD btw. Not a CD... not sure if that makes a difference) when I try to boot off it. 

Am I missing a step here? Do I need to partition my HD or something like that? Some one please halp!


Thanks in advance!

EDIT: I also forgot to menstion, after burning the disc, it will mount right away on the desktop. HOWEVER, when I take the disc out and try to put it back in, I hear the DVD drive working for like 20 seconds, then it ejects it. No warnings, no mounting, nothing. Mac OS X no likey aparently.

---

### Post by aysiu on 2007-10-24
It has to be burnt as a disk image.

More details here:
[http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)

---

### Post by multifaceted on 2007-10-24
I would first think it's a BIOS issue... but, since you use a Macintosh machine....

Hmmmmm.... I'm not sure if you can access a Mac's BIOS like you can a PC?... At least, I never have been able to. Dang, I know Macs pretty well but, have never needed to get into and configure the BIOS...

I'm stumped here

---

### Post by aysiu on 2007-10-24
For Macs, you have to hold down the *C* key immediately at boot-up in order to boot off the CD.

I still think you're not burning as a disk image.

After you burn it, double-click on the burnt CD and see if you have multiple files/folders or one big file as the CD's contents.

---

### Post by MatthewPlanchard on 2007-10-24
Also, it may make a difference if you burn it to a CD rather than a DVD

most burning progs won't properly burn a cd image onto a larger dvd

---

### Post by WillJeffery on 2007-10-24
> **aysiu said:**
> It has to be burnt as a disk image.

More details here:
[http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)

I'm pretty sure I'm burning it as an image.... I used Disk Utility so.. yeah.

> **aysiu said:**
> For Macs, you have to hold down the *C* key immediately at boot-up in order to boot off the CD.

I still think you're not burning as a disk image.

After you burn it, double-click on the burnt CD and see if you have multiple files/folders or one big file as the CD's contents.

This is what I did: Opened Disk Utility. Draged the "ubuntu-6.x-whatever-powerpc.iso" into the right-column of Disk Utility. Click "Burn". Set burning speed to 1X, and check "verify after blah blah...". Burned it (on a DVD). Shutdown computer. Pressed power button. Held the "C" key until the DVD was ejected.

Yes, when the disk mounted (for the first time after burning was complete) there were multiple files in the disk.



/perplexed :(

---

### Post by Dmart on 2007-10-24
I dont think the DVD is the issue, I burned an .iso on a DVD and it worked perfectly, although I dont have a mac.

---

### Post by aysiu on 2007-10-24
> **WillJeffery said:**
> I'm pretty sure I'm burning it as an image.... I used Disk Utility so.. yeah. I don't think using Disk Utility means you've burnt it as an image. You have to use Disk Utility and then go to **Images** and select **Burn** from that menu, and then select the .ISO you want to burn as a disk image.

As I asked before, please open the burnt CD (double-click it) and look at the contents inside. Do you see one file or a bunch of files and folders?

---

### Post by WillJeffery on 2007-10-24
> **aysiu said:**
> I don't think using Disk Utility means you've burnt it as an image. You have to use Disk Utility and then go to **Images** and select **Burn** from that menu, and then select the .ISO you want to burn as a disk image.

As I asked before, please open the burnt CD (double-click it) and look at the contents inside. Do you see one file or a bunch of files and folders?

What I did to burn it:


[[IMG]http://img91.imageshack.us/img91/2142/picture1copywg5.png[/IMG]](http://imageshack.us)
By [willjeffery](http://profile.imageshack.us/user/willjeffery)



What the disc looks like when mounted.


[[IMG]http://img91.imageshack.us/img91/7650/picture2gp3.png[/IMG]](http://imageshack.us)
By [willjeffery](http://profile.imageshack.us/user/willjeffery)

---

### Post by WillJeffery on 2007-10-25
Bump.

---

### Post by Incense on 2007-10-25
> **cfaulkner said:**
> While I agree with you that OSX is a great OS and I don't wish to start a flame war or call you a forum troll.  But, with this in mind.  OSX is just like linux but looks pretty.  Only thing I don't like about the Macs is the hardware, using Sub-standard parts and charging outrageous fees for them and charging you for the design is not my cup of tea.  

However, back on topic,  Looks like there's not a Installer cd recent for powerpc.  the newest release is 6.06.1

[http://mirrors.kernel.org/ubuntu-releases/6.06.1/ubuntu-6.06.1-desktop-powerpc.iso](http://mirrors.kernel.org/ubuntu-releases/6.06.1/ubuntu-6.06.1-desktop-powerpc.iso)

burn that to a cd and give it a shot.

Maybe give gutsy a go...you need a CDR, but it's a more recent release...

```
http://cdimage.ubuntu.com/ports/releases/gutsy/release/
```

EDIT: I just read that you already got those.... on my MAC I used a prog called [BURN]("http://burn-osx.sourceforge.net/") to burn my ISO. It sounds like you are doing every thing right. I would try to burn the image on a CD rather then a DVD to see if that makes a difference. Just to let you know, you're going to have a bit of a time setting up a dual boot. Reinstalling OSX and leaving a blank partition behind may be you're best bet on that front. The installer has a time shifting around the OSX partitions.

---

### Post by Pumalite on 2007-10-25
[http://ubuntuforums.org/showthread.php?t=185305](http://ubuntuforums.org/showthread.php?t=185305)

---

