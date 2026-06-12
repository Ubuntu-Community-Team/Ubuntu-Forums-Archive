---
title: "command to boot from cd on macintosh powerbook g3"
date: 2006-10-16
forum: Apple PPC Users
---

### Post by jaradronald on 2006-10-16
I'm trying to boot a Mac Powerbook G3 Laptop from the CD-ROM (downloaded & burnt the 6.06 Mac Distro). I can't get the darned thing to give me any boot options... I've read the documentation on the distro cd and googled the issue, but none of the following tell my system to boot from cd:

hold c before boot (post)
use Cmd-Opt-Shtf-Del to start Open Firmware
use Cmd-Opt-o-f to start Open Firmware

Here are my system specs:
G3 Processor
266 Mhz
128 MBs RAM
10 GB Hard Drive
Mac OS 9.2

There is lots of discussion as to "Old World" and "New World" Macs, but I'm not entirely sure what world mine comes from... :-p  I don't know if I need to install grub, or how to even tell what boot loader I have...

---

### Post by Steffen VN on 2006-10-16
Just to be clear, you have one of the "Old World ROM" Powerbooks.  Your machine is one of the ones commonly referred to as "Wallstreet," it was the last model with the "Old World ROM," which makes life tougher for installing Ubuntu.  It's managable, just be sure to refine your searches to installation on a Wallstreet/Old World machine...you cannot simply boot from the CD by holding down the C key as you might be able do with a newer machine.  Hope this helps.

---

### Post by madman91 on 2006-12-09
BUMP

I too have a powerbook g3 lappy and can't boot it. Do I install grub on it? Do I open up open firmware and do some command line magic?

And I am a mac noob, so please noobify it :D

Thanks,
Greg

---

### Post by jaradronald on 2006-12-09
You need to load OS 9.2 on (base installation) and then use the BootX Tool to load your Kernel off of the OS 9 partition.  The instructions are here:

[  http://help.ubuntu.com/community/Installation/OldWorldMacs]("http://penguinppc.org/historical/benh/")

You can download BootX Under OS 9.2 here:
[http://penguinppc.org/historical/benh/](http://penguinppc.org/historical/benh/)

These two links should get you started.  I'm running Ubuntu 6.10 on my Powerbook G3 (I did a base install first without the GUI, then added the "ubuntu-desktop" package using apt-get).

What size hard drive do you have, and how much RAM does your Powerbook have?

---

### Post by madman91 on 2006-12-10
> **jaradronald said:**
> You need to load OS 9.2 on (base installation) and then use the BootX Tool to load your Kernel off of the OS 9 partition.  The instructions are here:

[  http://help.ubuntu.com/community/Installation/OldWorldMacs]("http://penguinppc.org/historical/benh/")

You can download BootX Under OS 9.2 here:
[http://penguinppc.org/historical/benh/](http://penguinppc.org/historical/benh/)

These two links should get you started.  I'm running Ubuntu 6.10 on my Powerbook G3 (I did a base install first without the GUI, then added the "ubuntu-desktop" package using apt-get).

What size hard drive do you have, and how much RAM does your Powerbook have?

I read the installation instructions and have concluded that it is too much of a hassle for too little of a gain. And by the way, your URL is messed up. Both lead to [http://penguinppc.org/historical/benh/](http://penguinppc.org/historical/benh/)  but only one is supposed to.

:D
Thanks for the help

---

### Post by binaryspiral on 2006-12-18
I've got a Macintosh PowerBook G3 with semi transparent keyboard with White lettering (and orange/brown sub lettering).

I held down C after it restarted but before it played the start-up tune. And booted from the liveCD.

So far, it's still loading...

Oh, sound works... it played the cool boot sound.

It's also installing - woo hoo!


I have an eerie feeling I'll be back seaching the forums... but so far, so good! :o

---

