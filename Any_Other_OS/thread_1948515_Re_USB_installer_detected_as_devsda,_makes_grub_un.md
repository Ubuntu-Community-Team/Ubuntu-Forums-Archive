---
title: "Re: USB installer detected as /dev/sda, makes grub unhappy"
date: 2012-03-28
forum: Any Other OS
---

### Post by krustybaguette on 2012-03-28
> **j8kel said:**
> For my purposes, I needed to be able to create a usb stick that could do automated install without user intervention.  I needed the same installer to work on dell appliances that named the usb drive /dev/sda and /dev/sdb.  The solution I found to this was opening the initrd.gz and adding some rules to /etc/udev/rules.d.

When I build the usbdrive, I apply a label to it, either using dos's "label", or linux "mlabel" or "makedosfs".  The rules I embedded into the initrd check for this label being recognized as /dev/sda, and if so, switch it with /dev/sdb.

This happens in time for the installer to proceed normally as though the usb drive was discovered as sdb to begin with.

The rules file is named 99-install.rules and the contents look like this:

```

KERNEL=="sda*",ENV{ID_FS_LABEL}=="INSTALL",NAME="sdb%n"
KERNEL=="sdb*",ENV{ID_FS_LABEL}!="INSTALL",NAME="sda%n"

```

This looks interesting but I'm trying to correct a sdb~sda switching problem that exists POST installation. My primary drive is sdb when I have two hard drives installed (the second is via a multi-bay adapter) in my Lenovo X60 docking station. The primary drive gets renamed sda when I swap out the second drive to use the DVD burner OR if I just remove the laptop from the docking station. At that point I cannot boot Linux Mint although Win7 will still boot.

I suspect this situation arose a few months ago when I installed LM9 via a bootable USB stick while BOTH hard drives were present in the system. I did this because the LM12 "upgrade" was unsatisfactory due to Gnome issues, and other problems. Only later, when I wanted to use my laptop detached from the docking station did I discover the sdb~sda swapping problem.

Now I seek a cure. It looks like a udev rule might solve the problem, but I wonder if reinstalling LM from the DVD drive rather than the USB stick might also solve the problem.

krustybaguette

---

### Post by Perfect Storm on 2012-03-28
Moved to Other OS/Distro Talk.

---

