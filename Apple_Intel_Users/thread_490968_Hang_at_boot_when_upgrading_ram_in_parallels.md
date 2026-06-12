---
title: "Hang at boot when upgrading ram in parallels"
date: 2007-07-03
forum: Apple Intel Users
---

### Post by lotu5 on 2007-07-03
I'm using a MacBook Pro Intel Core Duo 2ghz with 1.5Gigs of ram. 

I installed Ubuntu in parallels with a virtual machine that had 500MB of ram. BUT, I use ubuntu most of the time, so now I want to increase the ram. When I increase the ram above 600MB, ubunt hangs at boot. 

When I boot in rescue mode, I see that there's an error like this:

udevd-event /sbin/modprobe abnormal exit

I tried adding noacpi acpi=off nolacpi noapic irqpoll

but none of those helped. i also tried adding HIGHMEM as a kernel param, but that diesn't help either. 

now that i spent all night trying to fix this, does anyone know what the problem might be?

thanks!

---

### Post by cyberdork33 on 2007-07-03
as far as i know this is a documented problem with parallels

---

### Post by lotu5 on 2007-07-05
I don't think so. The documented problem is with increasing the hard drive size.

---

### Post by cyberdork33 on 2007-07-05
Well.... in that case, let me be more specific. It _is_ a known issue that your RAM may need to be adjusted to get Ubuntu to run in parallels...

Here are a few posts dealing with the "too much RAM" problem.

[http://ubuntuforums.org/showthread.php?t=402512](http://ubuntuforums.org/showthread.php?t=402512)
[http://ubuntuforums.org/showthread.php?t=415827](http://ubuntuforums.org/showthread.php?t=415827)
[http://ubuntuforums.org/showthread.php?t=360038](http://ubuntuforums.org/showthread.php?t=360038)

Here are some in the parallels forum:
[http://forum.parallels.com/showthread.php?t=12600](http://forum.parallels.com/showthread.php?t=12600)
[http://forum.parallels.com/showthread.php?t=3207](http://forum.parallels.com/showthread.php?t=3207)

---

