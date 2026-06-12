---
title: "Please help.... New to Linux and lost a drive!"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by Lord Kel on 2005-09-09
Hi There,

I have recently (2days ago) installed Ubuntu 5.04 on an older machine that I have. Now this machine was running WinXp and had one drive (30gig) partitioned into two C: was 5 gig and D: was 25gig.

I installed Ubuntu to the C: drive (completely removing Windows) and all has appeared to go o.k. The problem/issue I now have is "How do I get to the other drive as it does not show up in the file manager?" I would like to keep the data that is on the D: drive. Is there a way of accessing it easily??

Thank you in advance for your assistance

---

### Post by XDevHald on 2005-09-09
[QUOTE=Lord Kel]Hi There,

I have recently (2days ago) installed Ubuntu 5.04 on an older machine that I have. Now this machine was running WinXp and had one drive (30gig) partitioned into two C: was 5 gig and D: was 25gig.

I installed Ubuntu to the C: drive (completely removing Windows) and all has appeared to go o.k. The problem/issue I now have is "How do I get to the other drive as it does not show up in the file manager?" I would like to keep the data that is on the D: drive. Is there a way of accessing it easily??

Thank you in advance for your assistance[/QUOTE]
 Well, first off it's nothing like windows where you can switch from drive to drive, or in your case, OS to OS. If you want to run two OS's at the same time, I recommend you getting Wine to do so.

Now, if you want to get into windows, do a simple reboot and it will give you an option on which OS you wan to boot up.

If this is correct on my stating what you're asking then we accomplished something, if not please reply back with other questions.

---

### Post by Lord Kel on 2005-09-09
Thanks for the reply Steve,

I don't think I explained myself properly in the original post. 

I have replaced windows on the c drive with Ubuntu... (No more windows for you Mr PC).

The D drive is still formatted NTFS but has no OS on it just data.

What I would like to be able to do is to be able to browse what is on the d drive.

Hope this is a bit clearer.

---

### Post by racecat on 2005-09-09
[QUOTE=Lord Kel]Hi There,

I have recently (2days ago) installed Ubuntu 5.04 on an older machine that I have. Now this machine was running WinXp and had one drive (30gig) partitioned into two C: was 5 gig and D: was 25gig.

I installed Ubuntu to the C: drive (completely removing Windows) and all has appeared to go o.k. The problem/issue I now have is "How do I get to the other drive as it does not show up in the file manager?" I would like to keep the data that is on the D: drive. Is there a way of accessing it easily??

Thank you in advance for your assistance[/QUOTE]

It sounds like you just want access to the files on d. I haven't done it with Ubuntu, but I did dual boot Mandriva with Win2000 and it was just a matter of mounting the Win2000 partition to access all the files from Mandriva.

Sorry I can't be more specific, but this may get you looking in the right direction, if I understand your question correctly.

Happy trails.
Bill

---

### Post by codejunkie on 2005-09-10
[QUOTE=Lord Kel]Thanks for the reply Steve,

I don't think I explained myself properly in the original post. 

I have replaced windows on the c drive with Ubuntu... (No more windows for you Mr PC).

The D drive is still formatted NTFS but has no OS on it just data.

What I would like to be able to do is to be able to browse what is on the d drive.

Hope this is a bit clearer.[/QUOTE]
what you can do is find what partitons are on the drive with sudo fdisk -l 
it will output something like this 
```

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9634    77385073+  83  Linux
/dev/hda2            9635        9964     2650725    5  Extended
/dev/hda5            9635        9964     2650693+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4791    38483676   83  Linux
/dev/hdb2            4792        4998     1662727+   5  Extended
/dev/hdb5            4792        4998     1662696   82  Linux swap / Solaris

```
if you have a ntfs partition it will be listed somewhere in there and you can follow one of these guide's at [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) to mount the ntfs drive manually or automaticly also never write data to a ntfs drive through linux it can corrupt the data on there you can only read data from the drive hope this helps.

---

