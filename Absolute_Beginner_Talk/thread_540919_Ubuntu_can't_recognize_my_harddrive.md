---
title: "Ubuntu can't recognize my harddrive"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by OskarB on 2007-09-02
When I boot Ubuntu from the CD first I get the following error:

Loading Hardwaredrivers...
[110.736000] intel_rng: FWH not detected

but I can use the testversion on the cd...

Then I start the installguide, everything works fine until I´m about to partition the harddrive... I only get the Manual alternative and when I chose it and press next I only get a blank area with a little text explaining that I have to hava a rootpartition and yada yada but there are no buttons or so to push so I can't do anything. And when I press next it says that I have to partition the harddrive first...

I think this is becouse that ubuntu cant recognize my harddrive, maybe it's not supported or something... (I have allready a windows partiton and it works so it's nothing wrong with the harddrive and I've tested the boot-cd for errors and it's ok..)

Anyone has a sulotion to my problem?

Thanks!

//Oskar

---

### Post by Skrynesaver on 2007-09-02
When you are booted on the liveCD, Do you have an icon for your hard drive on the desktop?

---

### Post by OskarB on 2007-09-02
No, there is only one Example icon and a install icon...

---

### Post by armandh on 2007-09-02
asuming that the hard drive was working in this computer it may have been set up with an odd unreconizable partition / file system
you may need a partition utility to remove the old one.

---

### Post by OskarB on 2007-09-02
Right now I have one NTFS partition with Win XP on it... it's been there from the very start... I have a Toshiba portégé laptop if that helps...

Do you mean that I have to format the harddrive?

I want to have dualboot...

//Oskar

---

### Post by MenZa on 2007-09-02
Could you please paste the output of *sudo fdisk -l*? Thanks!

---

### Post by OskarB on 2007-09-02
I ran sudo fdisk -R and got the following answer:

fdisk: invalid option -- R

and then a little explanation of fdisk...

Thanks for all help!

---

### Post by Duck2006 on 2007-09-02
> **OskarB said:**
> I ran sudo fdisk -R and got the following answer:

fdisk: invalid option -- R

and then a little explanation of fdisk...

Thanks for all help!

sudo fdisk -l

---

### Post by OskarB on 2007-09-02
Ok... finally... I ran sudo fdisk -l and got no answer only a new line...

---

### Post by OskarB on 2007-09-02
Anyone who knows what that means? And what I should do?

---

### Post by OskarB on 2007-09-02
I tried to partition with a GParted Live CD and there I get an error: filesystem check failed,it says that I should run chkdsk /f and I did , it allso says that I should reboot twice, but my windows hangs every second time i boot it so I had to cut the power the second time.. might that be the problem? because when I try again its the same error...

Thanks for your help!

//Oskar

---

### Post by vanadium on 2007-09-02
fdisk -l does list all drives and partitions on them that your system recognises. If the output remains empty, then it would seem that the Ubuntu Live CD does not recognise any drive in your system. This is weird in my opinion and could only be caused by very non standard equipment.

---

### Post by OskarB on 2007-09-02
I have a Toshiba PORTÉGÉ laptop with a TOSHIBA RAID LD0 SCSI Disc Device harddrive.. it should work shouldnt it?

any solutions?

---

### Post by OskarB on 2007-09-03
throug the night I ran windows "online fix me service" and now my windows goes a little bit faster even though it still hangs every second tim I boot it... Do you think it should help if I just did a recovery on windows so it has the original settings like when I bought it? or if I just format the entire drive? oris it that ubunto doesnt support my harddrive? I wrote in the previous post what harddrive I got...

Thanks for all the help!

---

### Post by OskarB on 2007-09-03
I just ran the recovery disc.. now everything is gone... but still.. it doesnt work... starting to get desperate.... please help me!!

Thanks  a lot!

//Oskar

---

### Post by OskarB on 2007-09-03
Noticed one more error text that appears just after I´ve pressed Start or install, it only appears under a short perion of time but this is what I get: 

[(numbers)] failed to allocate mem resources No (numbers) for (numvers)..

anyone knows what that means?

---

