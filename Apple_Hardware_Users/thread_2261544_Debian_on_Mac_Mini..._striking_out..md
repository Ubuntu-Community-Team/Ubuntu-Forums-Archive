---
title: "Debian on Mac Mini... striking out."
date: 2015-01-19
forum: Apple Hardware Users
---

### Post by Roasted on 2015-01-19
Hello friends. I'm trying to install OpenMediaVault on an old Mac Mini. OMV is based on Debian stable. I've tried both OMV and Debian stable and they install fine, however once the system completes and reboots, it comes back up to a flashing folder with a question mark. It seems like it's just a boot loader oriented issue, however grub installed fine during the installation (and by that I mean, I just didn't receive any errors).

I'm trying to figure out how I can work around this. I can either install OMV itself with its own ISO or install Debian stable and then pull in the OMV repo. Either way, same basic result.

Most guides I find online (which constitutes a good 99% of them) say to boot into OSX and install refit, or the new-ish forked version of refit known as refind, I believe. Either way, this is assuming OSX is on the system. In this case, it's not. I'm working with bare metal and a blank drive.

Anybody have any ideas of what in particular I can check?

For what it's worth, during the Debian installer I used automatic partitioning. I noticed that it was creating partitions in a familiar arrangement that Ubuntu MATE had done so on my iMac with the 1MB partition first, etc etc. I took this as a good sign but, like I said, struck out with the flashing ? folder upon the initial boot.

This Mac Mini is an older Core 2 Duo unit. I'd assume 2009-ish, though I am not overly positive. It's one of the white units. It's not the shorter-but-wider all aluminum Mac Minis that you see available today. 

What say you, folks? Any ideas?

---

### Post by este.el.paz on 2015-01-23
@roasted:

In the past when I used "automatic" on my MBPro the install would seem to go "well" or "successfully" . . . but, on reboot, would not load GRUB.  So, lately I've taken to "manual" . . . with the 1-10MB partition labeled "bios_grub" . . . then home (ext4) and then swap . . . but, I'm now triple booting with OSX, so I use rEFInd.  Apparently now you don't "need that" but seems to take some CLI chops to set it up.  I like simple/easy . . . .  But, without manually setting up that "bios_grub" partition, it says "install complete" on my Core2Duo MBPro . . . but doesn't "work."

e.e.p.

---

### Post by Roasted on 2015-01-23
Thanks for your reply. I actually just got this figured out last night. I noticed this on the Debian MacMiniIntel Wiki page:

```
With the mid-2009 (macmini 3,1) model, you need a "testing" installer to get a recent enough kernel for reboot to work (with kernels from lenny and prior a hard power-off is needed after shutdown). 
```
from:
[https://wiki.debian.org/MacMiniIntel](https://wiki.debian.org/MacMiniIntel)

Guess which Mac Mini I have? Yep. I have the exact 2009 3,1. Imagine that.

OpenMediaVault is based (currently) on Debian Wheezy, which boots from kernel 3.2. I have no idea how it was okay with booting to the installer and installing the operating system, but not booting post-install, but that's what I was facing. At first I thought about pulling the drive and putting it in another system to install, then upgrade kernel, then put the drive back, but the Mac Mini is time consuming enough to take apart... I took another approach.

I installed OpenMediaVault in a virtual machine on my laptop first. I upgraded the kernel via backports using OMV-Extras (a popular add-on to OMV which brings in more plugins, though you could also add backports via Debian's repo). This brought my kernel from 3.2 to 3.16. After that, I powered down the VM and booted it to Clonezilla Live and saved an image from the virtual machine. I took that image, which again was just OMV + backports 3.16 kernel, then put it on a flash drive, booted up the Mac Mini to Clonezilla Live CD, and imaged it. It worked perfectly. I just booted to GParted after to create a second EXT4 partition for data, since the Mac Mini is a little single drive unit and by default OMV uses the entirety of the main drive it installs to. (the intention is to have the OS separate from the data, which makes complete sense with a NAS, but isn't what I was after in this case with the Mini being a single drive unit)

In regard to your suggestion, I've seen the Debian *and* Ubuntu installer automatically create that little partition at the beginning that you mention (assuming you choose "automatic partitioning" in the menu). I did not do that in this case. I just did swap, EXT4 for root, and EXT4 for data afterwards and it worked. In the event that didn't work I was going to try the VM idea with the little partition in the beginning, but I was already working through the installer when I remembered I forgot to do that. That being said, in this case, it worked without it (perhaps only newer Macs/UEFI systems need it? Not sure...). 

Thanks for your assistance. :)

---

### Post by este.el.paz on 2015-01-23
Glad I could help out . . . it's certainly a lot easier when the OP figures out how to fix their own question via their own answer--then there is no "resistance" to the "solution" . . . .  Main thing is, if it's working, it's working.

e.e.p.

---

