---
title: "Installing onto a RAID 0 Volume..?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Siyfion on 2008-01-09
I have an ASUS P5B-Deluxe with the onboard RAID controller, which I use to have 4 disks, split up into two seperate RAID 0 arrays. When I try to install Ubuntu using the Live CD it detects the drives as seperate SCSI drives, even though when I go into the device manager it quite clearly states that they are "(isw_raid_member)" and are listed under the "82801 SATA RAID Controller".

Any idea's as to how I would go about installing Ubuntu onto one of the two RAID 0 Volumes?

---

### Post by Siyfion on 2008-01-09
About to answer my own question.. but after a little more digging.. [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by dstew on 2008-01-09
I have heard that the Alternate Install CD will install on a RAID without any extra steps.

---

### Post by Siyfion on 2008-01-10
I didn't even realise there *was* an alternate install CD!?

---

### Post by dstew on 2008-01-10
Yes, it is a text-based installer. It doesn't have the LiveCD system on it. I think it has more room for hardware detection software. Often, if the LiveCD won't install on a system, the Alternate Install will. To get it, check the box below the "Start Download" button on the [Ubuntu Download page]("http://www.ubuntu.com/getubuntu/download").

---

