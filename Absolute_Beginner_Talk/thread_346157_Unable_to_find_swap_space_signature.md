---
title: "Unable to find swap space signature"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-01-25
I see when I boot "Unable to find swap space signature."  I searched the forums and I did see quite a few times where people asked about this, but I wanted to ask and post the same information they did, in case the solution is different based on different computers.

sudo fdisk - l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         564        5201    37254735    7  HPFS/NTFS
/dev/hda2               1         563     4522266    b  W95 FAT32
/dev/hda3            5202       11875    53608905   83  Linux
/dev/hda4           11876       12161     2297295    5  Extended
/dev/hda5           11876       12161     2297263+  82  Linux swap / Solaris

Partition table entries are not in disk order





--------------------------------------------------------------------------


sudo gedit /etc/fstab



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=865718b7-222f-4889-95f5-f54037cff7e5 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=4ffab9bc-690c-435f-8353-5dbf0bb1352f none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



Thanks

---

### Post by kidders on 2007-01-25
Hi there,

Is your swap space formatted?
What solution did you find elsewhere?
Does your swap actually mount for you?

---

### Post by brandoncolorado on 2007-01-25
Hello,

My swap space is formatted, or at least I think so.  I think it is HDA5, and I asked ubuntu to set it up when I first installed Ubuntu.  This is a similar thread that I was looking at, but they said that mkswap is a dangerous command.  I think this problem may be what is causing my computer to hang on hibernate maybe too.

[http://ubuntuforums.org/showthread.php?t=307009&highlight=Unable+to+find+swap+space+signature](http://ubuntuforums.org/showthread.php?t=307009&highlight=Unable+to+find+swap+space+signature)

---

### Post by kidders on 2007-01-25
Ahh... I took a quick (very quick!) look at that other post. It seems as though something like this might've happened:

[LIST=1]
[*]You ran into hibernate-related trouble, so you fixed it by (in part) reformatting your swap space to get rid of the RAM image stored in it.
[*]This changed (obviously) the UUID of the swap filesystem.
[*]Now /etc/fstab's reference to the old UUID isn't valid any more.
[/LIST]

If you find yourself reformatting swap every now and then, you should probably switch the reference to it in /etc/fstab to a "/dev/hda..."-style path, rather than using its UUID. You'll be trading Ubuntu's ability to spot your swap space moving around on your IDE bus for the ability to format your swap on a whim, without having to remember to update /etc/fstab.

Just to be safe, I'd mkswap (format) the swap space first, tweak /etc/fstab so it really does point to the right place (either by /dev path or by UUID), and then test your swap (with swapon) to make sure it works without having reboot. That should sort you out.

**Edit:** mkswap isn't particularly dangerous (granted, of course, unless you point it at the wrong partition!) ... it just formats swap space, just as mkreiserfs formats ReiserFS, or mke2fs formats Ext2/3.

---

### Post by steve.horsley on 2007-01-25
Good idea kidders. You are quite possibly right. Let's tell him the fix too.

Edit the /etc/fstab file with this command:
**gksu gedit /etc/fstab**
find these lines:
> # /dev/hda5 -- converted during upgrade to edgy
UUID=4ffab9bc-690c-435f-8353-5dbf0bb1352f none swap sw 0 0
and replace them with this line:
> /dev/hda5 none swap sw 0 0

I am beginning to think that UUID stuff was a bad mistake.

---

### Post by kidders on 2007-01-25
> **steve.horsley said:**
> I am beginning to think that UUID stuff was a bad mistake.Can be tremendously handy though!

> **steve.horsley said:**
> Let's tell him the fix too.Lol yes... How did I manage to be so long-winded and manage *not* to explain what I was talking about?! Oops.

---

### Post by brandoncolorado on 2007-01-25
> **kidders said:**
> Ahh... I took a quick (very quick!) look at that other post. It seems as though something like this might've happened:

[LIST=1]
[*]You ran into hibernate-related trouble, so you fixed it by (in part) reformatting your swap space to get rid of the RAM image stored in it.
[*]This changed (obviously) the UUID of the swap filesystem.
[*]Now /etc/fstab's reference to the old UUID isn't valid any more.
[/LIST]

If you find yourself reformatting swap every now and then, you should probably switch the reference to it in /etc/fstab to a "/dev/hda..."-style path, rather than using its UUID. You'll be trading Ubuntu's ability to spot your swap space moving around on your IDE bus for the ability to format your swap on a whim, without having to remember to update /etc/fstab.

Just to be safe, I'd mkswap (format) the swap space first, tweak /etc/fstab so it really does point to the right place (either by /dev path or by UUID), and then test your swap (with swapon) to make sure it works without having reboot. That should sort you out.

**Edit:** mkswap isn't particularly dangerous (granted, of course, unless you point it at the wrong partition!) ... it just formats swap space, just as mkreiserfs formats ReiserFS, or mke2fs formats Ext2/3.


Thanks for the help.  I haven't tried to fix the hibernating thing before, I just lived with it.  I just brought it up because I saw it in a few of the other threads, and connected it to this problem.  So, just to sum up what I should be doing....

1) sudo gedit /etc/fstab
2)edit the fstab to say /dev/hda5
3)sudo mkswap /dev/hda5
4)Restart
5)sudo swapon

Is this right?

Thanks again

---

### Post by kidders on 2007-01-25
More or less...

Leave out step 4 and change step 5 to **sudo swapon /dev/hda5**

or

Leave out step 5.

**Edit:** But do bear in mind that using your swap's /dev path instead of its UUID will mean your swap will break again if you rearrange your hard disks on your IDE bus.

---

### Post by brandoncolorado on 2007-01-25
> **kidders said:**
> More or less...

Leave out step 4 and change step 5 to **sudo swapon /dev/hda5**

or

Leave out step 5.

**Edit:** But do bear in mind that using your swap's /dev path instead of its UUID will mean your swap will break again if you rearrange your hard disks on your IDE bus.

> **kidders said:**
> Can be tremendously handy though!

Lol yes... How did I manage to be so long-winded and managed *not* to explain what I was talking about?! Oops.



Thanks for all of the help.  This is what I get now, so I think it worked.

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         564        5201    37254735    7  HPFS/NTFS
/dev/hda2               1         563     4522266    b  W95 FAT32
/dev/hda3            5202       11875    53608905   83  Linux
/dev/hda4           11876       12161     2297295    5  Extended
/dev/hda5           11876       12161     2297263+  82  Linux swap / Solaris

---

### Post by kidders on 2007-01-25
Your partition layout shouldn't have changed ... at least I **hope** it hasn't!!

You should however notice that you have swap now. If not, be sure to post back!

---

### Post by brandoncolorado on 2007-01-25
> **kidders said:**
> Your partition layout shouldn't have changed ... at least I **hope** it hasn't!!

You should however notice that you have swap now. If not, be sure to post back!

I think it worked

free -m
             total       used       free     shared    buffers     cached
Mem:           947        371        575          0         10        195
-/+ buffers/cache:        166        780
Swap:         2243          0       2243

---

### Post by kidders on 2007-01-25
Looks good! :-)

---

### Post by mlissner on 2007-01-27
Just did these instructions here as well. Worked like a charm, thanks.

---

### Post by brandoncolorado on 2007-02-09
Looks like it is gone now again.  Is there any reason why the swap space would keep going bad/disappearing?

---

### Post by kidders on 2007-02-09
It shouldn't really vanish all by itself ... are you sure you didn't do something odd?

Here are some things to check:

[LIST]
[*]Does the swap partition mentioned in /etc/fstab still exist?
[*]Are you sharing Ubuntu's swap with another operating system?
[*]Are you sure the swap really isn't mounted?
[*]If not, what happens when you try to mount it?
[*]Does reformatting it make any difference?
[*]Are you having trouble with hibernating?
[/LIST]

---

### Post by brandoncolorado on 2007-02-11
> **kidders said:**
> It shouldn't really vanish all by itself ... are you sure you didn't do something odd?

Here are some things to check:

[LIST]
[*]Does the swap partition mentioned in /etc/fstab still exist?
[*]Are you sharing Ubuntu's swap with another operating system?
[*]Are you sure the swap really isn't mounted?
[*]If not, what happens when you try to mount it?
[*]Does reformatting it make any difference?
[*]Are you having trouble with hibernating?
[/LIST]

Here is the fstab printout:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=865718b7-222f-4889-95f5-f54037cff7e5 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

* I am running Ubuntu alongside Windows XP, so there shouldn't be other OS's using the swap.

*I have tried reformatting it and mounting it, and it works temporarily.  

*I am having trouble while hibernating.  On battery, when I close the lid on my laptop, it won't come off black screen when I open it back up so I have to hard restart.

---

### Post by d3mia7 on 2007-02-12
> **kidders said:**
> It shouldn't really vanish all by itself ... are you sure you didn't do something odd?

Here are some things to check:

[LIST]
[*]Does the swap partition mentioned in /etc/fstab still exist?
[*]Are you sharing Ubuntu's swap with another operating system?
[*]Are you sure the swap really isn't mounted?
[*]If not, what happens when you try to mount it?
[*]Does reformatting it make any difference?
[*]Are you having trouble with hibernating?
[/LIST]

I'm going through the same thing right now... I've got a Compac nc6220 which used to hibernate fine under Dapper... after upgrading to Edgy things were fine UNTIL I tried to hibernate my laptop.  Post-hibernation no more swap.  

I've gone through now and reproduced it repeatedly - run mkswap, doing a swapon -a (which also proves /etc/fstab is set up correctly) and then hibernating.  When I resume my swap partition is not recognized PLUS resume from hibernate doesn't work.

Hibernate writes the contents of RAM to the swap partition so it makes sense that this would be hibernation-related.  I'm guessing the OP is having the same problem...

---

### Post by kidders on 2007-02-12
> **brandoncolorado said:**
> I am having trouble while hibernating.  On battery, when I close the lid on my laptop, it won't come off black screen when I open it back up so I have to hard restart.Annoying. Whenever that happens, one of the steps involved in the recovery is reformatting your swap, afaik. :-(

---

### Post by kidders on 2007-02-12
> **d3mia7 said:**
> Hibernate writes the contents of RAM to the swap partition so it makes sense that this would be hibernation-related.Yep, that's right. I'd say your suspicion about brandoncolorado's problem is correct.

---

### Post by brandoncolorado on 2007-02-12
> **d3mia7 said:**
> I'm going through the same thing right now... I've got a Compac nc6220 which used to hibernate fine under Dapper... after upgrading to Edgy things were fine UNTIL I tried to hibernate my laptop.  Post-hibernation no more swap.  

I've gone through now and reproduced it repeatedly - run mkswap, doing a swapon -a (which also proves /etc/fstab is set up correctly) and then hibernating.  When I resume my swap partition is not recognized PLUS resume from hibernate doesn't work.

Hibernate writes the contents of RAM to the swap partition so it makes sense that this would be hibernation-related.  I'm guessing the OP is having the same problem...

That sounds about right :(.  Am I missing out on any other functionality/speed other than hibernate without a swap?

---

### Post by kidders on 2007-02-12
> **brandoncolorado said:**
> Am I missing out on any other functionality/speed other than hibernate without a swap?If you don't use any virtual memory, your OS will become slow and unstable, especially when you push it. If you have a lot of RAM, the effect won't be as severe though.

---

### Post by ltk5 on 2007-03-01
True! I tried that, when Firefox crashed because of Flash. I waited for more than five minutes, before I noticed, there's nothing I could do. The next time, I rebooted, I saw there's no swap.

Uhm, what happens, if you share the swap with some other linux distro?

---

### Post by kidders on 2007-03-02
In practice, doing that can often be okay, but you *could* encounter weird behaviour. If I were going to do that, I would alter my startup sequences so both distros reformatted the shared swap at every boot. Doing that would prevent you hibernating either OS though.

Tbh, just as you wouldn't expect Win98 and WinXP to share the same virtual memory, it's not advisable to expect two Linuxes to do so.

---

### Post by mcduck on 2007-03-02
> **kidders said:**
> In practice, doing that can often be okay, but you *could* encounter weird behaviour. If I were going to do that, I would alter my startup sequences so both distros reformatted the shared swap at every boot. Doing that would prevent you hibernating either OS though.

Tbh, just as you wouldn't expect Win98 and WinXP to share the same virtual memory, it's not advisable to expect two Linuxes to do so.

If you don't use hibernate, there is no reason why you couldn't share the same swap between all your Linux installs. (Booting another Linux distro while the first one has stored it's RAM data into swap will of course cause problems).

Anyway, if hibernating doesn't work for you, why not just disable it completely?

---

### Post by ltk5 on 2007-03-03
hm, how to do that?

---

### Post by NickeNyfiken on 2007-04-09
> **brandoncolorado said:**
> Thanks for all of the help.  This is what I get now, so I think it worked.

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         564        5201    37254735    7  HPFS/NTFS
/dev/hda2               1         563     4522266    b  W95 FAT32
/dev/hda3            5202       11875    53608905   83  Linux
/dev/hda4           11876       12161     2297295    5  Extended
/dev/hda5           11876       12161     2297263+  82  Linux swap / Solaris


Instead of running "sudo fdisk -l" to list the partition table, run "cat /proc/swaps". That will show you the information you want to have. Namely, what devices are you using as swap right now? The above information only tells you that you have a device with system type "Linux Swap".

---

### Post by arjanm on 2008-02-03
When hibernate causes the swap partition to become invalid, the reference to the partition in
/etc/initramfs-tools/conf.d/resume might be wrong. There the UUID is also used (you can use /dev/xxx if you want).

The reason is that upon hibernate the swap is replaced by a hibernate file. When starting the PC again, the resume= contained an invalid UUID, causing hibernate not to work and forcing a normal startup. But since the hibernate file was still on the swap partition, the swap partition signature was invalid. Even reformatting the swap partition worked temporarily, until the next hibernate.

In my case, to get hibernate and swap working again I had to:

(replace XXX by your swap partition, for instance /dev/sda4)

1. Format the swap partition again: **sudo mkswap /dev/XXX**
2. Activate swap partition **sudo swapon /dev/XXX**
3. Replace UUID=XXX in /etc/initramfs-tools/conf.d/resume by "resume=/dev/XXX"
4. Regenerate the initrd: **sudo mkinitramfs -o /boot/initrd.img-2.6.XX** (same version as the kernel)

---

### Post by merike on 2008-03-06
I have also issues with "unable to find swap-space signature".
I have tried to:
[LIST=1]
[*]reformat swap with mkswap
[*]swapon
[*]change fstab to find swap using /dev/sdax
[*]change resume file to also have /dev/sdax
[*]update-initramfs
[*]reboot
[/LIST]
In my case it didn't work. It still shows 0 swap space using "free".
In addition when I run mkswap and swapon before hibernate then after resuming my desktop isn't like I left it. For example Firefox window is gone and comes back asking if I wan't to continue with my previous session. It's been strange for some time now, so I'm not completely sure any more, but shouldn't all the windows come back just as I left them?

---

### Post by oliver69 on 2008-03-19
Thanks arjanm!!  Your solution in #27 worked perfectly for me. :)

Here the problem was caused by a freeze-while-hibernating of an older Ubuntu, which is still installed on the same harddisk. This corrupted my (shared) swap partition, it got reformatted and UUID changed. Especially on laptops I like your solution for swap and resume much more than the one with a UUID!

---

