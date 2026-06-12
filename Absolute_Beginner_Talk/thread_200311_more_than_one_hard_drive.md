---
title: "more than one hard drive"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by alastair mccracken on 2006-06-20
I was given an old sony vaio laptop by my sister when she upgraded and have recently had lots of fun trying out ubuntu, and linux, for the first time. I first installed 5.10 and have now upgraded to 6.06 I have to say I am very impressed and have enjoyed getting ubuntu working the way that suits me. I have found both the starter guide and wiki/forums very helpfull but cannot find any help when it comes to multiple hard drives.

On Administration - Disks it appears this old laptop has 3 - yes, Three - hard drives. /dev/hda of 18.63 GB with my ubuntu and memory partitions, /dev/sda with no further information or partitions and /dev/hde with no further information or partitions.

How do I get ubuntu to recognise/partition these hard drives so that I can use them from within ubuntu?

On my Windows box I have two hard drives, one of 60GB with windows and other applications on it and one of 80 GB which is my music library - all controlled from within windows. It would be good to have a similar setup here.

By the way, remember folks I'm a baby when it comes to this stuff, so make it simple and step by step.

---

### Post by anaconda on 2006-06-20
Does it have a CD-drive.. that could be hde

Does it have memory-card-reader it could be sda..

What is the output of 
sudo fdisk -l
written to terminal?

---

### Post by dvarsam on 2006-06-20
As "anaconda" replied, you have to provide more info from your side!

Launch a Terminal window (from Menu, select "Applications\Accessories\Terminal"), & do the following:

1. Type "sudo -i"
2. Type your password
3. Type "fdisk -l"
4. Select the info (using your mouse), shown inside your Terminal window.
5. Copy the info (using Ctrl+Shift+C), shown inside your Terminal window.
6. Paste the info (using Ctrl+V), inside this Thread.

Help us to help you!

Cause without some feedback from your side, it is hard for us to provide help to you....

Thanks.

---

### Post by ifokkema on 2006-06-20
[QUOTE=anaconda]Does it have a CD-drive.. that could be hde[/QUOTE]

I myself occasionally use
```
cat /proc/ide/hdX/model
```
to see how my drives are arranged (don't forget to replace the X with the correct name).

This command returns the model name of the device. If it, for example, reads:
```
WDC WD400BB-75DEA0
```
it's a hard drive (Western Digital in this case)
My CD-RW drive returns:
```
HL-DT-ST GCE-8400B
```

You can also look around in the list presented by:
System -> Administration -> Device Manager
System -> Administration -> Disks

---

### Post by alastair mccracken on 2006-06-20
Sorry folks, 
been away all day.

The information requested by dvarsam is:-

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2339    18787986   83  Linux
/dev/hda2            2340        2432      747022+   5  Extended
/dev/hda5            2340        2432      746991   82  Linux swap / Solaris

which doesn't mention /dev/sda or dev/hde which both show in Administration - Disks

As for ifokkema's suggestion - I get a model from hda but "no such file or directory" from both sda and hde

This laptop has a removable cd-rom through PCMCIA and a removable USB floppy - neither of which are connected at the moment. In Windows when you remove a drive it no longer shows up - would linux remember that I once had these drives connected?

I guess I'll ring my sister tonight and ask her if she ever had any extra HD fitted to this box.

Thanks for taking an interest folks. Any further ideas very welcome.

---

### Post by ifokkema on 2006-06-20
[QUOTE=alastair mccracken]The information requested by dvarsam is:-

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2339    18787986   83  Linux
/dev/hda2            2340        2432      747022+   5  Extended
/dev/hda5            2340        2432      746991   82  Linux swap / Solaris

which doesn't mention /dev/sda or dev/hde which both show in Administration - Disks[/QUOTE]
How exactly do /dev/sda and /dev/hde show up in the disk manager list? As hard drives? What kind of information is provided when you select either one of these drives?

[QUOTE=alastair mccracken]As for ifokkema's suggestion - I get a model from hda but "no such file or directory" from both sda and hde

This laptop has a removable cd-rom through PCMCIA and a removable USB floppy - neither of which are connected at the moment. In Windows when you remove a drive it no longer shows up - would linux remember that I once had these drives connected?

I guess I'll ring my sister tonight and ask her if she ever had any extra HD fitted to this box.[/QUOTE]
I don't think there will be a separate HD, since that will show up as hdb or the like and definately have some 'model' information in /proc/ide/.../model. But if the drives you mentioned are not connected right now... I have no experience with PCMCIA connections, but the 'hde' and 'sda' names suggest one IDE drive (hde) and one SCSI(-sumulated) drive, such as an USB device.

---

### Post by alastair mccracken on 2006-06-20
Hope this works - I've taken screenshots of Administration - Disks and attached them to this message. Hopefully!!!!

---

### Post by alastair mccracken on 2006-06-20
Folks,
I'm gonna go and watch Sweden beat England - hopefully!

I'll check back with this thread tomorrow (maybe tomorrow night)

Thanks for your time.

---

### Post by ifokkema on 2006-06-20
[QUOTE=alastair mccracken]Hope this works - I've taken screenshots of Administration - Disks and attached them to this message. Hopefully!!!![/QUOTE]
Hmm..... does the 'partitions' tab show anything useful?

Also, I thought of this:
what if you search the kernel log (/var/log/kern.log) on the terms 'hde' and 'sda'? Anything useful there?

---

### Post by bruce89 on 2006-06-20
[QUOTE=alastair mccracken]Folks,
I'm gonna go and watch Sweden beat England - hopefully![/QUOTE]
I hope so too, you can watch it by doing this - ```
telnet diego.ascii-wm.net 2006
```
[QUOTE=alastair mccracken]Hope this works - I've taken screenshots of Administration - Disks and attached them to this message. Hopefully!!!![/QUOTE]
Could you open the partitions tab on the right, /dev/hde is a CD-drive, and I guess that /dev/sda is a card reader.

---

### Post by alastair mccracken on 2006-06-20
Okay,

my sister says only one hd of 20GB ever fitted to this box - so I think all the comments about the other two drives being CD-ROM or card readers etc etc must be correct. I'm going to assume that unlike windows Ubuntu holds onto the presence of removable drives even when they are not there.

Thanks for the thoughts and time and effort from everyone. I have to say I like this whole community thing with Ubuntu.

Pity about the result of the Sweden/England match - it would have been nice for England to face Germany in the next round.

---

