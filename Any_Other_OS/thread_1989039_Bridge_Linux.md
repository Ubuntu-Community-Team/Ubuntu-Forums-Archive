---
title: "Bridge Linux"
date: 2012-05-28
forum: Any Other OS
---

### Post by chris1216 on 2012-05-28
All,

I recently installed Arch on my netbook as many of you recommended it not only as a stable OS that can be as minimal as I wanted, but also as a way to increase my knowledge of the command line what what goes on behind a GUI.

Well, I will admit I liked the experience more than I thought I would, but it was probably also too big a jump for me to go from Ubuntu to Arch. I was reading about Bridge Linux, and it seemed a good step in my learning curve, but I am unable to get the 32bit ISO to work as when I try to boot from a USB stick I get a message telling me the kernel is not available. I read a review where this was the issue also.  I checked the Bridge Forum, but did not find my answer.

Can anyone point me to a working download, or can anyone point me to a distro based on Arch, but with more GUI in setting it up?

Chris

---

### Post by ratcheer on 2012-05-28
> **chris1216 said:**
> 

Can anyone point me to a working download, or can anyone point me to a distro based on Arch, but with more GUI in setting it up?



ArchBang - I used it for about six months, then made the jump to standard Arch Linux. It is excellent for learning about Arch without having to configure every little thing.

[http://archbang.org/](http://archbang.org/)

Tim

---

### Post by drawkcab on 2012-05-28
I'd like an iteration of Arch that I can install from usb--not Chakra (because I dislike KDE).

---

### Post by ratcheer on 2012-05-28
> **drawkcab said:**
> I'd like an iteration of Arch that I can install from usb--not Chakra (because I dislike KDE).

[http://wiki.archbang.org/index.php?title=Main_Page](http://wiki.archbang.org/index.php?title=Main_Page)

> You can customise your install to suit your needs, and draw on the vast resources & knowledge of the [Arch Linux community]("http://archlinux.org/"). The [download page]("http://archbang.org/download")  has links to both 32 & 64 bit versions, **bootable as a live CD / USB**  – allowing you to easily test it out before doing a full install. 
Tim

---

### Post by Antman on 2012-05-28
> **chris1216 said:**
> All,

I was reading about Bridge Linux, and it seemed a good step in my learning curve, but I am unable to get the 32bit ISO to work as when I try to boot from a USB stick I get a message telling me the kernel is not available. I read a review where this was the issue also.  I checked the Bridge Forum, but did not find my answer.

Can anyone point me to a working download, or can anyone point me to a distro based on Arch, but with more GUI in setting it up?

Chris

How are you transferring it to your USB stick? Bridge Linux works fine for me when I do a DD transfer to my USB sticks.

```
dd if=bridgelinux.iso of=/dev/sdb bs=4k
```
of course you would change the .iso name and /dev/sdX to reflect the real .iso and sdX device names.

---

### Post by chris1216 on 2012-05-28
Ratcheer--I will read up on Archbang and see if I think it is for me.

Antman-- I am using Universal USB installer.  I have never had an issue with it before, except on this distro of Bridge.  I will see if I can make the dd command work.

---

### Post by chris1216 on 2012-05-29
So after some more searching and reading I came across a suggestion to try a different program to put the iso on the USB.  I used Lili Live Linux creator and this solved the issue.

I ended up putting Archbang on the netbook and so far it is exactly what I want.  Minimal and snappy.    Thanks for the suggestion Ratcheer.

Chris

---

### Post by ratcheer on 2012-05-29
> 
I ended up putting Archbang on the netbook and so far it is exactly what I want.  Minimal and snappy.    Thanks for the suggestion Ratcheer.

Chris

You are welcome. I thought you would like it.

Note that once installation is completed and it has given you a usable default environment, ArchBang is just Arch Linux. You will get the same packages when you upgrade. There are some slight cosmetic differences, but that's about all.

Tim

---

### Post by drawkcab on 2012-05-29
> **chris1216 said:**
> So after some more searching and reading I came across a suggestion to try a different program to put the iso on the USB.  I used Lili Live Linux creator and this solved the issue.

I ended up putting Archbang on the netbook and so far it is exactly what I want.  Minimal and snappy.    Thanks for the suggestion Ratcheer.

Chris

Chris, can you point me in the direction of the stuff you looked at?

---

