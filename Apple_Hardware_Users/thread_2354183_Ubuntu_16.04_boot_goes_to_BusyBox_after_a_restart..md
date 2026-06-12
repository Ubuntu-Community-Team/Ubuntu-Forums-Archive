---
title: "Ubuntu 16.04 boot goes to BusyBox after a restart."
date: 2017-02-28
forum: Apple Hardware Users
---

### Post by vegarab on 2017-02-28
Hi.
Ive had Ubuntu 16.04 running on my machine for some months. Last week I had some troubles with bootloaders, since I am running Windows 10, OS X and Ubuntu 16.04 on a MacBook with 11.1 drivers.

Today I just restarted Ubuntu, because I couldnt find any applications by launching from Dock, Launcher or Terminal and downloads from Firefox said the disk was write-protected?? - during the shutdown the screen teared (upperhalf and lowerhalf of screen was not synced) and froze there for a minutes before I had to force a shutdown by holding down the power-button.

Now, when booting it goes straight to BusyBox after I choose Ubuntu in Grub2.
I am left at the ([COLOR=#333333][FONT=Lucida Grande]initramfs[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande])[/FONT][/COLOR]BusyBox terminal. What now? I have a boot-repair disk. Should that do the trick, or will it bork my current boot-setup (reFind installed on OSX, when I boot Ubuntu I can let reFind boot kernel etc., or go to Grub - in this case both give same result).

---

### Post by vegarab on 2017-02-28
[COLOR=#CCCCCC][FONT=Helvetica Neue][COLOR=#000000]I managed to monitor what happens during boot.[/COLOR]
[COLOR=#000000] [/COLOR]
[COLOR=#000000]It says my Linux partition sda4 is a filesystem with errors. It runs fsck, but it ends with exit code4, and then tells me the partition needs a MANUAL fsck. Is it as simple as booting a live-disk and running fsck, or would there be more to do? [/COLOR]
[/FONT][/COLOR]

---

### Post by vegarab on 2017-02-28
Fixed by running
sudo fsck.ext4 -v /dev/sda4
from liveCD

---

### Post by ajgreeny on 2017-02-28
Great news! Just what I, and no doubt others would have told you to do.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

