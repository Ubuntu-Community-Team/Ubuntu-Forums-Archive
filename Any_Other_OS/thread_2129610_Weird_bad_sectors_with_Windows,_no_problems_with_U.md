---
title: "Weird: bad sectors with Windows, no problems with Ubuntu"
date: 2013-03-26
forum: Any Other OS
---

### Post by Jon Monreal on 2013-03-26
Although I primarily use Ubuntu on my systems, I've had Windows installed on one for Flight Simulator X.

The weird thing is that recently the Windows installations have had problems with bad sectors, eventually to the point where chkdsk can't repair the problem and the OS has to be restored. This occurred first under Vista and then Windows 7, under different installations. I wasn't terribly concerned about data loss due to a failing hard drive because the system was backed up, so I continued to use it.

Recently I decided to install Ubuntu (with ext4 file system). I've been using it for a few weeks now and have checked the disk for bad sectors using seatools (by now Windows would have had at least some problems) and haven't had a single problem with bad sectors.

Does anybody know if this could simply be due to the ext4 file system? I'm trying to figure out why Windows would have this problem while Linux doesn't. EDIT: and the problem didn't occur in Windows for quite some time.

Thanks,
Jon

---

### Post by matt_symes on 2013-03-26
Hi

> Does anybody know if this could simply be due to the ext4 file system?  I'm trying to figure out why Windows would have this problem while Linux  doesn't.

The filing system itself should not make any difference to any bad sectors but i am wondering if you have had some bad sectors reallocated by the drives firmware due to writing to the sector while formatting to ext4 or some such.

I would perform a SMART test on the drive and see what that returns. Most newish drives are SMART capable.

From the terminal

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

This assumes your drive is sda. 

It will take a while to finish. When it has finished

```
sudo smartctl -a /dev/sda
```

Post the results back here.

Kind regards

---

### Post by leclerc65 on 2013-03-26
I have friends that were reluctant to try Ubuntu.
I told them them to try Ubuntu (or derivatives) out on BSOD PC's, and everything worked out OK.
Made a few conversions that way.:P

---

### Post by Jon Monreal on 2013-03-26
I've started a SMART test now to see if I can get any results.

> **matt_symes said:**
> The filing system itself should not make any difference to any bad sectors but i am wondering if you have had some bad sectors reallocated by the drives firmware due to writing to the sector while formatting to ext4 or some such.

I would think that if this were the case, the same would be true of the drive being reformatted to NTFS before one of the multiple times it was reformatted before being restored, no?

EDIT: here are the results: [http://pastebin.com/XK09U1x9](http://pastebin.com/XK09U1x9)

---

### Post by matt_symes on 2013-03-26
Hi

> I would think that if this were the case, the same would be true of the  drive being reformatted to NTFS before one of the multiple times it was  reformatted before being restored, no?

That may well depend on whether it does a quick or a full NTFS format at the start.

I'll take a look at you SMART results and post back. Hopefully that may give some concrete answers as at the moment it's all speculation.

Kind regards

---

### Post by Jon Monreal on 2013-03-26
> **matt_symes said:**
> That may well depend on whether it does a quick or a full NTFS format at the start.

I'll take a look at you SMART results and post back. Hopefully that may give some concrete answers as at the moment it's all speculation.

Thanks.

Just so you know, I always do a full NTFS format prior to restoring a backup.

---

### Post by matt_symes on 2013-03-26
Hi

Looking at the SMART results, your drive is having read errors. 

Infact the drive has...

> **Error 23683** occurred at disk power-on lifetime: 14395 hours (599 days + 19 hours)



SMART can be wrong, however as you were having problems under windows it would suggest it's not in this case.

Quite why your not seeing the same errors in Linux, i'm not sure. I can only assume the driver is more fault tolerant.

I would suggest this drive is failing though.

To be honest, it's too late here in the UK for me to really study the SMART report. I may look again the in the morning.

Kind regards

---

### Post by Jon Monreal on 2013-03-26
I'll keep an eye on it and see if there are any additional errors. I'm not sure if the 14395 POH mark would fall under when Windows was still installed. I find it interesting that the "LBA_of_first_error" value has increased so much, at any rate.

Thanks for all your help.

---

### Post by prodigy_ on 2013-03-26
```
  4 Start_Stop_Count        0x0032   092   092   020    Old_age   Always       -       8704
  5 Reallocated_Sector_Ct   0x0033   080   080   036    Pre-fail  Always       -       415
  7 Seek_Error_Rate         0x000f   060   057   030    Pre-fail  Always       -       1237186230140
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       65535
188 Command_Timeout         0x0032   100   093   000    Old_age   Always       -       154621182149
190 Airflow_Temperature_Cel 0x0022   052   038   045    Old_age   Always   In_the_past 48 (0 37 49 42)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       492
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       492
254 Free_Fall_Sensor        0x0032   001   001   000    Old_age   Always       -       2060
```
Wow, with SMART readings like these, your HDD belongs in a trash bin. And - just a friendly advice - don't buy Seagate next time.

---

### Post by Jon Monreal on 2013-03-27
[QUOTE=prodigy_][COLOR=#000000]Wow, with SMART readings like these, your HDD belongs in a trash bin.[/COLOR][/QUOTE]

I'm not using it with the expectation it will last at this point, certainly. I just find it interesting that Linux seems to be able to handle the problems with no apparent problems while Windows breaks down like crazy.

[QUOTE=prodigy_][COLOR=#000000]And - just a friendly advice - don't buy Seagate next time.[/COLOR][/QUOTE]

Unfortunately, it's what came with the system. It'll be replaced with an SSD at any rate.

---

### Post by prodigy_ on 2013-03-27
> **Jon Monreal said:**
> Linux seems to be able to handle the problems with no apparent problems while Windows breaks down like crazy.
Linux installation normally takes less space than Windows. Maybe it fits into an area that isn't failing yet.

---

### Post by Jon Monreal on 2013-03-27
[QUOTE=prodigy_][COLOR=#000000]Linux installation normally takes less space than Windows. Maybe it fits into an area that isn't failing yet[/COLOR][/QUOTE]

There's a total of about 39 GiB on the disk, well into the area that failed before.

---

### Post by mips on 2013-03-27
That drive is on it's way out.


> **prodigy_ said:**
> And - just a friendly advice - don't buy Seagate next time.

No brand is immune to failure and it's pretty much luck of the draw when you buy any brand of hard drive.

---

### Post by prodigy_ on 2013-03-27
> **mips said:**
> No brand is immune to failure and it's pretty much luck of the draw when you buy any brand of hard drive.
It's not luck when they slap 1 year warranty on their products. Seagate was great once but they went rapidly downhill ca. 2007.

Right now WD Black is probably the best you can (still) get at consumer grade. Hitachi is OK... most of the time. I've heard a lot of good things about Samsung drives but I've never had one.

---

### Post by mips on 2013-03-27
> **prodigy_ said:**
> It's not luck when they slap 1 year warranty on their products. Seagate was great once but they went rapidly downhill ca. 2007.

Right now WD Black is probably the best you can (still) get at consumer grade. Hitachi is OK... most of the time. I've heard a lot of good things about Samsung drives but I've never had one.

It's luck of the draw. I've had most failures on Samsung, followed by WD & then Seagate. It could have gone in the reverse as well. There's no more Hitachi, they were purchased by WD. There's no more Samsung, they were purchased by Seagate. All that's left is Seagate, Toshiba & WD. If you know people that do data recovery (the type that deals with hardware failures, logic boards, head stack assemblies, spindle motors etc) they will also tell you it's pot luck. Every now and again a manufacturer will have a bad run with certain models where they screw up but it happens to all of them.

---

### Post by Jon Monreal on 2013-03-30
Just to give an update, now at 14,471 POH there still haven't been any additional errors or problems. As I said before, I believe that the last error was from when Windows was still installed. I'm just hoping this isn't a problem other than with the hard drive itself that might cause more problems when I install the SSD.

---

### Post by mips on 2013-03-30
Keep an eye on the S.M.A.R.T. info. Usually with bad sectors they increase. There's a limited amount of reallocation sectors on a HDD. Once you reach the limit the HDD is fooked.

---

