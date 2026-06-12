---
title: "Ubuntu Mac Edition?"
date: 2011-12-28
forum: Apple Hardware Users
---

### Post by rfkrocktk on 2011-12-28
Can someone explain this to me: [http://cdimages.ubuntu.com/releases/oneiric/release/](http://cdimages.ubuntu.com/releases/oneiric/release/)

It seems that the very first download is tweaked for installing on Mac hardware. How did I not come across this before? 

Are there any major differences? Could I get a list of what's different? Is it possible to patch my current Ubuntu install with the CD?

---

### Post by Symbolix on 2011-12-29
Yeah, you are right. I came across it couple of days ago and yes: no body mentions about it which is annoying. But it works. So 10.04.3 will not install on my iMac (Early 2009), due to nvidia issues. I managed to install all 11.10 (64bit+mac) versions. Kubuntu 11.10 will still need the nomodeset tweak at install time. However I found all 11.10 a bit ugly and too much eye candy. Coming from Ubuntu 7.04 myself. So will try Xubuntu now.

---

### Post by rfkrocktk on 2011-12-29
Since I'm on a 8,3 MacBook Pro, Ubuntu Mac edition doesn't really help me much, as I've discovered. Best compatibility comes with standard 11.10 amd64.

---

### Post by wiz561 on 2012-01-03
Hi!

I was wondering if anybody has any more information about this.  I just stumbled across this ISO today and have had lots of issues with my macbookpro 3,1.

It's also confusing because most intel macbooks come with a 64 bit processor, and the FAQ in the forum says use the 64 bit version, and everything else I've read says use the 64 bit version.  However now, on the releases document, it says to use the x86 version.

[http://releases.ubuntu.com/11.10/](http://releases.ubuntu.com/11.10/)

Did something change?  Maybe there still is hope with a working ubuntu version on my mbp.

Thanks!

---

### Post by rfkrocktk on 2012-01-03
Use 64bit. Trust me, it's worth it.

---

### Post by wiz561 on 2012-01-03
I'd use the 64bit version of ubuntu, but I can't get it to boot.  I started another thread about this in the apple subforum.  Going to try a the 'mac' version of ubuntu tonight....

---

### Post by rfkrocktk on 2012-01-03
Yeah, as far as I know, the older MacBooks have different hardware that isn't compatible out of the box, hence the MacBook edition of Ubuntu. For new MBPs (8,1|2|3), it's not so much of an issue. In hindsight, things for the most part worked well, with the exception of screen brightness and WiFi.

---

### Post by wiz561 on 2012-01-05
Thanks for the info.  I was having that problem where Ubuntu installed fine, booted up grub, and then when grub tried to load the kernel, things just locked up.  The mac version solved it.

It would still be good to know what was different or what had been added to the "mac" version of Ubuntu.  How do you go about trying to figure this out?  I would assume there's some sort of changelog somewhere.

Thanks!

---

### Post by rfkrocktk on 2012-01-05
Good question, I'm really not sure what makes Mac Edition different.

---

### Post by Seq on 2012-01-05
[Colin Watson answered this on Ask Ubuntu]("http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image")

> In Ubuntu 10.10, we changed the normal amd64 CD images to dual-boot on either BIOS or UEFI systems (UEFI, "Unified Extensible Firmware Interface", is a different kind of firmware found on many newer systems). This was done using a technique known as a "multi-catalog" CD - it contains two boot images, and the specification says that the firmware is supposed to pick the one it can best use.

Unfortunately, even though Macs use a variant of EFI (an earlier version of what's now called UEFI), they apparently can't cope with multi-catalog CDs, and simply refuse to boot them. This left us in rather a quandary: we needed to support UEFI systems, but we didn't want to drop support for Macs either. I therefore created the amd64+mac CD images, which are exactly the same as the amd64 images except that they only support BIOS booting. Macs are happy to boot these in their BIOS emulation mode.

---

### Post by mw1coe on 2012-01-06
I installed using the mini.iso cd on my Emac.

I then installed the Lubuntu Desktop as I found Ubuntu and Kubuntu to be a little slow on my machine.

I found no issues with the Install and also found all things to be working excellent apart from a small issue with maybe the Screen Size but I think that may be a hardware (Monitor) Issue as opposed to any Lubuntu Problem.

I hope this continues as it gives new hope to older Power PC Machines that would otherwise be left to rot with an older and almost unsupported version on Mac OS.

Rob..

---

