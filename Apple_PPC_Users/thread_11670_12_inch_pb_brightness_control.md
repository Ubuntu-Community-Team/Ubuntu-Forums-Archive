---
title: "12 inch pb brightness control"
date: 2005-01-18
forum: Apple PPC Users
---

### Post by resiance on 2005-01-18
Hello everyone,

I currently cannot control brightness on my 12 inch pb. I have searched the forums and find various references to brightness problems and have fiddled a bit but no luck so far. The one post relating directly to the 12 inch pb has no replies alas.

pbbuttonsd, gtkpbbuttons and powerprefs are all installed. Other posts mention fblevel and /dev/pmu, is this a permissions thing? The pbbuttonsd.conf mentions /dev/fb0, is that the right display to be sending the commands to? Volume and eject all work just fine.

Any advice appreciated. Out of interest, have any 12 inch pb owners had their brightness work by default or is this a problem for all?

Thanks.

---

### Post by Viro on 2005-01-18
[QUOTE=resiance]Hello everyone,

I currently cannot control brightness on my 12 inch pb. I have searched the forums and find various references to brightness problems and have fiddled a bit but no luck so far. The one post relating directly to the 12 inch pb has no replies alas.

pbbuttonsd, gtkpbbuttons and powerprefs are all installed. Other posts mention fblevel and /dev/pmu, is this a permissions thing? The pbbuttonsd.conf mentions /dev/fb0, is that the right display to be sending the commands to? Volume and eject all work just fine.

Any advice appreciated. Out of interest, have any 12 inch pb owners had their brightness work by default or is this a problem for all?

Thanks.[/QUOTE]
 Brightness controls aren't supported on the Powerbook 12". I think it has to do with the nVidia video card. I've been trying to get mine to dim for a long time with no success at all. Guess we'll have to wait till nVidia releases the specs or some proper drivers for PPC Linux.

---

### Post by resiance on 2005-01-18
Ah, that would explain it then, thanks for clearing that up. A real shame though if you wanna conserve battery life. This and the Airport Extreme issue are the two things stopping the pb from being pretty much the perfect portable linux machine, hopefully nVidia and Broadcom will pull their fingers out at some point soon :)

---

### Post by Viro on 2005-01-18
[QUOTE=resiance]Ah, that would explain it then, thanks for clearing that up. A real shame though if you wanna conserve battery life. This and the Airport Extreme issue are the two things stopping the pb from being pretty much the perfect portable linux machine, hopefully nVidia and Broadcom will pull their fingers out at some point soon :)[/QUOTE]
 And sleep. Don't forget sleep. The Powerbook 12" just can't sleep, which makes lose a lot of it's usefulness.

---

### Post by maddog39 on 2006-12-17
I just put ubuntu on my 12" powerbook and I noticed that the title bar and some other things are burning into the top of the screen because its at 100% brightness all the time and I'm on the computer almost constantly. I even tried some software based utilities from the ubuntu repository to try and control the brightness, but no luck with that either. Can't you just compile the nvidia drivers from source or something, or do you absolutely need the proprietary drivers for this. Brightness seems like a really simple feature, I can't believe they would not include that feature in the open source version of the driver.

---

### Post by a.panico on 2006-12-22
Salut!

I think that is a problem of configuration because it works in GentooPPC. I've a Powerbook 12" 1.5GHZ with the NVIDIA 5200. I've tried but I've not that this funciton works in Ubuntu.

Au revoir

---

### Post by KaOS-bEat on 2006-12-23
> **a.panico said:**
> Salut!

I think that is a problem of configuration because it works in GentooPPC. I've a Powerbook 12" 1.5GHZ with the NVIDIA 5200. I've tried but I've not that this funciton works in Ubuntu.

Au revoir

I also had it working in gentoo... once. I believe it's kernel related, I always compiled my own kernels and with some tweaking it worked fine on my 1.33Ghz 12" Powerbook, also doomed with nvidia hardware. But this was in the 2.6.10 kernel series. I had to upgrade because of wifi support (bc43xx is not available in 2.6.10) and eventually I also switched to ubuntu. But I would love it if this worked. Maybe [[COLOR="Sienna"]this[/COLOR]]("http://nouveau.freedesktop.org/wiki/") will help. *nouveau* is a rather *new* project, but there's lots of activity.

KaOS

---

### Post by tharrrk on 2007-06-22
> **a.panico said:**
> Salut!

I think that is a problem of configuration because it works in GentooPPC. I've a Powerbook 12" 1.5GHZ with the NVIDIA 5200. I've tried but I've not that this funciton works in Ubuntu.

Au revoir

Hi there !
Could you please specify kernel version and your .config (or just fb related stuff ?)
I tried >=2.6.20-gentoo on my 12" 1.5G PB with no luck :(

Thank you very much
Tharrrk

---

