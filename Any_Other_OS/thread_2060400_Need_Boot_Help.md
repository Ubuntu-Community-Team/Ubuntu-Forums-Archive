---
title: "Need Boot Help :/"
date: 2012-09-20
forum: Any Other OS
---

### Post by statphantom on 2012-09-20
[FONT=Arial]Hey guys just some background info (sorry if this is the wrong place, I am new to these forums). I work in a computer repair and warranty shop and we got a customer a few days ago about her Windows 7 Home Premium laptop no longer able to boot. I had a look at it and sure enough, no booting. I thought this was just a regular OS repair but it turns out it was deeper then that.

First I tried to view the drive in the test machine to see if the HDD was physically damaged and here's the strange thing, Ubuntu cant see the drive at all, but BIOS and Windows XP can (Dual Boot from the same machine) so, obviously, the first thing I did was back up the files then decided to try some more advanced techniques.[/FONT] [FONT=Arial]

Since ubuntu cant see it (not even in "sudo fdisk -l) I thought it could have a problem with the MBR, so I put the HDD back in the laptop and booted to ubuntu live netbook edition and when booting to CD I realized that her laptop BIOS doesn't see her HDD either, after a bit of research I found a program known as boot-repair, that is for fixing the boot sequence and mainly the MBR that I could tell. After installing the Repositories and apt's for it, it ran, saw the HDD, and after a few minutes said "boot successfully repaired, please restart your computer and try to Boot" however I still couldn't. The results for the Boot-rep[/FONT] [FONT=Arial]air is posted here, [/FONT]
[URL="http://paste.ubuntu.com/1216176"]
[/URL][FONT=monospace][http://paste.ubuntu.com/1216176](http://paste.ubuntu.com/1216176)

[FONT=Arial]I did have a look through it but since I am not even close to an expert on computers I didn't understand to much from it but no obvious errors were showing that I could see.

I know most people would have just given up and said "sorry we cant fix it" but it is really interesting to me.

Please any help? thanks.[/FONT]


[/FONT]

---

### Post by Rokel on 2012-09-20
As far as I know you don't have to have anything on a drive to 'see'  it (e.g. using fdisk). Not even a boot record, partition or formatted filesystem.

Of course in ubuntu you would need the drivers for the harddisk controller to be loaded.

'BIOS doesnt see it'  you mean during self test/autodetection you don't see any evidence of a hard drive connected? Sounds like cable/plug/power/drive PCB problems to me, intermittent because you do see them on that other machine.

I don't think you should talk about 'not booting'  and 'OS repair' if the harddrive is completely missing from BIOS detection. 
Not booting would be more like "No bootsector found on harddrive" or "Starting windows,.." and then it stops

Spinrite by grc.com is a brilliant low level hd diagnosis and repair tool, a must for a shop.

---

### Post by pyrokinetic on 2012-09-20
Back to basics, check all cables are being plugged in correctly first and hooray for backing up!

I've repaired computers for a while now and I have seen this kind of behaviour before, usually not long before a drive is ready to die.

---

### Post by YannBuntu on 2012-09-20
Hello

> **statphantom said:**
> http://paste.ubuntu.com/1216176

BCD is missing on sda1.
Please try to move (via [Gparted]("https://help.ubuntu.com/community/GParted") or else) the 'boot' flag from sda1 to sda2.

---

### Post by oldfred on 2012-09-20
Moved to Other OS sub forum since a Windows issue.

If BIOS does not see drive, then there is not much you can do besides making sure all connections are good.

From Ubuntu liveCD you can go into Disk Utility and click on drive. On right side is Smart Status. All I really know is green is good, but it can run a variety of tests.

It looks like Boot-Repair was able to mount partitions. If NTFS has errors Linux' NTFS driver will not mount to prevent further damage. But it might not hurt to run chkdsk from a Windows repairCD or USB.

---

### Post by statphantom on 2012-09-20
Thanks for all the support, I did check the SMART and seems all ok and yes, I did make sure all the plugs/cables are fine. I will be a bit more specific of what can see what.

Machine 1: test desktop, dual boot ubuntu 12.04 cant see it but windows XP can in its disk manager. (so probly a driver or an ubuntu apt not installed that's needed.)

Machine 2: cust. laptop. BIOS doesn't see the drive to boot from or in its Setup to configure it but the ubuntu net book edition live CD 10.04 can see it. 

So because of this I doubt its a cable/connection problem. I will try to move the boot flag to sba2 using gparted and see how that goes, I will edit this post with my results.

---

### Post by oldfred on 2012-09-21
Several versions ago, I had gparted not even show my entire sda drive which has XP. XP booted, but after running chkdsk gparted then showed drive & XP booted a bit faster.

The NTFS driver in Linux often will not mount a NTFS partition if the chkdsk or hibernation bits are set. That is to prevent damage that chkdsk may not then be able to fix. But the newest versions still seem to show partition/drive exists.

---

### Post by statphantom on 2012-09-21
Ran GParted and saw an exclamation icon next to sda2, so I tried to run a check/fix from GParted but it said found 32 bad sectors, run chkdsk on windows and reboot twice then run GParted again. Did that but its still saying 32 bad sectors, so I decided to just move the boot flag to sda2 and restarted the laptop, still not able to boot into it. I'm just spit balling here but I think the BIOS version on the cust. laptop wont view a drive with bad sectors (no idea why it would go that far) anything else anyone could suggest I try?

---

### Post by oldfred on 2012-09-21
IF a NTFS partition, Linux can only run ntfsfix which does only minimal fixes and sets chkdsk flag on NTFS partition. You really have to run chkdsk from Windows repair console or repair console in Windows repairCD or USB.

---

### Post by statphantom on 2012-09-24
I'm surprised Linux has such restrictions even being for a NTFS partition. I have tried chkdsk from the command prompt and still wont fix it. I guess its a mystery that wont be solved, sorry guys.

---

