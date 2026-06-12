---
title: "Seagate SCSI tape drive woes..."
date: 2006-09-13
forum: Apple PPC Users
---

### Post by jave on 2006-09-13
Hello,

I'm having trouble getting Ubuntu 6.06 to recognise a Seagate STT320000N SCSI tape drive which I have set up externally on my G4 MDD.  After searching around the forum for help I have done the following:

1. Added st to the /etc/modules file and rebooted.
2. Installed mt-st using "sudo apt-get install mt-st".
3. Ran "sudo /dev/MAKEDEV -v st0". No errors are returned.

After all this, I try to check the status of the tape with "mt-st -f /dev/st0 status" and it tells me that there is no /dev/st0 device.  So I take a look in /dev and find that there is no st0 file. dmesg lists my PCI SCSI card ok, but it doesn't list my tape drive as being connected.... :(

I'm suspecting a dud tape drive, as I bought the drive off eBay for under $10 (Australian - including postage), so the chances of this are pretty high. :-k

So I guess my question is, how do you test for a dud drive?  When I boot up OS X and run System Profiler, the PCI SCSI card is listed, but not the tape drive. Hmmmm...

Also, how do you remove a tape manually?  Is it possible?  :oops:

---

### Post by ristosu on 2006-09-14
1. Check (lsmod) that st module is loaded.

3. Looking at the MAKEDEV script on my older Ubuntu installation, makes me think that the device file (handle) should be created somewhere, possibly in /.dev, if udev is running. Note the following (from MAKEDEV man page):
"Note that programs giving the error ``ENOENT: No such file or directory''  normally means that the device file is missing, whereas ``ENODEV: No such device'' normally means the kernel does not have the driver configured or loaded."

---

### Post by jave on 2006-09-16
Mystery solved...  I was surfing around and found an interesting article on Adaptec's website.  It says to turn on any external SCSI devices BEFORE you boot up.  Tape drive is being recognised now.  As for removing the tape, you just pull it out when the "in-use" LED is out...  Easy once you know how. :grin: :grin: :grin:

---

