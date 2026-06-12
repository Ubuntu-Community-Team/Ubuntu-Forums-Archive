---
title: "Dapper not seeing bios raid5 array"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by maheanuu on 2006-12-23
After getting grub error on the alternative AMD64 Dapper disc installation, I have loaded the Live Desktop and am trying to get the raid array to be recognized by Dapper.  I am only (at present) able to set partitions on one of the drives as it isn't seeing the bios raid5 array that was set up..

I am using a MSI K9N SLI Platinum Motherboard with 5 Maxtor 320 GB hard drives and a PNY GEForce 7900 GS PCIe Graphics accellorator.  

I have been through the install 4 times, and up to now, I have not been able to boot from hard disk, only run from the live cd...  I have been trying to get this system up for the past 4 days, and seem to only return to the same situation...

I am a total newbie to linux, but have installed Raid5 on many windoze boxes...  and never had the probs I seem to be having here...

Not grumbling, just trying to find out what I need to learn and where to go for the information or installation details that I can understand...

If any of you have done a raid5 install, I would appreciat your help....

Ken Jackson
CPO USN Ret.

---

### Post by brolin on 2006-12-30
I had the same experience with an ASUS K8N motherboard, which also has an nVidia RAID controller.  The problem is that this RAID controller is a "fake RAID" controller:  it is not a full hardware RAID controller;  it is designed for use with Windows and requires a Windows driver.

I was able to boot from the hard disk only after disabling the nVidia RAID controller in the BIOS.  If you need RAID, you can get a card with a true, hardware RAID controller, or use Linux software RAID.

BTW: I found this post because I have the non-SLI version of your motherboard.  I have not tested the RAID controller on my K9N Platinum, since I do not need RAID for this application.

---

### Post by maheanuu on 2006-12-31
After beating my brains out on my keyboard shelf, I have finally discovered (yesterday) what Brolin so kindly stated in his post.  I have managed to find the ultimate software raid config/manager by digging constantly and repeatedly in nooks and crannies everywhere....

I am leaning towards mdadm and have managed to bookmark a lot of howtos  and am beginning to see a light at the end of the tunnel that is not an oncoming train...

Thanks to Brolin for your comeback and help...  I appreciate it more than I can express in here....

I will make a html list of everything I have bookmarked and post it in here when I have it complete (sometime today).

---

