---
title: "Epson Stylus CX5000 printer"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2006-10-31
I was wondering if anyone has this printer working under Edgy (or Dapper, if it matters). The printer is a "More-in-one" Scanner, printer, copier, computer-less print from camera/memory card etc. I don't care about the scanning; the rest is done without a computer. All I really care about is printing.

Any ideas? Any possible leads? The gutenprint drivers has drivers for a CX4800, CX5100, CX5200 etc...no CX5000.

Thanks

---

### Post by Coburn on 2006-11-19
I'm with you there.  I just bought one--or rather it was a birthday present--and am working on getting it going right now.

linuxprinting.org says that Epson printers in general are fully supported.  They don't list the CX5000 either, but most likely it uses the same basic driver as similar models.

Looking forward to either getting mine working first, or hearing good news from you.

OK, update:

I got it to print a test page.

What I did that made it work was use the CX4800 driver.  The 5100 was just kicking the printer into a hang mode doing endless formfeeds.


**FYI**--for visitors who _are_ interested in **scanning**:

 I also installed sane, sane-utils, and libsane-extras (I already have libsane...) to make sure I could scan.  BTW it does but now I have to figure out how to access xsane as a regular user.  Only root works right now....

OK, System > Device Mgr. > USB > CX5000 > Advanced says it is /dev/usblp0...

But chmod has no effect. <sane-find-scanner -L> still only finds it as root.  Which is supposed to mean that I need to "adjust device file permissions."

That's frustrating.  I am not a Certified Ubuntu Professional, guys.  I have no clue what device files that is referring to.

<found USB scanner (vendor=0x04b8, product=0x082b) at libusb:001:004>

BTW I already put those ID's in the epson.conf file, along with a line at the end for enabling the scanner.  I'm pretty for sure I did it right.

PS adding myself to all applicable groups also did not work.

Update:  Scanner success!

It was as simple as changing device permissions.  For some reason this type of scanner does not automatically load the drivers to be usable by anyone but root.  I guess that is a legacy of other distributions which assume you perform administrative tasks as root.  The developers have a very thorny problem, switching over in an exhaustive manner to the Ubuntu Way.

The thing that threw me was, I changed permissions on /dev/usblp0, all right, but I was too lazy to bite the bullet and also change them on /sys/devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.1.  Both were in the Advanced list under System > Administration > Device Manager.

Works beautifully.

---

### Post by jevharr on 2007-08-24
I am trying to get this same model scanning. I can run xsane, but I get the "no devices available" error. This is printing just fine, but I cannot scan yet. I attached the HAL output.

Thanks,
J--

---

