---
title: "Ubuntu refuses to start. Automatic file system check failed. Manually required."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by PureRumble on 2007-04-04
I was using my computer and I installed a program with Synaptic. When the installation had been completed, the bar at the bottom and the top of the screen just freeze and refuse to respond. I shut down by pressing the power button on the tower quickly so the Quit-windows shows up. Then I choose restart. But it simply refuses to do anything. So now I hold the powerbutton down 5 secs to force a shutdown.

When I start up and choose the Ubuntu-partition, the start-up screen shows up (the one with the bar). When it reaches about 20% it freezes, and then the following text is presented to me


* Checking root file system...
/etc/rcS.d/S20checkroot.sh:407 logsave:not found

* An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed in maintenance mode with the root filesystem mounted in read-only mode


The story goes on. It then tries to start up some commands that obviously fail. I am then presented with a prompt. Running fsck will do no good. It simply states that there is no such command.

I am now running from the liveCD. I managed to run sudo fsck on /dev/hda3 and it fixed something (last time of writing was in th future), and then stated that it was "clean". But this still won't help me out. I am presented with the same problem when I reboot and startup my Ubuntu-partition.

My HD layout

/dev/hda1 FAT32 (compaq-recovery partition)
/dev/hda2 NTFS (my windows XP partition)
/dev/hda3 EXT3 (my linux partition)
/dev/hda4 SWAP (the swap partition)

How can I solve this?

---

### Post by LaurelLynn on 2007-04-04
Dear PureRumble,

I would try booting and picking ¨Recovery Mode¨ from the GRUB menu.

If that didn´t start  I would boot from the Live CD.

Open a terminal Applications->Accessories->Terminal:

sudo fsck  /dev/hda3

At least that´s what Ubuntu is telling you to do. What happens next depends on how much damage the installer did (which depends on where the app came from).

Hope that helps,

Laurel Lynn

---

### Post by PureRumble on 2007-04-04
Thanks for reply. I have done this from the liveCD. I am writing this reply from the liveCD! There was an initial error, but fsck fixed it. Since then, it only says that the partition is clean. I think what it wants me to do is to run this command from the prompt that it presents. The only problem is that I cant! I can't run any command. Even some commands that the system tries to start after the error-message has been presented fail to start.

Does anyone know why I cant atleast write some commands here?

Thanks.

---

### Post by LaurelLynn on 2007-04-05
Dear PureRumble,

It depends on where here is.  If your getting a prompt  ¨#¨ or ¨$¨ the kernel has loaded.

From a ¨#¨ prompt you have root access and any command should run, unless its been erased from the disk. 

At a ¨$¨ prompt you need to type ¨sudo¨ first to have the right permissions.

Most linux commands are actually a filename for some  program in your path. ¨env¨ is a shell command that should list something like:

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11

It´s all those bin entries that you need to run most commands.

Try  ¨/bin/ls /bin¨. If that doesn´t work its a real problem

From the Live CD browse the directories in the path above, if you can´t even read them I hate to say I would reinstall the operating system at that point (WITHOUT erassing the /home partition, better yet back home up to a USB external drive if you have one). Even if you somehow got the system to boot it won´t be stable without the directories above.

Laurel Lynn :(

---

### Post by PureRumble on 2007-04-05
> **LaurelLynn said:**
> Dear PureRumble,

It depends on where here is.  If your getting a prompt  ¨#¨ or ¨$¨ the kernel has loaded.

From a ¨#¨ prompt you have root access and any command should run, unless its been erased from the disk. 

At a ¨$¨ prompt you need to type ¨sudo¨ first to have the right permissions.

Most linux commands are actually a filename for some  program in your path. ¨env¨ is a shell command that should list something like:

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11

It´s all those bin entries that you need to run most commands.

Try  ¨/bin/ls /bin¨. If that doesn´t work its a real problem

From the Live CD browse the directories in the path above, if you can´t even read them I hate to say I would reinstall the operating system at that point (WITHOUT erassing the /home partition, better yet back home up to a USB external drive if you have one). Even if you somehow got the system to boot it won´t be stable without the directories above.

Laurel Lynn :(

Thank you for all your time. I decided to do a full reinstall. You say this now but I have already removed the complete partition.

I have mentioned all of this in a bug-report that I think they might find interesting (files aren't supposed to be there one second and be gone the next now are they? <^_^>). Thanks once again.

---

