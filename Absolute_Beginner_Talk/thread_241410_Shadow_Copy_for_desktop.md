---
title: "Shadow Copy for desktop?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by asmith3006 on 2006-08-22
Hi. I know Shadow Copy is the MS name for it, but is there an equivalent that can be used locally on Ubuntu? So if I save a file on my local hard drive it will archive the old one?

Thanks

Andrew.

---

### Post by wpshooter on 2006-08-22
> **asmith3006 said:**
> Hi. I know Shadow Copy is the MS name for it, but is there an equivalent that can be used locally on Ubuntu? So if I save a file on my local hard drive it will archive the old one?

Thanks

Andrew.

Are you referring to the backup file feature that is found in the M/S word program ?

---

### Post by asmith3006 on 2006-08-22
No, I'm referring to the Windows 2003 server feature for shared folders.
It takes a snapshot of files every X hours so you can go to a previous version should you mess up a new one.

It's the feature that Apple calls "Time Machine" and claims is wonderfully brand new :roll:

---

### Post by wpshooter on 2006-08-22
You are talking about a system restore point feature or something like goback.

To my knowledge Ubuntu does not have this unless it may be incorporated in the recover mode feature during bootup.

Maybe someone else can tell you if there is a system restore feature that can be installed from Synaptic.

---

### Post by asmith3006 on 2006-08-22
Not quite. System Restore takes snapshots of the system state, such as drivers and installed programs and ignore the user documents.

Shadow Volume Copy monitors the documents you make (office, PDF etc). This is the system I'm after. [http://www.apple.com/macosx/leopard/timemachine.html](http://www.apple.com/macosx/leopard/timemachine.html) is the Apple implementation of it.

I was assuming that because Apple are introducing it that they have simply put a nice (questionable) GUI on a feature that Linux (or FreeBSD) has anyway seeing as that's what they seem to do with everything else.

---

### Post by orb9220 on 2006-08-22
Well you could look into rsync and tar commands which you could setup as  cron job. 

You would have a script that would run every so ... and have it do incremental which would only backup files that changed.

Sorry but I am new to linux so you would need others to help you in that area.

---

### Post by Marsolin on 2006-08-22
Any program that uses [rdiff-backup]("http://linuxappfinder.com/package/rdiff-backup") can keep both a current backup and historical backups. I'm not sure how close they match what you are looking for, but I'd start there first.

Some front-ends are [pyBackPack]("http://linuxappfinder.com/package/pybackpack") and [Keep]("http://linuxappfinder.com/package/keep"), which is included in Kubuntu.

[KDar]("http://linuxappfinder.com/package/kdar") and [rsnapshot]("http://linuxappfinder.com/package/rsnapshot") are other options that might work for you.

---

### Post by asmith3006 on 2006-08-23
Thanks. I will have a look at them :)

---

### Post by cprofitt on 2007-07-02
For note: Volume Shadow Copy does not make backups in the way we traditionally think of. It was first implemented on Server 2003 shares, but is now included as part of the Vista OS.

Here is a link: [http://msdn2.microsoft.com/en-us/library/aa384649.aspx](http://msdn2.microsoft.com/en-us/library/aa384649.aspx)

The beauty of the feature is that an end user simple has to right click on a file or folder and say "restore previous version" and they are then presented with several date/time combos to restore. They can restore or "open" the files (used for restoring with a different name or to a different folder). From what I have seen it is a very efficient implementation as well.

Losing this functionality could be an issue for folks looking to migrate to Linux.

---

### Post by asmith3006 on 2007-08-05
Especially seeing as MacOS will soon have Time Machine too. 

Is there no equivalent for Linux then? This seems to be a huge oversight as both windows and now macos have it.

---

### Post by asmith3006 on 2007-08-07
Ok, I feel stupid
[http://ubuntuforums.org/showthread.php?t=474973](http://ubuntuforums.org/showthread.php?t=474973)

Ubuntu seems to be developing this exact thing an call it TimeVault.

I love Ubuntu!!!

---

