---
title: "Bless on Linux"
date: 2012-06-07
forum: Apple Hardware Users
---

### Post by tilllt on 2012-06-07
Hey,

i am - for some strange reasons - running Ubuntu 12.04 and Windows 7 on my Macbook Pro 5.5...

Actually the Lid Sensor got damaged for some liquid spill and the machine thinks the Lid is always closed, causing OSX - even during installation - to immediately enter sleep mode. 

So far the only solution to run OSX would be to run the machine with an external monitor, which i dont have, so i ended up using a non Apple OS on my Apple computer: Both Ubuntu and Windows are friendly enough to let me decide on my own what the comp should do when the lid is closed.


Initially i had some problems with the partition scheme to run a Ubuntu / Windows 7 dual boot and it still is kind of a mess as i have to run reFit from a USB stick, looking for bootable OS on an MBR Partitioned Disk only... whenever i tried to use GPT or GPT / MBR Hybrid, things started getting nasty. So far only the MBR solution worked kind of OK.

The reason for installing reFit on the USB stick is that the instructions just descibe how to install via OSX, which i cannot run. Same for refind.

A big part of the problem is connected to the "bless" command apparently only available on OSX. And this makes me wonder: Is it not possible for some Mac Loving Linux coder to compile the darwins "bless" code for Mactel Linux?

I guess this is the sourcecode no?
[http://opensource.apple.com/source/bless/bless-46.1/](http://opensource.apple.com/source/bless/bless-46.1/)

Maybe somebody knowledgable is kind enough to take a look at it!

bye,
t.

---

### Post by metatechbe on 2012-06-09
> **tilllt said:**
> A big part of the problem is connected to the "bless" command apparently only available on OSX. 

"hfs-bless" does exist on Linux in the "mactel-boot" package :
[https://bugzilla.redhat.com/show_bug.cgi?id=755093](https://bugzilla.redhat.com/show_bug.cgi?id=755093)

metatech

---

