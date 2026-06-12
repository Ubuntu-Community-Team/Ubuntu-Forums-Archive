---
title: "Probs with Feisty64, Grub, and SATA"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by arachnegl on 2007-04-12
Hi everyone,

I recently bought a new comp: AMD64 with a SATA 3gb hard drive.

Ubuntu 6.10 wouldn't detect half the features on the motherboard so I installed the Feisty dev version. Eventually I got everything working. It has been a sweet honeymoon for one month.

Two days ago, at boot up the usual "this drive has booted 30 times, force check" (or something similar) occured. For the first time ever, this started reporting a series of errors. Can't recall what they were, but something about sectors being dead. (Note that this is a brand new samsung hard drive.) 

Finally Ubuntu booted up. I installed some new updates and shock horror: Linux crashed!!! 

(I do recall installing an update to Fdisk (?) the day before not sure if relevant)

Now my system occasionally boots and gives me various results. Usually I can work but then the system stalls for a minute or so then resumes. Command line doesn't let me log in...

Often Grub gives these messages:
Error 18 Selected cylinder exceeds max supported by BIOS [Clearly untrue...]
Error 16 Inconsistent filesystem structure

When the system stalls and when I do manage to log in at the command line, or when I check the logs this seems to be the issue:
[xxxx.xxxxxx] ata1 : port failed to respond (30 secs, Status 0xc0)
[xxxx.xxxxxx] ata1.00 : revalidation failed (erao=-5)
[xxxxxxxxxxx] ata1.00 exception Emask 0x0 Sact 0x0 SErr 0x400000 action 0x0
[xxxxxxxxxxx] (BMDMA stat 0x24)
[xxxxxxxxxxx] cmd 35/00:00:77:ed:b0/00:04:04:00:00/e0
[xxxxxxxxxxx] tag 0cdb 0x0 data 524288 out

The x's vary and the error message format is usually similar to the above.

Sometimes the desktop boots up fine and works for an hour stalling only a few times. At other times it stalls every 5 mins. Often it never gets past the Grub stage. At least it constantly surprises me...

I realise Feisty is experimental. As a newbie I might have chewed off more than I could handle. But it was the only blend that worked. 

I don't want to reinstall as I have substantial data on the hard drive. If this is the only practical solution, is there anyway of installing without wiping out all my data? A costly option would be to buy a new hard drive and use it to recover files off the old... Would rather sort this out though.

Thanks in advance for your help.

---

### Post by mendingo84 on 2007-04-12
use gparted to resize your partition. make it slower and with the new free space create a new partiotion. after having that done, move your important files to the new partition. you can reinstall then if you want.
my advice for you, for future reinstallings, would be to make a separate partition for your /home directory which you won't format on a new install. that way, you will be able to perform a new install without any problems and even keep your settings.

---

### Post by Boztech on 2007-04-12
If you are getting reports of bad sectors, you could have a failing hard drive.  The symptoms you listed are also indicative of a possible failing drive.

If you truly have substantial data on the hard drive, you need to back it up to cd/dvd or external drive immediately whether or not the hard drive is failing.  Then you need to test the drive to see if it is failing by downloading and burning a copy of the Samsung diagnostic utility - [here.]("http://www.samsung.com/Products/HardDiskDrive/utilities/hutil.htm")

Only once you can be certain you don't have bad hardware, then you can continue to experiment with different versions of Ubuntu to fit your needs.

---

### Post by arachnegl on 2007-04-12
Thank you both for your advice.

I am currently doing a hard drive check with the utility Boztech suggested. Its taking forever and so I don't think I will know if it is a hard disk failure rather than an Ubuntu bug before tomorrow.

Will keep you posted.

Thanks

---

### Post by arachnegl on 2007-04-12
Ok the hard drive check came up with the following at 87.074% of completion: 

C:95542 H:4 S:1 Error: Busy not clear

I think that this concludes that the prob is my hard drive and not Linux (my apologies for doubting you!)

I need to retrieve my data before taking the HD back.

I think that I will buy a new HD and attempt to copy the files onto it from my current failed one. Does anyone have any suggestions about the best way to do this? Will it fail? Make it worst...? Is there a better solution?

Could I 'cordon off' (ie isolate) the failed part of my HD to make my system more stable? Is there a utility for this?

---

