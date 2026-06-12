---
title: "how to install xubuntu on a mac ?"
date: 2013-03-31
forum: Apple Hardware Users
---

### Post by v41 on 2013-03-31
There do not seem to be any [+mac]("http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image") iso's available for xubuntu.
So is it possible to install 64-bit xubuntu on an intel mac?

(I would like to dual-boot 64-bit xubuntu 12.04 and OSX 10.6, using the legacy BIOS boot loader.)

---

### Post by Lars Noodén on 2013-03-31
The regular AMD64 disc images will work, too.  Or you can go with Lubuntu +mac and add the metapackage xubuntu-desktop and then (optionally) [removing the non-Xubuntu bits](http://www.psychocats.net/ubuntu/purexubuntu).

---

### Post by superchar42 on 2013-03-31
Xubuntu hasn't been on a ppc iso for a while it seems - I'd recommend lubuntu, I'm running it on an ibook g4. 

this made all the difference as a boot parameter: 
    live video=radeonfb:1024x768-32@60

from here: [http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html](http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html)

---

### Post by v41 on 2013-03-31
> **superchar42 said:**
> Xubuntu hasn't been on a ppc iso for a while it seems ...
I've clarified the first post to specify 'intel mac'.

---

### Post by v41 on 2013-03-31
> **Lars Noodén said:**
> The regular AMD64 disc images will work, too. In that case, why do ubuntu iso's come in 'regular' and '+mac' flavors?    From reading the forums, I was under the impression that:


[LIST=1]
[*]The regular iso [would not boot on some macbooks]("http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image") . 
[*]The regular iso would mess up the EFI partition, [bricking the system]("http://ubuntuforums.org/showthread.php?t=1743664"). 
[/LIST]

Looking at launchpad, I see that [problem (1) is still open]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633983"), while [problem (2) has been fixed]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089").

---

