---
title: "Dual Boot Ubuntu and openSUSE"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Yuki_Nagato on 2008-02-22
I know this must have been rehashed how many times already, but I cannot get a dual boot of Ubuntu 7.1 and openSUSE 10.3 to share the same /home partition.  What I am asking for is a comprehensive overview of what partitions I should set up when installing Ubuntu, and then afterwards when installing openSUSE.  I looked around on Google, all I found was a guide on how to share the /home directory between Debian Etch and Mandrivia.

I have tried something similar to using the Ubuntu install partition editor:

PRIMARY ext3 /
LOGICAL ext3 /home
LOGICAL swap
unallocated space (supposedly for openSUSE later)

However, when install finishes, I end up with two mounted volumes, (/target and /target/home) and attempting to run Ubuntu off of the hard drive produces an Error 15 on the GRUB loader, Stage 1.5.

---

### Post by kooolrock on 2008-02-22
> **Yuki_Nagato said:**
> I know this must have been rehashed how many times already, but I cannot get a dual boot of Ubuntu 7.1 and openSUSE 10.3 to share the same /home partition.  What I am asking for is a comprehensive overview of what partitions I should set up when installing Ubuntu, and then afterwards when installing openSUSE.  I looked around on Google, all I found was a guide on how to share the /home directory between Debian Etch and Mandrivia.

I have tried something similar to using the Ubuntu install partition editor:

PRIMARY ext3 /
LOGICAL ext3 /home
LOGICAL swap
unallocated space (supposedly for openSUSE later)

However, when install finishes, I end up with two mounted volumes, (/target and /target/home) and attempting to run Ubuntu off of the hard drive produces an Error 15 on the GRUB loader, Stage 1.5.
i hv a friend who tried out Open suse. He was fed up of it, esp. b'coz of lack of proper graphics for his nvidia card. i gave him a ubuntu cd and asked him to try it out. He loved it!!!:) He's happy now. i feel ubuntu is more than sufficient.

---

### Post by sandysandy on 2008-02-22
here&#347; a nice link to grub errors

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

it gives following info about error15

[COLOR="Blue"]15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. [/COLOR]

regards

---

### Post by Forrest Gumpp on 2008-02-22
You may care to have a look at how Herman installs multiple distros and different releases of the same distro at his Illustrated Dual Boot Site:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This is quite an extensive site and an excellent general reference.  The specific reference for your proposal is:  [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)  

The reference is headed "Windows and Linux Multiple Boot Arrangements", and is well down the page according to the scroll bar indicator (near the bottom in fact).

---

