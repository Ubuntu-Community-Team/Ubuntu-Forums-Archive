---
title: "Unable to Boot Up"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by tlinux on 2007-05-17
I had a dual boot system with Windows and Mandrake installed. I just attempted to replace Mandrake with Kubuntu 7.04. I used the Alternate LiveCD to install it. I changed the partition areas used by Mandrake to allow Kubuntu to install in those areas. The installation went smoothly and everything seemed to run properly. When finished I attempted to reboot but this failed. I got the following messages:

PXE-E61: Media test failure, check cable
PXE-MOF: Intel Boot Agent
No bootable device--insert boot disk and press any key

I don't have a boot disk and the live Kubuntu disk will not run. No matter what I've tried I get the same three messages as shown above.

I don't know what to do now. Help will definitely be appreciated.

---

### Post by netwerx on 2007-05-17
"PXE-E61: Media test failure, check cable
PXE-MOF: Intel Boot Agent
No bootable device--insert boot disk and press any key"

This error is from your bios.  Perhaps you have lost the boot loader, or in your bios, the boot device list doesn't have your first hard drive on it.  Check the boot order in your bios to make sure the first hard drive is on the list, past that, your mbr (master boot record) or your bootloader is corrupted or missing.

---

### Post by tlinux on 2007-05-17
How do I get into the bios if I can't open either Windows or Kubuntu?

---

### Post by netwerx on 2007-05-17
the bios is the internal setup of the machine, when you first boot, when it shows you information about your machine (ie, cpu, ram, etc) it should say hit ??? for setup.

normally this key can be the "DEL", "F1", "F2" or other key.

---

### Post by tlinux on 2007-05-17
netwerx,

I followed your advice and was able to get into BIOS. I didn't really know what I was looking for, but I didn't see anything that looked unusual. Then I tried again and was able to get the Kubuntu live disk to load. I then proceeded to reinstall Kubuntu, but nothing changed. I still get the same three error messages.

Is there anything I can do with Kubuntu from the live disk that will allow me to diagnose the problem and possibly fix it?

Also is there anything in particular in the BIOS that I should be looking for?

Thank you.

---

### Post by ugm6hr on 2007-05-17
In the BIOS, there will be an option for "Boot Order", which for the time being should be put in the following order for simplicity:
1. CD drive (often IDE 3)
2. Internal Hard Drive (often IDE 1)
3. Floppy Drive
The concern is that the error messages suggest that the computer is trying to access the Hard Drive, but can't find it!  This would mean that either the internal cable or connectors have a fault (or have become disconnected), or that the hard drive has failed (or is about to).  It is interesting that the Live CD allows you to install to the hard drive; this gives the impression that the problem is with the Master Boot Record, which can potentially be terminal too.  If the HD manufacturer has a diagnostics CD available for download from their website - it's worth a try to check.

---

### Post by tlinux on 2007-05-17
In the BIOS the boot order is: 1) TSSTCorp CD/DVDW-TS-H552B  --  AIAPI, 2) GCR-8483B  -- AIAPI, 3) 
ST3160023AS -- 160.0 GB,  and 4) IBAFE Slot 0540 v4110. The computer doesn't have a floppy drive.

Apparently TSSTCorp doesn't have a diagnostic disk available for download.

---

