---
title: "[SOLVED] Read/write to HFSPLUS devices"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-10-10
Hi,
Can Linux (feisty) natively read/write to pre-formatted Apple HFS+ devices ??

If not, is there software that can be installed to make this possible ??

---

### Post by Tteddo on 2007-10-10
I have the same question, with mount I tried specifying -t hpf+ or just hpf but it gives me a mount error.

---

### Post by tgalati4 on 2007-10-10
You have to turn journaling off.  Read/write is support on an HPFS+ system but no write capability with journaling enabled.

When you restore an iPod using a Mac, sometimes you have to turn journaling off if you reformatted using Disk Utility.  It's happened to me a few times.

Turning off journaling is usually not destructive to the existing data on the partition.

---

### Post by ayenack on 2007-10-10
Hello Steve, Tteddo. Don't know if you've done this but you need to turn Journaling off in OS X.

Applications/Utilities/Disk Utility (Choose what drive to switch it off on.)

To turn it back on, click the Enable Journaling button or choose Enable Journaling from File menu.

Then.

**sudo -i** (Password)

**mkdir /mnt/osx** (Your choice for the name.)

**mount -t hfsplus /dev/hda1 /mnt/osx** (Replace /dev/hda1 with the name of the drive.)

That's it. Ubuntu does natively support hfsplus. By the way the drive must be listed as "hfsplus" under drive type in fstab.

[B]gksudo gedit /etc/fstab
[/B]

To mount.

**sudo mount -t hfsplus /dev/hda1 /mnt/osx**

To unmount type.

**sudo umount /mnt/osx**

To find out what drive is your hfsplus drive do this.

**sudo fdisk /dev/hda**

Then.

**p** (This will list the drives.)

**q** (To quit.)

Well hope that helps. ayenack.

---

### Post by Tteddo on 2007-10-10
It's a hard drive from a dead mac I am trying to get data from. I guess I didn't know the fs type (hfsplus) for the mount command. 
I'll give that a shot! Thanks!

---

### Post by steve-shinn on 2007-10-11
Sorted .... thanks all

---

### Post by ayenack on 2007-10-11
Mark as solved so others can learn from your experience ;))

---

### Post by poochy on 2007-11-11
Guys can someone please help? I tried the umount command with sudo and it did not work, saying that the bash shell did not recognise such a command.
This is exactly what i typed:
"sudo unmount /mnt/macosx"
where /mnt/macosx is my mount point. can some one help please?

P.S. I am using Ubuntu 6.10 on a TiBook G4 15"

Thank you

---

### Post by Tteddo on 2007-11-11
The command is umount, not unmount
Cheers!

---

### Post by ayenack on 2007-11-12
Doh... always do that. Now fixed.

---

### Post by Tteddo on 2007-11-12
Mmmm....Pizza.....

---

### Post by ayenack on 2007-11-14
LOL

Mmmm Duff.... BUUuuurrrrpp. (_8(|)

---

