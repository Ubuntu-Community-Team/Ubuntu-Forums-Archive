---
title: "Using Parted to extend a partition to a different physical drive"
date: 2012-06-30
forum: Any Other OS
---

### Post by ruhtraeel on 2012-06-30
Hi,
I'm actually on Windows 7 right now but I'm running Parted through System Rescue CD.

I want to extend my main partition on my C: drive (boot drive), which is a 250GB (Hitachi) physical drive, to another 160GB (Samsung) physical drive which is unallocated to hopefully give me around 410GB total, all within the C drive.

How would I do this with Parted using commands? 

I would be using GParted, but the wizard command to set up a VGA driver doesn't work with either option.

---

### Post by Elfy on 2012-06-30
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by ratcheer on 2012-06-30
What you are asking for is not possible, as far as I know. Maybe some kind of logical volume manager would do it, but I have no idea how Windows would react to such a configuration. So, you could look into btrfs or LVM or other similar facilities, but I don't have much hope for them working with Windows.

Maybe Windows has its own LVM facilities, but again, I have no idea.

Tim

---

### Post by southerngeek on 2012-06-30
Yeah, I don't think that is really feasible....can i ask what your reasoning is behind wanting to do this? If you're just after storage there's not a real benefit in combining the two drives.

---

### Post by oldfred on 2012-06-30
I normally am suggesting the opposite. Separate system from data. Whether Windows or Linux.

Or keep all your data on d: and leave c: as system. With Windows you still often need a large system partition as it install large applications by default to c:.

---

### Post by steeldriver on 2012-06-30
Windows 7 Disk Management will natively allow you to create a 'spanned volume' across multiple disks - I have never used it for the reasons stated above 

Control Panel -> System and Security -> Administrative Tools -> Computer Management -> Disk Management

R.Click the 1st partition you want to use and select 'New Spanned Volume' then add the other(s) from the popup selection window

---

### Post by ruhtraeel on 2012-06-30
> **steeldriver said:**
> Windows 7 Disk Management will natively allow you to create a 'spanned volume' across multiple disks - I have never used it for the reasons stated above 

Control Panel -> System and Security -> Administrative Tools -> Computer Management -> Disk Management

R.Click the 1st partition you want to use and select 'New Spanned Volume' then add the other(s) from the popup selection window

I wanted to do this, but apparently you can't do it with the windows boot drive.

I think what this is called is software jbod and I think it's possible cause Windows just extends to the other drive once full instead of striping the data like RAID does. 

I want to do this because I don't want to install things on two separate drives, and I think 250gb isn't enough for my games.

Anyone else have any ideas?

---

