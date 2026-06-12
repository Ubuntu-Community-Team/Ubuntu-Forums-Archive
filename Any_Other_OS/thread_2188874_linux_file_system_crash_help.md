---
title: "linux file system crash help"
date: 2013-11-19
forum: Any Other OS
---

### Post by weezilla on 2013-11-19
Hi, first off, and I'm skeptical to say because I really want help here, this is a Red Hat Enterprise machine. However, I'm fairly certain this problem and solution is general to linux. 

We have an NMR instrument (like an MRI) at my university, attached to a computer running Red Hat Enterprise 5. We had a file system crash, due to a researcher running fsck -y (while drives mounted). This has happened before and it's been repaired before, but the notes for the solution are not available for reasons beyond the scope of this thread. Anyhow, it is very important we recover the data/operating system without corrupting it further in the process (contains data to-be-published). Last time, a full recovery was possible. 

So, onto the problem. When it attempted boot after the fsck, we saw [https://www.dropbox.com/s/yv81bp9cazvnp7r/20131030_162800.jpg](https://www.dropbox.com/s/yv81bp9cazvnp7r/20131030_162800.jpg). This screen scrolls and shows one or two other messages (see folder link at bottom for more images). 

Upon restart, we see this: [https://www.dropbox.com/s/6olgb8p7zob5uij/20131111_114317.jpg](https://www.dropbox.com/s/6olgb8p7zob5uij/20131111_114317.jpg).

Booting into a live disc, we see this: [https://www.dropbox.com/s/fpzt64kucwurcdy/20131114_114200.jpg](https://www.dropbox.com/s/fpzt64kucwurcdy/20131114_114200.jpg).

I've been instructed to run a e2fsck -y in live, but I've read that special things need to be done to use an e2fsck on lvm partitions, which I can try, but I don't want to risk making a salvageable situation an impossible situation. I also want to make sure the lvm is actually an lvm, since it assumes the lvm by "using metadata type lvm2". 

I just got an email from the instrument company helping me troubleshoot it saying > My Linux support specialist looked at your outputs and at the partition structure (from the live disk pictures) and told me It looks to him like you had a RAID configured and that he cannot help with that. 

I know this same problem was recovered in 2011 (I was here, but don't remember what commands the Dell technician told me to type). That being said, it seems like this can be fixed. My next step was to ask IT if they can ghost the drive to make a backup, then attempt an fsck of the lvm (I've already e2fsck'd the /boot).

If anyone can give better advice, or confirm that an fsck on the lvm won't break it further, then I can skip the ghosting. 

I know this is a lot, but I don't want to overlook any aspect since this is a potentially expensive problem, not to mention the research data that would be lost.

Thanks a ton for any help. Here is the folder full of other screenshots: 
[https://www.dropbox.com/sh/7luou7osn3s1ia4/v6fN8yrgV8](https://www.dropbox.com/sh/7luou7osn3s1ia4/v6fN8yrgV8)

---

### Post by oldos2er on 2013-11-19
Moved to Other OS/Distro Support.

---

### Post by tgalati4 on 2013-11-20
What prompted the original* fsck*?  Was the system acting up and someone thought an *fsck* would fix it?

Typically, in this situation, you would boot the system with a Live CD or DVD (with Fedora, and preferable the same kernel version), then, while running from RAM and your system disk unmounted, you can run a full *fsck* (no automatic fix or yes mode).  Then go through and manually fix the errors.  It's helpful to make a log as to what errors were fixed, so you have a record as to how much damage was done.  Some files may get lost--any application that was left open, notepads, instrumentation, etc.  So expect some data loss in this situation.

Shutdown, remove the Live CD, and reboot.  Now check for file integrity for your research project.

Other than the 160 GB boot drive, is there another drive or set of drives that are set up in a RAID?

There is a warning about running *fsck* on a mounted root partition--it will cause damage and data loss.  I think newer versions of *fsck* have an auto-abort:

tgalati4@Mint14-Extensa ~ $ sudo fsck /dev/sda3
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda3 is mounted.
e2fsck: Cannot continue, aborting.

---

### Post by weezilla on 2013-11-20
Hi tgalati4, thanks for the response. The original fsck was entered by a user who found a (really old) troubleshooting manual, from wayyy before I was here. They thought it might fix a queue hang in the software. I have since obliterated that sheet of paper.

Luckily, I don't think any software was open when fsck was run (terminal,OS, and perhaps background communication with instrument hardware). Ughh, I meant to say Red Hat. I'll correct my original post. Anyhow, hopefully Red Hat Enterprise 5 has a live option. Otherwise, I've been using Ubuntu 11.04 live. 

I'm still concerned about running fsck without having a disk clone, which I'm working on as I write this. I downloaded clonezilla and made a bootable USB. I have an external hard drive empty and ready for the destination image. I'm stuck now trying to decide whether to use "device-image" or "device-device" clone. I would like to have something that I can restore to the hard drive exactly as the way it was when I cloned it.**edit ->

I'm now doing a clonezilla device-image backup to an external hard drive. As another precaution, from inside ubuntu live, I previously did a fsdisk export and a parted export of the partition structures. 

After that, I suppose I'll attempt my fsck across all partitions.

---

### Post by weezilla on 2013-11-20
Clone is complete. Booted to Red Hat Enterprise 5 installation cd, entered rescue mode. When prompted to attempt mounting partitions, I opted to SKIP mounting. Upon shell becoming available, attempted: 

```
sh-3.2# fsck /dev/sda

e2fsck 1.39 (29-May-2006)
WARNING: Couldn't open /etc/fstab: No such file or directory
e2fsck 1.39 (29-May-2006)
Couldn't find ext2 superblock, trying backup blocks . . .
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>
```

I found this: [https://bugzilla.redhat.com/attachment.cgi?id=529744&action=diff](https://bugzilla.redhat.com/attachment.cgi?id=529744&action=diff) I don't know what it means, but it has the fstab msg and some other similar messages. 

Meanwhile, while I hope and wait for someone to interpret the above, I'm going to boot ubuntu live and try fsck from there to see if somehow I get different results. 

Much thanks.

---

### Post by weezilla on 2013-11-20
Booted into Hiren's boot CD and ran the parted linux recovery OS (had to use Hirens because ubuntu live didn't have lvm2 package installed, which activates the lvm partition, which is necessary to do an fsck)

Did an e2fsck -y /dev/VolGroup00/VolGroup01

It 'corrected' lots of things. Rebooted and now I get the message

setuproot: moving /dev failed: No such file or directory
setuproot: error mounting /proc: No such file or directory
setuproot: error mounting /sys: No such file or directory"
ERROR opening /dev/console: No such file or directory"
Trying to use fd 0 instead.
WARNING: can't access (null)
exec of init ((null)) failed!!!: Bad address
Kernel panic - not syncing: Attempted to kill init!
Kernel alive

and it just hangs there. It seems like this made things worse. I'm not sure what to try next. I think I'll restore the original image and start over again. 

I am in big need of help, since my limited knowledge/ideas has been exhausted.

Thanks

---

