---
title: "Microcode Boot Error"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by thefowlstar on 2007-03-18
I downloaded the Ubuntu 6.10 Dekstop i386 LiveCD from [http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/) (first link on the page) today and burned it onto a CD using PowerISO. 

After I booted up, I selected the Install/Start option. After the boot screen (with the loading bar) went away, a screen flashed up. It said something about "firmware_helper," "microcode not available," and something about "bcm43xx".

I didn't get to copy all the information down because the screen lasted only for a few seconds.

I'm running a Compaq Presario V6107US laptop, by the way.

Any help will be appreciated.
Thanks in advance. :)

---

### Post by quark_77 on 2007-03-18
Hi thefowlstar,

A microcode is a binary driver, in short and Ubuntu is looking for bcm43xx because that is in all likeliness the driver your wireless card needs. The [relevant documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy") says that there should be generic support in kernel 2.6.17 (you will be using this version on edgy). I would think the live cd doesn't have this microcode loaded as there is only limited space to play with - I use ipw3945, another microcode, which also doesn't load on the live cd to my knowledge - I was certainly unable to go online.

[LIST]
[*]Does the live cd start up (i.e.) can you install ubuntu?
[*]Have you tried checking the disk for errors / MD5 sums
[*]You could use the alternate CD to install Ubuntu. Then, you have a choice. The driver should be installed, or you could download a later copy using synaptic.
[/LIST]

If the disk has no defects and the live cd starts up without issue (Apart from this error - I am assuming this is what has happened) then I would proceed with the install. If you have a network card / cable and network ports on your router, you can use wires temporarily to download the appropriate files. See the documentation above - I'm sorry, but I can't guide you through fwcutter installs but I can do ndiswrapper!

Hope this helps,

Quark_77

---

### Post by thefowlstar on 2007-03-19
Hey quark_77
First of all, thanks for the help.

I can boot up the live cd up to the selection menu (where you select, install/run/low graphics, etc.) but I can't load the desktop or install it. I tried it with the limited graphics mode and even tweaked around with some of the settings, but it won't work. My laptop (Compaq Presario V6107US) screen resolution is 1280 x 800. It's just a wild guess, but do you think that could be a problem since I didn't see that resolution in the resolution menu down at the bottom and kept it to its default VGA selection.

I'm currently downloading the alternate edgy version to see if it works and will post the results.

Just in case any of this helps, here's my laptop hardware info.

[LIST]
[*]AMD Turion 64 Mobile Tedchnology MK-36 (x86) Processor
[*]NVIDIA GeForce Go 6150 Video Card
[*]1280 x 800 Display
[*]Broadcom 802.11b/g WLAN - Packet Scheduler Miniport Network Card (bcmwl5.sys driver)
[/LIST]

Thanks again for the help!

thefowlstar

---

### Post by quark_77 on 2007-03-21
Hi thefowlstar,

I think the problem might be the fact that you downloaded the i386 version. Your AMD Turion 64 Mobile supports the [[COLOR="Blue"]_x86-64 bit architecture_[/COLOR]]("http://en.wikipedia.org/wiki/AMD64") which having read the article on Wikipedia may not, in AMD implementations, be able to load 32-bit microcodes, which would explain your problem. As much as I loathe to suggest you download **another** ISO image this may be necessary, unless the alternate installer worked, that is? It might do, as x86-64 processors are supposed to be backwards compatible with the x86 architecture... at least that was my understanding. Perhaps that is only the case in the windows world.

[COLOR="Gray"]If you do have to download a new ISO, you want one from the "64bit AMD and Intel computers" section on the new download page, or from [http://releases.ubuntu.com/6.10](http://releases.ubuntu.com/6.10) you want this one: "64-bit PC (AMD64) desktop CD".[/COLOR]

I don't think your display resolution should be a problem, the drivers Ubuntu defaults to for graphics support nvidia out of the box in most cases, at a number of resolutions. These drivers should decide which resolution they can run at by themselves by finding the highest one that works. My Dad's PC runs Ubuntu on nvidia without problem. 

Is the vga option something like vga=x where x is a number 0-7? If this is the case, I think this  simply indicates what mode the kernel should try to use on the bios - i.e. 80x23 lines (DOS!) or something better, such as 80x40. By these numbers I mean lines of text/columns of text...

Post back if you get a working install...!!

Hope this helps, again!

Quark_77

---

### Post by thefowlstar on 2007-03-24
Hi quark_77:

Sorry, I'm late; I had a really busy week. Anyways, thanks for looking all of this up. Fortunatly, though, the Alternate installation was successful in text mode. However, the internet won't work, even with LAN. I'm going to try and use fwcutter since it seems so much easier than ndiswrapper to get the firmware. I'll let you know if I need any more help though. (I'm writing this from Vista; I was trying to triple-boot XP, Vista, and Edgy and it seems to be working now.)

And, again, thanks for all this help!

thefowlstar

---

### Post by JulienPDX on 2007-10-18
I am posting here because I just made a similar post and am having the same problem this person is.  I too, get a very fast microcode error that I cannot read because it goes by too fast.  

I did however, (in all cases, with each version 6.06--7.10) download the correct ISO of the amd64 version and have the same stats as the OP.  I have run defect checks on all iso's i've downloaded and not a single one wants to boot up correctly.  it would seem rather odd to me that a network driver not loading correctly would lock up the entire boot process.:(

---

