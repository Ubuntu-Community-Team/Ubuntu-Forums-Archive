---
title: "new install and mouse freezes up on the occasion"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2006-10-18
I just installed ubuntu on an amd64 (dell) and have noticed that the mouse locks up every now and then and stays that way until I unplug it and then plug it back in.  I swapped it with another mouse, but noticed the same thing.  Is this a fixable problem?

Thanks for the help.

---

### Post by chris.olsen on 2006-10-20
bump

If I don't find a way around this I will have to re-install windows.  Please help.

---

### Post by localuser on 2006-10-20
What kind of mouse is it?  USB?  Wireless?

---

### Post by chris.olsen on 2006-10-20
I have tried it with 2 different mouses, the first one is just the generic model that came with the dell and the other is a logitech trackball mouse.  I have tried all the different usb ports (front and back)

This guy is having the exact same problem on pretty much the exact same model of computer
[http://www.ubuntuforums.org/showthread.php?t=279626](http://www.ubuntuforums.org/showthread.php?t=279626)

---

### Post by rlozano on 2006-10-29
what's your graphics card?

---

### Post by Jott on 2006-12-27
Not to but in, but I'm having the exact same problem, with a fresh install of edgy on a Dell Dimension E251, AMD x2 processor and Nvidia graphics on board.  Tried 2 different mice, and two different usb ports.  I had the same problem on an old dell (P4 processor, integrated intel graphics) at work, got around it by using one of those old whatchyamacallim (serial?) mice instead of usb.  The Dell I use now is too new to have those old ports though, so I really need to deal with this.  Hope someone has an idea?

---

### Post by vguhesan on 2007-01-03
I have the exact problem:

Mouse locks up after some use. When I unplug and wait for a few minutes and replug into a different USB port it works again for sometime and then locks up again.

Dell Dimension C521 - AMD64 Athlon - Ubuntu 6.10 Edgy Eft

Link to Dell product specifications:
[http://www.dell.com/content/products/productdetails.aspx/dimen_c521?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/products/productdetails.aspx/dimen_c521?c=us&cs=19&l=en&s=dhs)

I'm using the USB Dell mouse that came with it. No serial mouse port available.

Any help is greatly appreciated!!!

-V-

---

### Post by Jott on 2007-01-03
There's another thread on this problem with the Dell E521 here:

[http://www.ubuntuforums.org/showthread.php?t=279626&page=8](http://www.ubuntuforums.org/showthread.php?t=279626&page=8)

it looks like there's a BIOS update that MAY take care of it - I haven't tried it myself yet, so I can't vouch for it's efficacy.  I installed a PCI card with USB slots, which seems to take care of the problem, so I'm not in such a hurry anymore, but I may try it anyway.  

Good luck.

---

### Post by vguhesan on 2007-01-04
Hello All: I posted a few days ago about the problem and a few folks have suggested that I upgrade my Dell Dimension C521 's BIOS...

Here is a link to the BIOS... (as of Jan 04, 2007)
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R142795&SystemID=DIM_P4_C521&os=BIOSA&osl=en&deviceid=308&devlib=0&typecnt=1&vercnt=4&formatcnt=1&libid=1&fileid=190570](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R142795&SystemID=DIM_P4_C521&os=BIOSA&osl=en&deviceid=308&devlib=0&typecnt=1&vercnt=4&formatcnt=1&libid=1&fileid=190570)

There may be newer BIOS released so it's best to goto Dell's "Support" site and search.

Here is my question:
- I have Ubuntu installed.
- The Dell BIOS update file is a DOS .exe file.
- My computer DOES NOT have a floppy drive.

How do I run the file and/or create a boot disk to run the ".exe"?

Any suggestions???

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

### Post by Zer0Nin3r on 2007-01-21
> **bodzasfanta said:**
> Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you


Tried this and the system would just hang up during the boot up.

---

### Post by magicfab on 2007-01-24
A similar issue on E521n was fixed by  recent BIOS upgrade from Dell. See:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

