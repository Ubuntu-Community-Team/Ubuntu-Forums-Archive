---
title: "ubuntu 9.04 jaunty doesn't boot anymore on MacBook Pro 3,1"
date: 2009-07-06
forum: Apple Hardware Users
---

### Post by bertvv on 2009-07-06
Hi all,

I'm running Ubuntu on my MacBook Pro 3,1 for almost two years (since Hardy). It's been a great experience, with the installation of Jaunty being the smoothest of the three releases I've installed. Until the beginning of this month. After installing updates (a.o. Linux kernel 2.6.28-13-generic) on July 1st, Jaunty refuses to boot. At first, the boot process halted after showing "GRUB _". After a lot of trying to fix it, I'm not even getting there anymore. Now the boot process hangs at the penguin or the message "Missing Operating System". 

I've installed rEFIt 0.13 and MacOS X (Tiger) is fully updated. When powering up, I get the choice between MacOS and Linux, as expected. Booting MacOS or an Ubuntu (or other) Live CD still works. In attachment, I've added the report of rEFIt's Partition Inspector.

[LIST]
[*] GPT partition 5 or /dev/sda5 is my Linux root filesystem
[*] GPT partition 3 or /dev/sda3 is mounted as /home
[/LIST]

There's quite a few forum posts on similar problems (e.g. [http://ubuntuforums.org/showthread.php?t=767677]("http://ubuntuforums.org/showthread.php?t=767677")), and I guess I just about read them all. I already tried the following:

[LIST]
[*] syncing GPT and MBR tables: "No need to sync"
[*] upgrading rEFIt (before the boot problem, I still had 0.11)
[*] reinstalling Grub on my Linux root filesystem, (hd0,4) in my case: still "Missing Operating System" (see [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11]("http://ubuntuforums.org/showpost.php?p=3303463&postcount=11"))
[*] verifying that the Linux partition has the correct boot code and that the MBR *doesn't*: see report, all correct.
[*] reinstalling Jaunty (I lost count by now): no change
[*] formatting /dev/sda5 with a different block size: no change (see [http://www.linuxplanet.com/linuxplanet/tutorials/6480/1/]("http://www.linuxplanet.com/linuxplanet/tutorials/6480/1/"))
[*] starting up while pressing the option key and selecting "Windows": "Missing Operating System"
[*] powering down and restarting several times, as is suggested in some of the threads on this issue: doesn't help
[*] installing Ubuntu Karmic alpha (for Grub2 and ext4): installer crashes while setting up Grub
[*] installing Fedora 11 and OpenSolaris (yes, I was that desperate): doesn't work
[/LIST]

Well, I'm out of options. Anyone?

Best regards,

bert

---

