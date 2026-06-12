---
title: "Grub error, no such partition?"
date: 2011-07-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by TheCurator on 2011-07-19
Hi, I bought an Asus K53SJ last week and installed an Ubuntu partition yesterday. For some reason this caused my AKT0100 driver to screw up and P4G stopped working. To try to fix this I restored the windows 7 factory defaults using the recovery partition, only replacing the windows partition, keeping the ubuntu partition. When I did this, the 'windows' option on the boot screen failed to initialise windows so I thought I'd just reset the whole thing and try installing ubuntu later. So I did a recovery partition of the whole HD, including the ubuntu partition. Now when I start my computer I get the message:
error: no such partition
grub rescue>

I tried restoring the windows bootloader according to this: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708), by downloading a win 7 recovery disc, but the DVD (it's a DVD-RW if that's at all significant) won't boot when I start up the computer. Any help would be greatly appreciated.

---

### Post by sumith_p on 2011-07-19
I had this same msg when i deleted one of my ubuntu partitions....i couldnt do anything....finally saved my important data using ubuntu live cd and then installed ubuntu again.....

---

### Post by toor58 on 2011-07-19
Follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

This works. I have used it.

---

### Post by raja.genupula on 2011-07-19
[http://ubuntuforums.org/showthread.php?t=1807508](http://ubuntuforums.org/showthread.php?t=1807508)

---

### Post by TheCurator on 2011-07-20
Hi guys, I've reinstalled Ubuntu and this seems to have fixed the issue (I was planning on installing it later on anyway). Thanks for you help.
Quick question: Even though I had restored my laptop to factory state and removed all partitions prior to reinstalling ubuntu, would the previous ubuntu installation have left anything on my laptop that might slow it down or be a problem in the future? I'm wondering because the MBR kept ubuntus changes even after ubuntu was uninstalled, might there be other changes like this have been left that need to be fixed?

---

### Post by raja.genupula on 2011-07-20
that old install will not make you any problem.

---

