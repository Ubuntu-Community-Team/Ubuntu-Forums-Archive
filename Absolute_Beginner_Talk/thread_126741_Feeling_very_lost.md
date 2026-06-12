---
title: "Feeling very lost"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by IainT on 2006-02-07
After finding my old(ish) laptop the other day I decided to have a play with it, maybe try and breathe some new life into it. Been toying with the idea of linux for ages and ubuntu was recommended to me.

Specs are not quite up to what is recommended. 433mhz Celeron, 96mb RAM, 4.2gb hdd. I downloaded the .iso file, burned it as an .iso file and the computer happily recognised it and started the install.

First time it gave some options for partitioning, and I broke my golden rule for things I don't really understand. I just went ahead without doing any research and selected the second option. Install carried on until 'installing the base system' got to around 60 something percent and then it told me that it couldn't install 'kernel i386'. Couldn't carry on, so I restarted the whole process.

Second time I chose another option for partitioning, this time it ran right through the 'installing base system', and ejected the cd, let me restart and then start to install 'further packages'. It got as far as about 60% of the way through and froze whilst trying to configure 'apmd'. It was now 3am. I went to bed.

Got up this morning and tried to set it off again. This time the computer turned on, and a little red screen popped up and said 'partition does not exist, write to disc disabled'. I figure that I can't proceed from here without help. Would be very grateful. Thanks in advance.

---

### Post by Kapre on 2006-02-07
[QUOTE=IainT]After finding my old(ish) laptop the other day I decided to have a play with it, maybe try and breathe some new life into it. Been toying with the idea of linux for ages and ubuntu was recommended to me.

Specs are not quite up to what is recommended. 433mhz Celeron, 96mb RAM, 4.2gb hdd. I downloaded the .iso file, burned it as an .iso file and the computer happily recognised it and started the install.

First time it gave some options for partitioning, and I broke my golden rule for things I don't really understand. I just went ahead without doing any research and selected the second option. Install carried on until 'installing the base system' got to around 60 something percent and then it told me that it couldn't install 'kernel i386'. Couldn't carry on, so I restarted the whole process.

Second time I chose another option for partitioning, this time it ran right through the 'installing base system', and ejected the cd, let me restart and then start to install 'further packages'. It got as far as about 60% of the way through and froze whilst trying to configure 'apmd'. It was now 3am. I went to bed.

Got up this morning and tried to set it off again. This time the computer turned on, and a little red screen popped up and said 'partition does not exist, write to disc disabled'. I figure that I can't proceed from here without help. Would be very grateful. Thanks in advance.[/QUOTE]

Iain - looking at the symptoms (if I may call it) you've stated above, it seems like you've made a bad disc. Maybe you should check the MD5Sum and if it is ok, try to burn it on a slower speed. 

Try those and post what happens. Also, with your specs, I wuold suggest you install Xubuntu (XFCE).

K

---

### Post by qwazert on 2006-02-07
The old Vectra that I am using is an old(ish) 450Mhz with a 4.2 gB HD as well. I have slightly more RAM (128Mb) but otherwise identical to your setup and my INSTALL went off without a hitch (until my documented problems with resolution and my Printer).

During INSTALL, I tend to accept the suggestions/defaults as they are offered, and since this machine was "empty" (a completely CLEAN install) this may have contributed to the success of the first installation.

I agree with **Kapre**, try to burn your **.iso** images at a slower speed.

---

### Post by IainT on 2006-02-07
Thanks guys. I've learned a few things since my post. The 'save to disk' feature appears to be a windows thing, and I've managed to disable that message in the bios. So it wasn't that critical, I was panicking about not being able to write to the hdd at all.

The maximum burn speed on the cd writer I used is 4x. Too fast?

Tried again earlier, it gave me the same error as it did the first time. I've now figured out how to 'execute a shell' and so can find the log file. Got to go out now, so I'll post what I find there later.

Learning stuff the hard way is still learning I suppose. I've briefly looked at Xubuntu, intimidated by the need to be online.

---

### Post by aujames95 on 2006-02-07
I had the same issues, came down to the speed I burned the CD. I started at 40x, ended up at 24x. Not to Hi-jack your thread, but why does the speed at which the speed at which the CD seem to matter so much?

JD

---

### Post by kaamos on 2006-02-07
I think even 24x is quite a high speed for an install cd.. 4x should not cause any problems though. Just make shure the iso you have downloaded is ok (md5sum) and check the cd integrity if you get errors. For the burning: more speed - more errors. And since the cd contains only installation files, errors do matter..

---

### Post by skirkpatrick on 2006-02-07
I don't know if the disc starts fluttering or not but most places recommend that you don't burn a CD higher than 16X and DVD's at 4X.

---

### Post by IainT on 2006-02-07
Well, I finally figured out how to check the integrity of the cd I had created. Was a little surprised, like I said I had burned it at 4x, but the file that initially gave me the problem 'linux i386' was invalid.

I'll try burning a new cd tomorrow. Thanks for the advice. I'm sure I'll be back for more.

btw Xubuntu looks like the route for my system, just a little more complicated to set up in the absence of an install cd.

---

### Post by skirkpatrick on 2006-02-08
The other thing you have to remember is that CD-ROM, CD-RW, and DVD drives are mostly plastic and the heat generated by the unit eventually warps the plastic of the drive causing it to be out of calibration.  Depending on how often you use it, it may not live more than 2-3 years.

---

### Post by IainT on 2006-02-08
The cdrom on this thing is not 100% healthy, but as I plan to rarely use it after installing then I've just got to get through this bit...

Created a new cd at 1x burn speed. Checked it and it is valid. Install is due later today.

---

