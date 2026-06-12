---
title: "Installed Ubuntu ok, no grub boot loader after install"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by redtom on 2008-04-15
Hi, I've been through numerous threads but can't get this working...

I've installed Ubuntu 7.10 fine on a drive that already has xp pro on it, everything went ok, no problems at all. Only thing is I get no Grub menu after restart to let me choose whoch OS to launch, only a "error loading operating system" message 

Partitioning went ok, both xp and ubuntu are on the same hard drive, cd has been removed at restart, etc.

All I get is this "error loading operating system" message (or whatever it says). I can boot off the Live CD ok again and go into ubuntu's partition manager where it says the ubuntu partition is the boot one - I can set the xp partition to be the boot one and then rebooting gets me back into windows (initially I thought I had royally screwed up my machine... )

Thought ubuntu was gonna be easy!

Any ideas?

---

### Post by Yoke &amp; Chung on 2008-04-15
How many hard disks do you have?

---

### Post by SnakeHips on 2008-04-15
cut n paste this into terminal and post the output here ok

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by OffAxis on 2008-04-15
try the super grub disc to reinstall grub; it's the easiest.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by redtom on 2008-04-15
Thanks for the replies, complete newbie here...

I have 3 actual drives in the pc, one seagate and two hitachi. Ubuntu and windows are definitely on the seagate.

At work at the moment, will get to this in a couple of hrs, will post more progress then.

---

### Post by redtom on 2008-04-15
> **SnakeHips said:**
> cut n paste this into terminal and post the output here ok

```
gksu gedit /boot/grub/menu.lst
```



Ok, did this and gedit comes up with a flashing cursor on a blank screen...

---

### Post by bumanie on 2008-04-15
Could you boot with the ubuntu live cd and type > sudo fdisk -l into terminal and post its output (cut and paste). that will give us a good idea of your partitions and where grub should be pointing to. (From memory, I think that command works off the live cd). Also at boot, what error are you getting? It is probably a grub error?? (some number) at stage 1.5 - post that too if possible.

---

### Post by redtom on 2008-04-15
Here you go:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xcfa5892e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2      969021   488386080    f  W95 Ext'd (LBA)
/dev/sda5               2      484512   244193512+   7  HPFS/NTFS
/dev/sda6          484513      969021   244192504+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e44873f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26783   215134416    7  HPFS/NTFS
/dev/sdb2           26784       36080    74678152+  83  Linux
/dev/sdb3           36081       36481     3221032+   5  Extended
/dev/sdb5           36081       36481     3221001   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2240ab79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60800   488375968+   7  HPFS/NTFS

---

### Post by bumanie on 2008-04-15
Thanks for your quick reply. Your fdisk -l suggests you have windows on your first hard drive, windows on your second drive with ubuntu and windows on your third drive (or least a data saving area formatted to ntfs). I suspect your problem is that both the xp installs on hda and hdb, both have boot flags and grub didn't know which one to install to and has either not installed at all or has installed to the wrong drive. 
Before i suggest anything further could you boot with the live cd again and terminal type > sudo grub  followed by > find /boot/grub/stage1 and provide the output.

---

### Post by redtom on 2008-04-15
Ok thanks for the response

find /boot/grub/stage1 produced the following:

 (hd1,1)


those other two drives are formatted ntsf because they're part of my windows pc setup - not too bothered by them tho, just want to get ubuntu up and running to check it out

---

### Post by bumanie on 2008-04-15
So which is your main drive? Usually one would set up the first drive as the main drive. Is that your main drive or is the second drive your main drive? Is windows on drive 2 important? I think that grub has been confused by the two bootflagged windows drives.

---

### Post by redtom on 2008-04-15
Yeah, see what you're getting at... not sure how drive 1 isn't my main windows drive - must have gone a tad wonky when I was setting up those two 500Gb drives last year

Anyway, windows is on the 300Gb drive, which looks like drive 2 - thats the one I want to use

---

### Post by bumanie on 2008-04-15
This would be easier to do from within ubuntu. Could you download a super grub disc (live cd) form here [http://forjamari.linex.org/frs/?group_id=61&release_id=499](http://forjamari.linex.org/frs/?group_id=61&release_id=499) and see if that will boot ubuntu. It often works to boot an unbootable ubuntu.

---

### Post by redtom on 2008-04-16
Success!

Just disconnected the two hitachi drives before turning on the pc, booted from the Live CD, installed, got the Grub menu at restart and am now downloading 209 updates for Ubuntu...

Knew there was a simple solution - just hope when I turn off my pc now to reconnect my two other drives that no hiccups happen on booting up again.

---

### Post by bumanie on 2008-04-16
> just hope when I turn off my pc now to reconnect my two other drives that no hiccups happen on booting up again. Nothing will have changed once you connect the other two drives up again. You need to modify your drive set up, because two boot flagged windows drives is confusing grub. Unfortuantely when I was last speaking to you I had been awake for 24 hours and had to get to sleep after I finished work.

---

### Post by redtom on 2008-04-16
thanks for your help anyhow, i'll hook up the other drives soon and see if anything happens

---

