---
title: "Debian Squeeze - EMGD"
date: 2013-01-16
forum: Any Other OS
---

### Post by Adam_GUI on 2013-01-16
This isn't mean to stir stuff up, believe me.

I have a Dell Inspiron Mini 1010 - Poulsbo chipset.
Latest ubuntu renders the correct video resolution very slowly.  Which is alright.  But, I'm missing the EMGD.  Since that driver gets a good scolding in the GMA500 thread, I decided I'd take a trip into the past.
I realize this machine has problem hardware and doing this I'm largely on my own, but I need a second set of eyes.

Debian Squeeze gets me into a VGA ratio display.

I wanted to install EMGD 1.16, but cannot.
The package from Intel's site [Linux Tarball]("http://www.intel.com/p/en_US/embedded/hwsw/software/emgd") version 1.16 does not include an install.sh file.  Converting the Fedora 14 rpms with Alien to deb lets things install, but nothing change.

So, I checked their archives.
A [Debian Wiki]("http://wiki.debian.org/IntelEmbeddedMediaGraphicsDriver") page says that things work with version 1.5.2.
That version is not on Intel's archive.

What I did manage to download was version 1.14 and version 1.10.
1.10 has a group of PDF files and an EXE file containing some odd files in Squeeze.  So, I skipped it.

Version 1.14 of the EMGD package has an install.sh.  Paydirt.
I had to enable Squeeze backports and pull XServer 1.10 (A version ahead of the 1.09 the driver asks for and two versions ahead of the 1.08 shipped in Squeeze) and kernel 2.6.30-5 something.  My memory is fuzzy and I'm away from the machine for now.

After making the debian wiki changes to the install.sh file and running "./install.sh -v" I can get most of the way through the 1.14 installation before it errors out complaining about linux/vga_switcheroo.h.

That was as far as I got before pulling something stupid and installing the IMGD ubuntu packages where I broke apt because I was in a hurry.

It's not a giant deal.  I'm starting from scratch again tomorrow and can get it that far back up to snuff.  I just don't know where to go about vga_switcheroo.

Any ideas on the puzzle?  Or an archive of the Intel 1.5.2 driver?

---

### Post by mips on 2013-01-17
Maybe try one of the .debs from here [https://launchpad.net/~gma500/+archive/emgd](https://launchpad.net/~gma500/+archive/emgd) , just check which version of ubuntu was more or less based on Squeeze. Manually download the deb.

---

### Post by Adam_GUI on 2013-01-18
Since I'd borked apt pretty badly I had set out with two game plans for the machine.
Live editions of SimplyMepis and LinuxMint Debian Edition.

I used dd to create flash drives for both.  SimplyMepis never booted.

LinuxMint Debian Edition got me to a correct desktop at kernel 3.2.
I tried compiling EMGD 1.14 again anyway with no luck.

But, turning on XFCE's compiz box helps with jitteryness and video playback in Google Chrome is acceptable.  I'm really impressed with Linux Mint Debian Edition.  I really hope they keep it up.

The Dell Insperon Mini 1010 works well enough to be rather usable again.
More than good enough for typing, web surfing, skype, and file transfers.

So, let this be a beacon of google-fu for anyone crazy enough to try what I was trying and not able to find the EMGD 1.5.2 that was supposed to be working in Debian Squeeze.

---

### Post by mips on 2013-01-18
Have you considered trying Debian Wheezy (upcoming v7), it's currently in freeze state and should be release *soon*.

---

### Post by Adam_GUI on 2013-01-18
> **mips said:**
> Have you considered trying Debian Wheezy (upcoming v7), it's currently in freeze state and should be release *soon*.

I did.  But, I couldn't find an installer on Debian's webpage.
All I could find were installers for stable Squeeze.  That could just be on my head for not looking in the right spots.  But, I didn't want to re-install squeeze just to mess with my sources.list and let synaptic run forever.  It's part of the reason I went with LinuxMint Debian Edition in that I had assumed it was spun from Debian Testing instead of Debian Stable.

Instead, LinuxMint DE is running from their own repos.  I'm letting the machine stay as it is for now.  It's in acceptable state for me.

---

