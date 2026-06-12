---
title: "Grub error 5 after new SATA hard drive"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by ukblacknight on 2008-03-31
Hi folks,

I bought a new 500gb SATA drive the other week, and decided to plug it in on Saturday.  I've got:

250gb SATA drive: Vista has about 210gb and Ubuntu 7.10 has the rest
120gb PATA drive: Just contains media.

Oddly, when I first installed Vista, it put MBR onto the PATA drive, even though I installed it to the SATA drive (this was before Ubuntu).  I resolved this by changing the boot order in BIOS so that the 120gb drive booted first.  I had no problems after that, even after installing Ubuntu.

But anyway, I had the intention of removing the 120gb PATA and replacing it with the 500gb drive.  I plugged the 500gb drive in, leaving the 120gb PATA drive in, booted up and stopped at grub: Error 5.  Anyway, I unplugged the drive, loaded grub, selected Windows Vista, that started, and I plugged in the SATA drive (i had it out of the box).  Windows detected the new drive, installed the drivers and asked me to restart.  Anyway, i switched the machine off, removed the drive top stop grub complaining and plugged it back in again once the grub menu was up.  Selected Windows - it starts to load but then BSOD's and restarts!  This keeps happening even if I don't plug the drive back in.

So basically, my Vista setup is screwed.  Ubuntu still works perfectly.  I have a few issues that need seeing to here:

1) How can I stop grub from the error 5 issue?  Do I need to edit something in Ubuntu to allow the drive to show up?
2) I need to repair my Vista setup (this can be done via the CD) - however I fear that it will over-write grub with MBR - how do I replace MBR with grub?
3) I need to move MBR/Grub to the 250gb SATA drive because the PATA drive will be coming out


I have no net at home so I won't be able to perform fixes on the fly (i'm at work right now).

If anyone could help it would be much appreciated. :)

---

### Post by bumanie on 2008-03-31
Quoted from the GNU/GRUB manual

    5 : Partition table invalid or corrupt
        This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 

Check the partition table by running fdisk as root ('sudo fdisk -lu) in Linux, or use your favourite partition editing software to make sure one of your partitions has been marked 'active'.

If no partition is marked as active, you can use Super GRUB Disk to do that for you.
If more than one partition has already been marked as active, you need to remove the 'active' flag from one of them, as only one is supposed to be set as active at a time. Use your partitioning software of that.

Read this site it has heaps of information on grub. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ukblacknight on 2008-03-31
So are you saying that my new drive is damaged?  It hasn't been formatted or anything yet.  It's worth noting that the new drive was appearing at Channel2 Master, where as the original 250gb drive was appearing at Channel3 Master.  Would this effect grub at all?

Cheers for the link, I'll have a look at it.

To check the new drive, wouldn't it need mounting?  I have no idea how to go about doing this.

Thanks.

---

### Post by bumanie on 2008-03-31
I guess if it hasn't been formatted that is why there is the reference to the partition table being invalid or corrupt. It is a quote from the GNU/GRUB manual which is on the site I pointed out. You really should read Herman's site it is extremely informative re grub and grub problems. I think the plugging and unplugging of drives has probably confused grub. Hopefully there has been no data loss. Also try super grub disc as suggested by Herman, many people have success with it. Get it here (choose live cd) [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

