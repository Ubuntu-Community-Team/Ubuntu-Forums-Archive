---
title: "Urgent Help XP Failed !!!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Vish555 on 2007-04-29
Ok got ubuntu going but now i get the following error:

Windows could not start because the file is either missing corrupt:

<windows root>\system32\hal.dll

Now i checked and i have the file. Any ideas on what to do from here? Please reply quickly. Thx in advance.

---

### Post by scrooge_74 on 2007-04-29
Get that file from your windows CD or download it and then replace it

---

### Post by Billy McCann on 2007-04-29
You didn't aggressively resize the Windows partition, did you?  Like, taking the free space to less than 1 Gig?

---

### Post by Vish555 on 2007-04-29
nope and the file is already there so what's the point of replacing it?

---

### Post by sailor2001 on 2007-04-29
[http://www.dll-files.com/dllindex/dll-files.shtml?hal](http://www.dll-files.com/dllindex/dll-files.shtml?hal)   for missing dll files

---

### Post by Vish555 on 2007-04-29
but its not missing!!!. I have the file. I just can't boot.

---

### Post by aberry5555 on 2007-04-29
This isnt a missing file, this is the windows loader getting confused about where windows actually is, use the windows installation disk in repair mode and then rebuild the windows loader, off the top of my head I cant remember what the command is but if you type in "help" in the command prompt it will give you a list.

---

### Post by oilchangeguy on 2007-04-29
what if any changes have you made before this happened? changed the drive from master to slave, etc.?

---

### Post by aberry5555 on 2007-04-29
I think its probably because you added a partition before the windows disk (sometimes you can get this error even from adding a partition anywhere!)

---

### Post by Vish555 on 2007-04-29
well there is a partition existing before the windows partition but it serves no use. It is just empty. About 7gb in size. So i get the xp cd, stick it in and press r for recovery console. Then what? Thx for the help so far. :)

---

### Post by abcuser on 2007-04-29
Hi,
if I understand correctly master boot record or partition boot record got messed out. Insert Windows CD into CD drive, go to repair mode and execute command: mbrfix - this will fix master boot record. I also advice to [search the error by Google](http://www.nocrash.com/ncbbs/msgs/162.shtml) - you know "Google is my friend" :)

---

### Post by aberry5555 on 2007-04-29
I think its actually "fixboot". I know for a fact it's not "FIXMBR" (don't try it, if it goes wrong you'll lose all your data so leave it until you've backed everything up). Basically if you type in the command it will search for a windows installation, ask you which installation(s) to use. Once you've chosen it it will re-write the boot record. Careful though it will probably install on the first partition and will over-write your linux grub if it's currently sitting there.

---

### Post by pm5org on 2007-04-29
Yes this is possible due to partitioning table changing.So boot.ini I think like this
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

here partition no. is now may differ I have face this problem and changed file like this

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP C  Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP  E Professional" /fastdetect /NoExecute=OptIn

here 2 windows in hard disk 1 on c and 2 on e but you may look partitions are 1 and 4 

 try and get success:guitar:

---

### Post by Vish555 on 2007-04-29
i need the real command cos this is my only pc atm. Is it fixmbr or fixboot? Sorry to be a pain. It's just i'm really annoyed. :mad:  and confused :confused:

---

### Post by abcuser on 2007-04-29
> **aberry5555 said:**
> I think its actually "fixboot". I know for a fact it's not "FIXMBR" (don't try it, if it goes wrong you'll lose all your data so leave it until you've backed everything up). Basically if you type in the command it will search for a windows installation, ask you which installation(s) to use. Once you've chosen it it will re-write the boot record. Careful though it will probably install on the first partition and will over-write your linux grub if it's currently sitting there.
It depends what is expected result. FIXMBR will overwrite master boot record - so Windows will start but Ubuntu will not (if I understand correctly Windows was first installed on computer and Ubuntu second). I don't know how Ubuntu makes a dual-boot (not done yet), but several years ago I have done dual boot by Windows and Suse Linux. Suse had an option to boot from Windows boot menu. Who takes control of dual boot if Ubuntu is installed? Ubuntu loader or Windows loader? If Windows then this is save to execute if Ubuntu loader is the first one, then fixmbr will just overwrite MBR and put Windows loader for the main control.

First of all try using fixboot command to fix Windows loader - if that doesn't go then try using fixmbr (this will put Windows of charge of booting process).

---

### Post by oilchangeguy on 2007-04-29
read this:
[http://support.microsoft.com/kb/330184/en-us](http://support.microsoft.com/kb/330184/en-us)

---

### Post by Vish555 on 2007-04-29
WOOT WOOT!!! I just fixed it.!!!!
Thx so much for all your help . All of u. I could hug all of you right now and i prob would if i knew where u lived. :P Thx again so much. I finally have a dual booting system. :D:D:D:D:D

Posted this twice now but thank you so much now.

---

### Post by otykier on 2007-05-01
> **Vish555 said:**
> WOOT WOOT!!! I just fixed it.!!!!
Thx so much for all your help . All of u. I could hug all of you right now and i prob would if i knew where u lived. :P Thx again so much. I finally have a dual booting system. :D:D:D:D:D

Posted this twice now but thank you so much now.

Sorry for bumping this relatively old thread, but could you please explain what you did to make it work? I'm experiencing the exact same problem at the moment.

Regards

Daniel

---

### Post by oilchangeguy on 2007-05-01
> **otykier said:**
> Sorry for bumping this relatively old thread, but could you please explain what you did to make it work? I'm experiencing the exact same problem at the moment.

Regards

Daniel
read post #16.

---

### Post by otykier on 2007-05-01
> **oilchangeguy said:**
> read post #16.

What do you know! It worked like a charm!

Thanks a lot for the fast and precise response. Ubuntuforums bookmarked for further newbie questions :D

---

