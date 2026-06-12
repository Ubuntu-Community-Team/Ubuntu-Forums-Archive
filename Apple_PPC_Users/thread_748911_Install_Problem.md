---
title: "Install Problem"
date: 2008-04-07
forum: Apple PPC Users
---

### Post by gallam on 2008-04-07
I downloaded the 6.06 LTS PPC Live CD version and it ran flawlessly, from the CD, on my IBM RS/6000 7025 F50 (an server made by IBM that uses 4 PowerPC processors).

However, when I went to install it, it runs perfectly until it gets to the point about a boot loader and then says it cannot find a yaboot partition.

What I am doing wrong?  I used the automatic partition scheme and told it to erase the entire disk.  It sets up two partitions (ext3 and swap) but it seems to be looking for a 3rd for yaboot.

Does anyone have any ideas?

Thanks.

---

### Post by stream303 on 2008-04-07
RS6000!  While I can't give you any direct help, I have seen some good info in the Gentoo forums about the RS6000, and even some yaboot configs for Ubuntu as well:

[http://forums.gentoo.org/viewtopic-t-42672-postdays-0-postorder-asc-start-25.html](http://forums.gentoo.org/viewtopic-t-42672-postdays-0-postorder-asc-start-25.html)

If you are willing to venture into unofficial territory, you could also try Feisty 7.04 here, and I'm wondering if the "alternate" image would be best for that machine, rather than the live-cd desktop images.

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

You can navigate this ports directory to obtain newer or older unofficial releases, and even try the latest Hardy-Beta if you feel so inclined.

[http://cdimage.ubuntu.com/ports/daily/](http://cdimage.ubuntu.com/ports/daily/)

I'd love to see an RS6000 running Ubuntu and would love to see the yaboot.conf for it myself!

btw, don't feel bad - many of us ppc'ers end up manually editing our yaboot.conf, especially the device line after digging around in Openfirmware and whatnot.  I wish I had an rs6000 to work on right now...

---

### Post by stream303 on 2008-04-07
Aha.  Now THIS is good:

[http://jrichards.org/blog/?c=linux](http://jrichards.org/blog/?c=linux)

Could it be as simple as the line in your yaboot.conf that reads

```
root=/dev/sda2
```

should in actuality be:

```
root=/dev/sda3
```

then follow up with a 
```

mkofboot -v -C /etc/yaboot.conf
then
ybin -v -C /etc/yaboot.conf
```

From that link, it appears that the standard partitioning layout for an RS6000 when you "use the whole disk" is:
1 - Prep Boot partition
2-  Swap partition
3 - Root partition

reboot!  Crossing fingers....

---

### Post by gtppc on 2008-05-10
I'm a newbie to linux. 

I have used the live cd ubuntu ppc 8.04 to try to install on my G4 powerbook.

It partitions and installs until the last part to do with Yaboot. The message is 'Failed to install bootloader'. This is at about 97% of the install process...

Appreciate any help.

Thank you

gtppc

---

