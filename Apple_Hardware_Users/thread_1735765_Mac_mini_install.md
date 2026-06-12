---
title: "Mac mini install"
date: 2011-04-21
forum: Apple Hardware Users
---

### Post by kpgalligan on 2011-04-21
I've been wrestling with getting ubuntu on the mac mini for about a week now.  Here's where I'm at:

I've tried the regular install disk for 10.10 (i386 32 bit, as well as the amd64, just in case).  That didn't work.  I also tried the regular disk for 11.04, which also didn't work.  then I tried the alternate disk for 10.10.  That got through the install process.  Here's the config:

Partitions #1 and #2 are mac specific.  #3 is biosgrub (or grubbios?), #4 is 120-ish gigs of ext4, and #5 is a few gigs of swap.

I installed grub at /dev/sda.

When I boot into the machine, I get rEFIt, select the penguin, then get the grub screen, which again lists macosx and ubuntu.  I select ubuntu.  Then I see a cursor and nothing else at the top left for a few seconds, then the screen goes blank.

That's it.

I tried a few "Ctr + F1"'s, and different F's, but nothing else ever came up.

thoughts?  It seems like everybody else installs this without issue.

I'm going to try the alt for 11.04 and see if that goes any better.

---

### Post by kpgalligan on 2011-04-21
11.04 alternate installs as well.  Now I get a little bit more down the startup hole.  In regular boot, it shows some obviously weird display lines, like the W * H is off.  Nothing happens when I click or type, and ctr+F_ does anything.

I rebooted in recovery mode and get:

"Loading Linux 2.6.38-8-generic ..."
"Loading initial ramdisk ..."
"_"

Then the same weird colors below that shortly after.

That's it.  Thoughts?

---

### Post by Alvasin on 2011-04-22
I have successfukky upgraded my powermac g4 to to os 10.2 by using the  emac install disk that purchased from macsales.com. It is possible to  upgrade from another machines install disk.

---

