---
title: "Problems with fsck at boot"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-02-11
Hi guys,

When my systems boots up the progress bar stalls for a few seconds just below the second U in the Ubuntu logo, then the graphical display dissapears and I get a message that says "Checking File System", followed by a line that refers to *fsck*.

I've had a search here in the forum and the advice seemed to be to remove the 2s from /etc/fstab and replace them with 0s.  I've done that but it isn't making any difference.

Is there anywhere else I can check, or anything else that I can try?

For reference, my /etc/fstab/ is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5e656ecc-b906-44b3-8645-334114dcdf33 /               ext3    defaults,errors=remount-ro 0       0
# /dev/hda4
UUID=c74cc6aa-97ba-40d3-b857-91cec17dd797 /home           ext3    defaults        0       0
# /dev/hda1
/dev/hda1   /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=rob,uid=rob 0       0
# /dev/hda2
UUID=94e5c730-a404-4d91-8c55-bb03a517a61d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by jpeddicord on 2007-02-11
The checking file system action occurs once every 30 startups. All it does is make sure your drives and filesystem are running correctly. Try waiting a while to see if it does anything. If nothing happens, try recovery mode from the GRUB menu to check to see if it will still boot.

---

### Post by Catsworth on 2007-02-11
I understand that, but this happens _every_ time I boot.  Sometimes it stalls for about 15 seconds and then carries on booting, sometimes I can wait for a minute or so before being presented with teh graphical login screen.

---

### Post by mcduck on 2007-02-11
Root partition should run fsck, and I'd recommend it for /home too. But not for NTFS partition. Anyway, try with this one:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5e656ecc-b906-44b3-8645-334114dcdf33 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=c74cc6aa-97ba-40d3-b857-91cec17dd797 /home           ext3    defaults        0       2
# /dev/hda1
/dev/hda1   /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=rob,uid=rob 0       0
# /dev/hda2
UUID=94e5c730-a404-4d91-8c55-bb03a517a61d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by Bartender on 2007-02-11
Do a search regarding "UUID".  I don't understand this entirely, but Edgy added that  "UUID=xxxxxxxx" stuff as some sort of error check.
Dapper just listed the automounted partitions without the UUID identifiers.  In other words, your partitions would be

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
/               ext3    defaults,errors=remount-ro 0       0
# /dev/hda4
/home           ext3    defaults        0       0
# /dev/hda1
/dev/hda1   /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=rob,uid=rob 0       0
# /dev/hda2
none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0 
```

See the difference?  Unfortunately, the lines are messed up so it's hard to tell what's supposed to be on the same line but if you compare carefully you'll see.  Although Edgy introduced this change, you don't have to use it.  You can remove the UUID and it'll still work.  I had a problem with UUID under a multi-boot situation.  The boot Linux distro lost track of the other distro's and gave me a weird fsck error message.

Yours appears to be a straightforward single boot so I'm not at all sure that UUID is causing your problem.


You could try pasting in the above or deleting out the UUID data yourself as long as you make sure to save your existing fstab!!  Because I'm not at all sure it's going to help you and you'd probly want to put it back to where it is now in case removing the UUID=xxxx part doesn't work.

---

### Post by Catsworth on 2007-02-11
Ok, tried your second fstab, and it all went horribly wrong :( 

Couldn't log in because the system claimed that my home directory didn't exist.. Had to boot into the failsafe terminal and cp the backup that I created back over the top of the new one.

Any other thoughts?

My Laptop's now stalling for about 2 minutes every time I boot :(

---

### Post by Galban on 2007-02-12
Exactly the same problem here (like Catsworth has) and looking forward to see somebody giving us the magic solution, I'd been having this problem for couple months now and after I did a system update with synaptic. Edgy had been particularly buggy compared with Dapper but one thing is for sure, this problem wasn't there since I first installed Edgy.                                   :?

---

### Post by mendingo84 on 2007-02-12
i had the same problem and solved it by modifying fstab. i think the problem is related to repartitioning with Gparted prior to installing Ubuntu...
Oh well...this is what my fstab looks like:
> 
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=91bbd05f-9866-4c82-a737-328cd85bc1e4 /               ext3    defaults,errors=remount-ro 0       0
# /dev/hda1
UUID=4AE47F21E47F0E87 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=8A3F-CAFA  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda4
UUID=509cdfcd-771c-426c-a5f1-0d4974b432ad none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


---

### Post by mcduck on 2007-02-12
Maybe there's something wrong with the way GPartedit sets the max count for fsck.

Try running 'sudo tune2fs -c 30 /dev/hda1' (replace hda1 with right device) for all ext3 partitions, and then editing fstab so that / has '1' as the last number, and other ext partitions have '2'.

---

### Post by Catsworth on 2007-02-12
Ok, tried that.

First time through it forced a check saying that /dev/hda3 hadn't been checked in 40 boots, and /dev/hda4/ in 38 boots.  Then it hung for 2 minutes.  Then it booted into Ubuntu.

second (and subsequent) times through it reported both as clean, hung for two minutes, and carried on.

Any more suggestions?

Thanks.

---

### Post by Galban on 2007-02-12
Tihis problem is now resolved.

Watching to the "mendingo84" fstab and comparing it to mine I found that every device on the mendingo84's fstab is finishing with two zeros and mine with 0 and 1. I just changed that "1" with a "0" (zero) and the problem is gone. No more GRUB's messages about fsck chenking files systems at the boot time. :) . I just wonder why Catsworth still getting that message at the boot time even two zeros in his fstab :confused:

---

### Post by Catsworth on 2007-02-14
Hi,

Anybody got any more thoughts on this.  Having to wait 2 and a half minutes to boot Ubuntu every time is driving me crazy.....

Thanks.

---

### Post by P235 on 2007-02-14
[http://www.ubuntuforums.org/showthread.php?t=355139&highlight=fsck]("http://www.ubuntuforums.org/showthread.php?t=355139&highlight=fsck")

---

### Post by Catsworth on 2007-02-14
> **P235 said:**
> [http://www.ubuntuforums.org/showthread.php?t=355139&highlight=fsck]("http://www.ubuntuforums.org/showthread.php?t=355139&highlight=fsck")

I don't mean to be rude but.....

either:

a) I've missed something here, or
b) You've not read the whole thread.....

I don't see anything in the thread that you've linked to that I haven't already tried.  The tune2fs command is all very well but (as you can see from the earlier posts in this thread) I've tried that and it hasn't worked.  

This doesn't appear to be the standard check, because it doesn't list any files/errors, it just seems to hang for a couple of minutes and then carry on.

Thanks for trying to help though, it's appreciated.

---

### Post by Catsworth on 2007-02-17
There's a _chance_ that this might not be an fsck problem.....

I've just had my laptop plugged into a router via Ethernet, when it's plugged in to the router there isn't a pause/hangup in the boot process - Ubuntu boots as normal.....

---

### Post by btoone on 2007-03-08
Catsworth, your last post made me realize that I had my laptop (hp compaq nc2400) plugged into its docking station.  Out of desperation, I un-docked the laptop rebooted and it came back without hanging in fsck.  No edits to the fstab file required.  Thanks.

---

