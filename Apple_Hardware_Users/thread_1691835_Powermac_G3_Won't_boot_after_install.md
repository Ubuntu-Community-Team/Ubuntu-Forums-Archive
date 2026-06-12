---
title: "Powermac G3 Won't boot after install"
date: 2011-02-20
forum: Apple Hardware Users
---

### Post by max1zzz on 2011-02-20
So i am trying to turn my old b/w G3 into a large file server, i chose ubuntu over osx because i can use standerd pc sata cards, i can boot the cd, install, but when i reboot one of two things happen:

With a non-apple hdd: nothing at all, just goes to the flashing folder

With a apple hdd: goes to a screen titled "first stage ubuntu bootstrap" either waiting or pressing l prompts "loading second stage ubuntu bootstrap" at which time the flashing folder appears in the middle of the screen and it all starts over again

Any help would be greatly appreciated

Thanks in Advance

---

### Post by linuxopjemac on 2011-02-20
I recommend Debian Squeeze on this particular machine. If you insist on Ubuntu there is something you need to know:
[http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0](http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0)

I don't have the patch for recent versions of Ubuntu. You'd have to recompile your own Ubuntu kernel with cmd64x built in. So again, go for Debian Squeeze. It will boot, as I heard people of installing Squeeze successfully on this machine.

It shows how bad support for PowerPC really is on Ubuntu. This bug has been known for several years. NOTHING was done to this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131)

---

### Post by max1zzz on 2011-02-20
> **linuxopjemac said:**
> I recommend Debian Squeeze on this particular machine. If you insist on Ubuntu there is something you need to know:
[http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0](http://mac.linux.be/content/installation-karmic-koala-when-hard-disk-not-recognised-g3-bw-0)

I don't have the patch for recent versions of Ubuntu. You'd have to recompile your own Ubuntu kernel with cmd64x built in. So again, go for Debian Squeeze. It will boot, as I heard people of installing Squeeze successfully on this machine.

It shows how bad support for PowerPC really is on Ubuntu. This bug has been known for several years. NOTHING was done to this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131)
will Debian squeeze work with this? [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

---

### Post by linuxopjemac on 2011-02-20
I can't guarantee but as Ubuntu is based on Debian it is probably very similar.

---

### Post by max1zzz on 2011-02-21
Thanks linuxopjemac that guide git it :-)

Now running ubuntu 10.04 on my PM G3

---

### Post by linuxopjemac on 2011-02-21
great!!

---

### Post by max1zzz on 2011-02-21
> **linuxopjemac said:**
> great!!
Not so fast, new problem now, was all working then i updated it, now it starts booting then prompts:
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/hdc3 does not exist. Dropping to a shell!

Now im no linux expert, but it looks to me as if it has lost the driver so can't access the hdd, is that right?

---

### Post by max1zzz on 2011-02-21
Ok found a workaround for now, typing "old" on the second stage ubuntu bootstrap screen (and thus loading the old intrid.img) allows it to boot normally, an i right in thinking i could edit yaboot.conf to boot the old intrid.img by default

---

### Post by linuxopjemac on 2011-02-22
you can, be sure to update the bootlaoder with ybin

---

