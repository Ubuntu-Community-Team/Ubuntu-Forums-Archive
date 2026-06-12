---
title: "Info about Intel Macs at Ubuntu Live"
date: 2007-07-25
forum: Apple Intel Users
---

### Post by benanzo on 2007-07-25
So I was at Ubuntu Live this week and had an opportunity to talk to a couple of the Ubuntu kernel developers about running Ubuntu on Intel Macs.  A couple of the questions I asked were:

1) How close are we to booting with EFI?

The answer: Not close at all.  Apparently Apple hasn't fully implemented Intel's EFI specification especially regarding how to get video information so X can start up with a usable resolution.  So don't work too hard on that (like I did.)

2) Is it safe to get rid of the 200MB EFI partition at the front of the disk?

The answer: Yes, but only if you're not booting OS X.  It is not safe if you use OS X to install firmware updates.  Although OS X doesn't boot from the EFI partition, Apple does use it to install firmware updates.  Apparently when OS X downloads a firmware update it copies that package to the EFI partition, sets it as the boot partition then when you reboot to install it, it boots from that partition and runs the update.  When it is done it changes everything back to normal.  This is somewhat contradictory to my experience.  I remember running firmware updates even after I repartitioned the disk as pure MBR (no EFI part.) without any problem.  However, it is advisable to keep that partition around if you use OS X to update your firmware.

 I only boot Ubuntu on my machine, so I have no need for that partition.

---

### Post by cyberdork33 on 2007-07-25
> **benanzo said:**
> Apparently when OS X downloads a firmware update it copies that package to the EFI partition, sets it as the boot partition then when you reboot to install it, it boots from that partition and runs the update. 

That sounds really logical, but I would think more people would complain that updates weren't working if that was the case. Oh well, I kept mine in place for a reason!

---

### Post by Gen2ly on 2007-07-25
The definitely makes sense to use the EFI partition for firmware.  I'm really surprised thought that is all it does.  Nice work finding all this out.  Since I have a original MacBook, I'm pretty comfortable with not worring about firmware updates.  My OS X partition is growing older and less and less used.  I'll probably ditch OS X one of these days if I suspend the great temptation to try 10.5, and reclaim that space and try your method of install.  With all this EFI crap not in the way I can make my partitions resonable.

---

### Post by ivesjd on 2007-07-25
Very nice info. Would be cool to have been there too. :D

---

### Post by chem on 2007-07-26
I just hope some of their devs can get their hands on a santa rosa MBP so they can see how unusuable gutsy tribe 3 is -- out of the box, without the end-user installing many many patches -- compared to mac os x.  There's simply a ton of work left to do.

---

### Post by duffman25 on 2007-07-26
> **benanzo said:**
> So I was at Ubuntu Live this week and had an opportunity to talk to a couple of the Ubuntu kernel developers about running Ubuntu on Intel Macs.  A couple of the questions I asked were:

1) How close are we to booting with EFI?

The answer: Not close at all.  Apparently Apple hasn't fully implemented Intel's EFI specification especially regarding how to get video information so X can start up with a usable resolution.  So don't work too hard on that (like I did.)

2) Is it safe to get rid of the 200MB EFI partition at the front of the disk?

The answer: Yes, but only if you're not booting OS X.  It is not safe if you use OS X to install firmware updates.  Although OS X doesn't boot from the EFI partition, Apple does use it to install firmware updates.  Apparently when OS X downloads a firmware update it copies that package to the EFI partition, sets it as the boot partition then when you reboot to install it, it boots from that partition and runs the update.  When it is done it changes everything back to normal.  This is somewhat contradictory to my experience.  I remember running firmware updates even after I repartitioned the disk as pure MBR (no EFI part.) without any problem.  However, it is advisable to keep that partition around if you use OS X to update your firmware.

 I only boot Ubuntu on my machine, so I have no need for that partition.

Any workaround on the 30 seconds delay at boot? I also boot only linux.

---

### Post by cyberdork33 on 2007-07-26
> **duffman25 said:**
> Any workaround on the 30 seconds delay at boot? I also boot only linux.

What 30 second delay?

---

### Post by pveith on 2007-07-26
I thought the EFI Partition was for data exchange beween OSX and Windows. I planed to use it for data exchange between OSX & Ubuntu, but i started OSX only twice since i got my macbook. I think i should remove OSX, it is not worth the diskspace for me...

---

### Post by duffman25 on 2007-07-28
> **cyberdork33 said:**
> What 30 second delay?

If you install ubuntu only(single boot) there's a 30 second delay when efi finds grub in mbr. AFAIK this is because it first looks for GPT partitions and after failing it resolves to MBR.

---

### Post by Ptero-4 on 2007-07-28
> **duffman25 said:**
> If you install ubuntu only(single boot) there's a 30 second delay when efi finds grub in mbr. AFAIK this is because it first looks for GPT partitions and after failing it resolves to MBR.
Isn´t refit supposed to jump straight to mbr and boot if you select the ´linux´ icon (or if you set it to autoselect that icon and you set the timer to 0)?

---

### Post by benanzo on 2007-07-29
I have the delay as well (more like 15 secs for me.)  This is because I don't have OS X or refit installed.  Mine is a pure MBR disk with GRUB only.  Without access to Apple's EFI to change the timeout the only way to fix it (afaik) would be to install OSX or install refit on the /boot partition.  In order to install refit you need to use a utility called *bless* which tells the EFI that /boot is a bootable partition.  I am not aware of a Linux version of this utility, nor do I know if it is even Free software, though it is a BSD utility.

[Here's]("http://developer.apple.com/documentation/Darwin/Reference/ManPages/man8/bless.8.html") the *bless* man page on Apple's developer site.

[Here's]("http://felipe-alfaro.org/blog/2006/09/19/installing-refit-on-the-hidden-efi-system-partition/") a little howto for installing refit independently of OS X (on the /EFI system partition.)  Still requires OS X to be installed, at least initially.

---

### Post by luisbg on 2007-07-29
The good news is that there is interest in developing farther and better the linux in mac-intel machines.

Thanks to all kernel developers.

luisbg

---

