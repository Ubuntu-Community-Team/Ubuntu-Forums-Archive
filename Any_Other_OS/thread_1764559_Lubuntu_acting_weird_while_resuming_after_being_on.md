---
title: "Lubuntu acting weird while resuming after being on hibernation"
date: 2011-05-21
forum: Any Other OS
---

### Post by ia4004 on 2011-05-21
Hi, I've been having this issue, put my netbook on hibernation, then, when I resume it, the screen goes black, then, a part of the desktop at the right is shown, also lines and dots from various colors appears on the other part of the screen, it has a black background.

---

### Post by azupan on 2011-05-22
Try this:

$sudo apt-get install hibernate

---

### Post by ia4004 on 2011-05-22
Thanks the problem got solved :) , I was getting worried about it

---

### Post by ia4004 on 2011-05-23
I did it, but the issue still there, worked by just one hibernation cycle, then did the same. I don't know what's wrong, because everything is on its place, I mean the programs, updates.

---

### Post by azupan on 2011-05-24
> **ia4004 said:**
> I did it, but the issue still there, worked by just one hibernation cycle, then did the same. I don't know what's wrong, because everything is on its place, I mean the programs, updates.Ummm... ideed. Well, back to the ol'cursing, tinkering & googling. Once I've figured something out, I'll let you know.

**EDIT:**

... OK, I'm back. I tinkered around swap partition a little bit. The system went in and out of hibernation once. In the next attempt, it refused to hibernate. I checked /proc/swaps and discovered, that Natty, in all its wisdom, somehow assigned its swap partition to the partition where Mint is installed :shock::mad: I just hope the Mint installation is still intact.

I got enough of this ****, I'm using Mint from now on. Hopefully 11.10 turns out more stable.

Check this thread, maybe you'll find something useful there

[http://ubuntuforums.org/showthread.php?t=1763333](http://ubuntuforums.org/showthread.php?t=1763333)


**EDIT II:**

Pheww, Mint is still there, only it's hibernating session was gone. Obviously, Natty has trouble figuring out which swap partition to use. Nasty.

---

### Post by azupan on 2011-05-28
I don't know if you are still following this, but my Mint hibernation also got unreliable, so I had no other option but to look into this more in detail. The solution is here:

[http://ubuntuforums.org/showpost.php?p=10872411&postcount=24](http://ubuntuforums.org/showpost.php?p=10872411&postcount=24)


In short:

[LIST]
[*]Uninstall hibernate again, it doesn't do any good
[*]Check /etc/initramfs-tools/conf.d/resume and  /etc/fstab files, replace /dev/dm-## with UUIDs
[*]Uninstall uswsusp. If you need it, check & fix /etc/uswsusp.conf
[/LIST]

---

