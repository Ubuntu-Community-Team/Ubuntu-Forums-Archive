---
title: "kernel panic on boot after Gutsy kernel-update"
date: 2008-03-11
forum: Apple Intel Users
---

### Post by usnmustanger on 2008-03-11
So about three or four weeks ago, I used Synaptic (or autoupdater--can't remember) to update everything, including the kernel.  I then rebooted, and ran into the following error:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0).
I then rebooted into OS X (this is an iMac), since I was going away for a few weeks (Navy), and my wife only uses OS X.
So now I'm back, and I've had time to troubleshoot.  I've googled and searched these forums, and I understand that it has something to do with the kernel looking to boot from the wrong partition (Linux is on the second partition of my HD, Leopard is on the first), and initrd.  But that's the extent of my knowledge.  I found a recommended solution in [this thread]("http://ubuntuforums.org/showthread.php?p=339858&highlight=kernel+panic#post339858"), but I have absolutely no idea how to implement it.
The only options in the grub menu are for the same kernel (one for normal use, one for recovery), so I can't boot into Linux at all.
Can someone please tell me how I can non-destructively repair this problem on my dual-boot iMac?
Many TIA!!!

---

### Post by cyberdork33 on 2008-03-11
Do you get the same problem when you boot the recovery mode?

if not, you will likely need to boot from a LiveCD and mount your Ubuntu partition, and repair the menu.lst file to point to the correct partition.

---

### Post by usnmustanger on 2008-03-12
**This post could be related to an Ubuntu bug filed at**: usnmustanger [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes, the recovery kernel does the same thing.
I've got some questions about what you recommend, and I apologize in advance for my apparent newbie-ness.
Once I boot into the LiveCD and fire up the terminal, are there any switches or options that I need to use with the "mount" command?
How do I know what partition to pass to the mount command?
How do I know what to enter into the menu.lst file?
Where is the menu.lst file?

This doesn't sound too difficult for me, as I'm actually no newbie to Linux or the CLI, I've just never run into this problem before, and I'm not too familiar with GRUB, as I cut my Linux teeth on LILO.

Again, TIA!

---

### Post by cyberdork33 on 2008-03-12
> **usnmustanger said:**
> Yes, the recovery kernel does the same thing.
I've got some questions about what you recommend, and I apologize in advance for my apparent newbie-ness.
Once I boot into the LiveCD and fire up the terminal, are there any switches or options that I need to use with the "mount" command?
How do I know what partition to pass to the mount command?
How do I know what to enter into the menu.lst file?
Where is the menu.lst file?

This doesn't sound too difficult for me, as I'm actually no newbie to Linux or the CLI, I've just never run into this problem before, and I'm not too familiar with GRUB, as I cut my Linux teeth on LILO.
well you can use lilo if you prefer too.

I don't think there are any needed options for mount. I do not know what partition you need to mount, it is whatever partition is your root partition. You can look at the partition layout in gparted on the live cd, then you should be able to determine which is your root partition.

The menu.lst is in /boot/grub/menu.lst. The configuration for the file is quite logical once you find the kernel stanzas. I don't know how things got messed up though, so once you get it working, you might have to make some additional edits to make sure that future updates don't break it also.

---

### Post by usnmustanger on 2008-03-14
**This post could be related to an Ubuntu bug filed at**: usnmustanger [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: usnmustanger [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks so much for the helpful replies.  I will try to fix this tonight when I get home, and post the results.
Thanks again!

---

