---
title: "I just want to start anew!"
date: 2011-12-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by richardsuave on 2011-12-28
How does one completely and totally remove everything from one's hard drive?
. I like to think that I am not totally stupid, Yet this evening, as I tried to reinstall Windows on My Asus K52F, I inadvertently lost My boot to the Linux partition that I myself set up. At this point, I don't care about any files I will lose, I would just like to learn from My mistakes and start fresh!  Quite simply, ... I would like, New linux. New windows.  I thank You in advance!! 

<email removed>

---

### Post by 2F4U on 2011-12-28
I would suggest that you start by installing Windows first. This will install the Windows boot loader into the MBR. You clould already create additional partitions during this setup, but this is not necessary. After Windows is setup you can install Ubuntu. Now it depends on your preferences whether you want to use grub as bootloader or do something different.

---

### Post by MARP1961 on 2011-12-29
I agree. Get your Windows install disk, boot from it and let it format your whole hard drive to NTFS. Let it install. Once Windows is installed, activated, verified, updated, protected by antivirus and whatever else it wants you to do, shrink the Windows partition enough to put Ubuntu on later. I download a free partition editor for this.

When I install Ubuntu from disk or USB I always choose the manual partitioning option ('Do Something Else'). The Ubuntu system partition (/) seems to run fine with no more than 12GB; but I always also set up a separate partition for all my data, music and other files and settings (/Home). This home partition should be as large as you can afford. Also set a small 2GB SWAP partition.

If you set up a dual boot like this, then Grub will load Ubuntu or Windows. If you ever need to reinstall Ubuntu, then you can easily leave Windows and your Ubuntu Home Partition (/Home) untouched by instructing the partitioner** not to format** those.

Remember if you ever remove Ubuntu then Windows will fail to boot. To get around this you have to restore Windows MBR using a Windows disk or just reinstall Ubuntu. Just be careful you never lose your Windows by installing Ubuntu on top of it!

---

