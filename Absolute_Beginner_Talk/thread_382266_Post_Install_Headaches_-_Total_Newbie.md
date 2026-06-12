---
title: "Post Install Headaches - Total Newbie"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by JesuSlaveX on 2007-03-11
OK, so I've finally decided to give Linux a legit try.  Beryl is just stunning, and its something that I've been looking for on windows for a while.  After a REALLY miserable time with VISTA, I've finally decided to kick my windows relationship, which I view as a battered wife who keeps going back for more.  So as for this post, I know that I will appear that I'm still thinking as a windows user.  I'm trying really hard to wrap my head around the new OS, its really intuitive, but functionality isnt my problem

Heres my specs:
1.8 Ghz
512 RAM
Hard Drive 1 (windows XP Sp2) ***hda
Hard Drive 2 (no OS, storage only) ***hdb
Grforce 5200 (AGP)
Geforce MX 4200 (PCI)

Dual boot went great!  Super easy

I was wanting to take my slave drive, cut it in half and use hdb1 for linux and hdb2 for file storage (NTFS) for my windows install.  I assume that I can mount that in linux, but as for now its not my main concern.  I downloaded Edgy Eft, install went pretty well, though I had some partition issues.  Did a second install, and still didnt get it right. But I decided I might be able to live with it so I continued on.

The Ubuntu install only picked up my 5200 (AGP) and my other card wasnt.  I really want to be able to use my duel monitors with Beryl.  I searched through the "this the software you can download" thingy :lolflag:  in the control panel.  I tried to download the NVIDIA control panel and the updated drivers.  It downloaded and asked me to restart.  Computer Freeze on STARTING UP screen.

Well, crap

Reinstall OS again.  Went on to the Nvidia website for linux AI32 drivers (not that I would even know how to install them).  Site said that I needed to remove the "linux-restricted-modules".  Downloaded the drivers, uninstalled the "linux-restricted-modules".  Restart, froze up at the exact same place.

Reinstalled Linux again, but this time, I screwed up (out of frustration) and I now have 2 linux installs, and on windows install........ya

OK, repartitioned my slave drive, fixmbr on my windows xp, came here

So in all this, here are my questions

1 - I want to split my hdb into 2 parts, one for linux, the other for storage (something I can link both OSs to.  How do I do it?

2 - Is there any way on this earth that I can edit anything on my linux to keep it from freezing.

3 - Once its all said and done, installed correctly and all, what do I do to get my video cards to work for dual displays.

Sorry about the newbieness, but I'm Linux retarded and really want to get away form windows.  HELP!!!

---

### Post by Famicommie on 2007-03-12
As to your partition question:

Windows doesn't know how to share with linux, but it's possible for linux to share with Windows. So, to that end, I recommend simply partitioning the drive as part for linux, and the rest as NTFS.

To mount the NTFS partition, follow the instructions given in the System Documentation.

1. System->Help->System Documentation
2. Ubuntu Desktop Guide->Configuring your system->Partitions and Booting

To get read/write access to the partition follow the [guide by givré](http://ubuntuforums.org/showpost.php?p=1263001&postcount=1)

Hope that helps with at least the one question.

---

### Post by eljalill on 2007-03-12
Just a piece of my (not very big) experience: I have dual boot, and both OS share an ext3 partitition with data.
I had to install the ext3 drivers in Windows first, but now it works fine.

I never found the write-access to ntfs less than optimal.. it was not very fast when I tried it out (half a year ago) .

---

### Post by JesuSlaveX on 2007-03-13
Well thats cool.  It gives me some hope for the future on the feature I'm looking for.  But, more things have happened

After I got some sleep, I re installed Edgy with, what I think, the correct partitioning is.  It installed fine, the boot loader works great.  Once I got everything up and running, for the first time it informed me that I had an auto update.  It DLd a bunch of files and asked me to restart.  Upon restart, it froze in the same freaking place.  nothing but STARTING UP on the screen....forever.  So, I loaded the recovery mode style, it stops on this:

[17179573.988000] pnp: 00:dd: IO Port Range 0x295-0x296 has been reserved

Upon further inspection of previous lines, it appears that there was a previous entry a few lines up that said this

[17179570.472000] pnp: 00:02 IO Prot Range 0xe4000-0xe47f could not be reserved

It pretty much stays there forever.  I even let it sit about 3 hours.

Would this be a windows equivalent to an IRQ conflict?  If it is, why would it work on initial install, but start after I update ANYTHING?

---

### Post by btolle on 2007-03-13
As a total newbie to Linux I tried Edgy and had some problems. Decided to start over. Bought the book "Ubuntu Unleashed" which includes a DVD with Dapper (6.06) on it and installed that and it has been a better experience.

I, too, always want the "latest and greatest" but when it comes to software "tried and true" is often better.

Just my 0.02.

---

### Post by JesuSlaveX on 2007-03-13
I have to say in my defence, I used Edgy out of complete ignorace.  

To add to my previous post though, I think it is an IRQ conflict.  When I logged back into windows, it installed new hardware (New partition on my drive I believe)

But why would that pop up now, and not immediatly after the install?

---

