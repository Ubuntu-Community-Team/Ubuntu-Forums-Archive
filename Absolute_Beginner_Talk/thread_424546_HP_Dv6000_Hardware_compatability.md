---
title: "HP Dv6000 Hardware compatability"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Captain Carrot on 2007-04-26
I have been trying to install a variety of Linux distros on my hp dv6000 notebook, and so far nothing has worked out for me. I am trying to download Kubuntu 7.04. I tried to boot the desktop copy and I was told I had a bad kernel. So I am downloading another copy (my third if you count ark linux, which apparently doesn't support partitioning) and I was just wondering if anyone had used my particular computer before with this distribution. I would appreciate any help with getting Linux to work.  :)

---

### Post by Kobalt on 2007-04-27
I have a HP dv6000 laptop and it works quite nicely on Ubuntu. But you need to boot with noapic nolapic options to get it installed.
Start your computer with the Live CD inside your drive. When you get to the first Ubuntu boot screen press F6 to access *Other options* and add at the end of the line (and after a space) : *noapic nolapic*
Finally press Enter to boot.

If you need help on installing the wifi, your webcam or the card reader here is a couple of helpfull link : 
[http://ubuntuforums.org/showthread.php?t=363211](http://ubuntuforums.org/showthread.php?t=363211)
[http://ubuntuforums.org/showthread.php?t=363211](http://ubuntuforums.org/showthread.php?t=363211)

Welcome to Ubuntu :)

---

### Post by ookook on 2007-04-27
I used the following guide and it worked to perfection...  Kudos Teaker1s et al.

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29)

As noted above the noapic noapci commands are required to boot live cd and install.  I added irqfixup but do not know result of omitting.

30 min. to install and get networked.  4-5g of hd used.

Ndiswrapper *really* is the preferred method for wireless.  Wait for keyring to initialize after rebooting or restarting networking.  I could not help myself and starting mucking with interface file etc when I just needed to let keyring do its thing...

Feisty does a very good job of recognizing hardware relative to nvidia drivers etc so you may not have to do much beyond the first 2-3 items in this guide.  beryl and aiglx = sweet, sweetness...  Set preferences desktop effects to let FF do the job of popping in video driver.

My machine:
HP DV6105us - ML36, 2gRAM, 80g, 1390WLAN Card (seen as Dell 1390 by lspci)

Currently monitoring heat/fan but all looks good at this point.

Ook

---

### Post by firecat53 on 2007-04-30
Did any of you get suspend to ram or suspend to disk working? I just get a black screen and it never turns off. Also tried uswsusp from the repostiory--same result. 

Scott

---

### Post by Cywolf1 on 2007-08-10
To all folks out there looking for an APIC/ACPI solution for Ubuntu AMD boot lockup problems:

My Hardware:
HP dv6324us
Gutsy Distro (Tested with feisty, seems to work)
2.6.22 Kernel
AMDx2 - 1.6
Nvidia 6150
Nvidia chipsets (All the goodies on HP)
bcm43xx driver
etc...

After many weeks of searching through kernel documentation, I think I may have found a permanent soluton to the kernel boot problem. Most people can temp. resolve the problem with either noapic noacpi or other kernel options that disable or impair the apic/acpi on the system. Fear no more the loss of IRQs, use more than 2 usb devices all at once, and free yourself from the random loss of your wireless cards............... okay so now that everyone is anxious...simply append this to the kernel boot option

pci=conf1

so for the ubuntu (linux) rookies...
when grub boots, press esc to stop boot on a grub menu, press e on the kernel line, and at the end of the line append "pci=conf1" without the quotes....then press enter, and then b, and witness the glory.

It almost seemed too simple, and I nearly cried when the system booted up faster and smarter. I've got all my APIC set to fasteoi and some on edge triggered, just like it should be. I've also got all 8 USB ports found, full working display, wireless, nics, USB 2.0, and even my battery stats appear to be more accurate. I am also using compiz and it's running ten times faster (cause the kernel is not tweaking out). Oh it's sheer beauty....I rarely post, but I figured it was time to share the love. I know that I will be making so many folks with HP dv6000 series or other HP model owners supremely happy!! I know I AM... YEAH. Hopefully the fix works on other platforms with similar issues.


Cyber///olf

Posted here as well -->
[http://ubuntuforums.org/showthread.php?p=3164902&posted=1#post3164902](http://ubuntuforums.org/showthread.php?p=3164902&posted=1#post3164902)

---

