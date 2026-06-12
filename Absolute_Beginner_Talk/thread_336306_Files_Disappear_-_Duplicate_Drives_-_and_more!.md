---
title: "Files Disappear - Duplicate Drives - and more!"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by GreenMedallion on 2007-01-11
Ok, not really any more than that. After working on my laptop all day yesterday, I turn it on this morning to find that 3 files I had been working on were gone - no trace other than their presence in the "Recent Documents" tab of Open Office. Two files were OO, the third was a PDF. 

In addition a duplicate drive is appearing. I have a Dell laptop, Ubuntu dual boot with Windows. In addition there are partitions for - Dell's Media Direct, Dell Recovery, and a large shared space where I keep all my docs (so i can go back and forth between Windows and Ubuntu if need be). Well the "Media Direct" drive is appearing twice now: Media Direct, and Media Direct 2.

I should note when I first turned on my laptop this morning it booted up to a window that said   'Dell Media Direct' - I have never seen this before. It then froze and brought up an error screen about a failure with the Plug and Play and that I should reboot, if it happens again do such and such, but it didnt happen again. Just rebooted, all was normal until I discovered missing files, and the dupe drive.

Obviously, the files are gone. Any ideas on what may have happened and how I can make sure it doesnt again?

Two things I could note I did between yesterday and today: I left my laptop on all night, it went to sleep, but I usually do not leave it on all night. Also, when I turned it off this morning to leave I unplugged my printer (not sure if that would affect Plug and Play to cause an error).

Thanks

---

### Post by GreenMedallion on 2007-01-11
Let me add to my post-

When I open QTParted or Gnome Partition Editor they show NO partitions on my harddrive. In the past, all partitions were present.

---

### Post by mikeize on 2007-06-07
I have duplicates of ALL my drives, it seems.  they have the names I gave them, plus names like "hdb1 and sda1, and cdrom0, etc."  and the shortcuts are weird too...  it seems like they point to the one that they AREN'T named after...  also, the folders have different permissions, despite containing the same files.  wtf!

-mike

---

### Post by forestpixie on 2007-06-07
Seems common at the moment - there are bugs reported of similar in launchpad

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118714](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118714)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/109418](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/109418)

I had a phantom cd drive - I commented it out in fstab and it has gone - for the moment.

---

### Post by mikeize on 2007-06-07
Thanks for the info,

Good to know it's being monitored.

-mike

---

