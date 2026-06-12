---
title: "installing ubuntu on an imac with no os"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by shill on 2007-11-11
2 imacs with NO os.
384 Ram
CPU:  400 & 500
HD:  13gig and 30gig

Ubuntu hangs on install, base system is corrupt.

Checked the md5sum, burned the 6.6 and 7.10 alternate with infra recorder (not live cd, it did not load, computer shut off).


Tried this on a G3 mac with very limited ram some months ago, it had no os either.  
Also tried live cd on older AMD windows box, hung up, could not complete.

Posted in Power PC forum no answers.  Any other steps to follow, should I try different distro?

---

### Post by magicman5421 on 2007-11-11
have you tried reformatting the hard drives?

---

### Post by shill on 2007-11-11
no, just re-inserting the cd and trying to start the process over.

How do you reformat without an os?

---

### Post by jrharvey on 2007-11-11
If you are using the live cd then when you get to the partition editor part of the install the you must select the format box next to the ext3 partition. Im not sure about the alternative cd since i have never used it.

---

### Post by Dr Small on 2007-11-11
> **shill said:**
> no, just re-inserting the cd and trying to start the process over.

How do you reformat without an os?
Use the gParted CD to reformat the hard drives without the OS.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by magicman5421 on 2007-11-11
I don't know if you can do it through bios, and i'm inclined to think not. You could plug the drives into a working desktop and format them from there, or get a hard drive caddy and format it via usb with another computer.

---

### Post by magicman5421 on 2007-11-11
> **Dr Small said:**
> Use the gParted CD to reformat the hard drives without the OS.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

or you could do that

---

### Post by maharbA on 2007-11-11
If you can boot the live CD (so you see the desktop, etc.) you can use gparted in SYSTEM>ADMINISTRATION>PARTITION EDITOR or some such name to do basically whatever you want to the HDs.

Just curious, are you using the PPC version of Ubuntu (there's a x86, and AMD64, and a PPC verion) If not you can get it here:
[http://cdimage.ubuntu.com/ports/releases/7.10/release/](http://cdimage.ubuntu.com/ports/releases/7.10/release/)
or you can probably find a torrent somewhere.

Best of luck

---

### Post by shill on 2007-11-11
The live PPC 7.10 did not boot, have read to start with 6.6 alternate ppc.  I get thru the install to libc6  of the base system set up and get the corrupt error red screens.

Did just repartition the ext3 directory and went thru the install.

Did choose oem and the command prompt instead of the default install.  Still libc6 error.

FYI:  While trying to install ubuntu I have the ethernet cable attached to our linsys 8 port router and the imac.  That would not throw off the install would it?

---

