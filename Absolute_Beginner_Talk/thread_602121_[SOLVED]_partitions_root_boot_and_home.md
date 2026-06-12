---
title: "[SOLVED] partitions root boot and home"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-11-03
[FONT="Comic Sans MS"]Just wondering about partitions.
I've, naturally, got root and home but I've seen many threads where a boot partition is also recommended, without mentioning why. Whats the purpose/advantage?

I keep all my files on a separate partition to prevent loss in case of reinstall, (frequent).
On Aysiu's site he mentions doing this to keep his 'settings' intact.
Not sure what that means. None of my settings are ever kept after a reinstall.

I haven't had any problems without a boot partition and this is only for the sake of furthering my understanding.[/FONT]

---

### Post by skymera on 2007-11-03
i have no boot,
but people reccomend a serperate home, to keep alll settingd blah blah.

---

### Post by Duck2006 on 2007-11-03
You use a MBR to hold the loader to load your system thats what a boot partition is. It,s only a small partition say 50Mb in size.

---

### Post by ruibernardo on 2007-11-03
If you have an encrypted / partition, you will need a separate /boot partition.

---

### Post by carloslosgrande on 2007-11-04
[FONT="Comic Sans MS"]I don't have an encrypted partition. Is this for physical or net security?

So GRUB sits on this boot?

[COLOR="RoyalBlue"]How would it keep my settings?? this part is what I don't get.[/COLOR]:confused:

Currently I keep a list of .deb files with this [COLOR="Red"]dpkg --get-selections | grep -v deinstall > ubuntu-files[/COLOR] and I've also got [COLOR="Magenta"]apt on cd[/COLOR] which I'm just trying out.
 Thanks guys.

I tried partimage but had a big problem with it.
Passion-fingers I reckon.[/FONT]

---

### Post by ruibernardo on 2007-11-04
I referred the case of / encryption because it's a case when you do need a separate /boot partition. Another case was before Feisty, if you used a XFS filesystem (like I do) in /, you had to had a separate /boot partition. There are other cases also.

Generally you don't need a separate /boot partition. If you did needed it and you didn't have it, your system wouldn't boot.

---

### Post by Evanlec on 2007-11-04
another case of needing a /boot partition is if you're using software RAID
in this case you must have a non-raid /boot partition because the RAID devices 
wont be readable at boot time

---

### Post by carloslosgrande on 2007-11-04
Yes, thanks Epimeteo. I understand that, but still don't understand how [COLOR="Red"]/boot[/COLOR] would save my settings.
So an encrypted partition needs[COLOR="#ff0000"] /boot > /root > /(encrypted) home[/COLOR] in this order for boot sequence to work? 
is that right?
Or is the encryption on [COLOR="#ff0000"]/root[/COLOR]?

---

### Post by ruibernardo on 2007-11-04
> **carloslosgrande said:**
> 
Or is the encryption on [COLOR=#ff0000]/root[/COLOR]?Yes, take a look [here]("http://ubuntuforums.org/showpost.php?p=3601683&postcount=5") to see how it's done (in the fourth picture you can see that only /boot is left unencrypted).

For some other reasons why to have a /boot partition I've found this post, it explains it very well:
> **tmetro said:**
> There are a number of reasons why you might want or need a separate /boot partition, some historical and some still relevant.[LIST]
[*]Boot loader file system limitations
This has already been mentioned above.
[*]Non-bootable file system, like RAID used for root
Similar to the first item. Sometimes if RAID is used for root, /boot will be placed on a separate partition, and optionally mirrored using rsync or other non-RAID method.
[*]Cylinder addressing limits in BIOS or boot loader
This was the primary motivation for a separate boot partition in the past. The BIOS on some machines can't address the cylinders beyond certain thresholds, and some boot loaders have this problem too. The workaround was to put the kernel into a partition at the front of the disk. Some discussion of this in the [wiki]("https://wiki.ubuntu.com/WartyWarthogInstallNotes?highlight=%28%2Fboot%29").
[*]Rescue kernel file system limitation
After a failed kernel upgrade, it'd be nice to be able to access your /boot partition to rename or replace the kernel. To do so, your rescue kernel needs to support the file system. Live CDs, with space to store modules for most file systems, have made this less of an issue.
[*]Extra protection against partition table corruption
The rarely ever accessed /boot partition is less likely to get trashed, though if your root partition gets trashed you still might not be able to do much to fix the system without using a bootable rescue disk. Again, Live CDs make this not much of an advantage.[/LIST]-Tom

About the boot process I've made a resume from "man boot" documentation:
> In PC, the OS Loader is located in the first sector of the boot  device - this is the MBR (Master Boot Record)... but the size limitation of the PC MBR (512 bytes including the partition table) makes it almost  impossible to squeeze a full OS Loader into it... Therefore,  most  operating systems make the primary loader call a secondary OS loader which may be located _on a specified disk partition_. [COLOR=RoyalBlue]<---- /boot: where are the GRUB files and the kernel images.[/COLOR]

When the kernel is  loaded,  it  initializes  the  devices  (via  their drivers), starts  the swapper (it is a "kernel process", called kswapd in modern Linux kernels), and mounts the root file system (/).

Only then the kernel creates the first (user  land)  process  which  is      numbered  1.  This process executes the program /sbin/init, passing any parameters that weren’t handled by the kernel already.

When init starts it reads /etc/inittab for further instructions.   This file defines what should be run in different run-levels.

---

### Post by carloslosgrande on 2007-11-04
[FONT="Comic Sans MS"]Hey Epimeteo, that was just what I was looking for. I understand now.
Much appreciated[/FONT]
[FONT="Comic Sans MS"]Thanks to all who've helped.[/FONT]

---

