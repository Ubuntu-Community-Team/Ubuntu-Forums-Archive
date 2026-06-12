---
title: "Help Installing Ubuntu"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by Oliver Barker on 2007-05-05
Hey, is it possible to have Ubuntu on a iPod Hard Drive 4gb??? if so i would be grateful for any help anyone can give me on how to install it onto it. If possible a detailed information.

---

### Post by Chrisj303 on 2007-05-05
Check this out : [www.ipodlinux.org/](www.ipodlinux.org/)

While i don't think it's possible to have UBUNTU on your ipod - there is a good chance you can install this ipod specific distro.

good luck,


*edit - sorry that link has stopped working, no worries just google "ipod linux" - it's the first link.

---

### Post by ronocdh on 2007-05-05
> **Chrisj303 said:**
> Check this out : [www.ipodlinux.org/](www.ipodlinux.org/)

While i don't think it's possible to have UBUNTU on your ipod - there is a good chance you can install this ipod specific distro.

good luck,


*edit - sorry that link has stopped working, no worries just google "ipod linux" - it's the first link.
Argh I had a reply to this thread open in another tab and of course I ADD'd out and was in the other forums. (Internet addiction is a bitch.) I think OP meant he wanted to boot Ubuntu on his computer from the iPod HD, though perhaps I misunderstood.

And I gotta say, that's a totally bizarre request, but thus just the type we like to see here! =)

---

### Post by Chrisj303 on 2007-05-05
I don't know - the way he's worded his post, it could be taken both ways - if it's wrong i'm sure he'll be back.

You can boot from an ipod though - i'm sure of it. I *think* you just treat it as a USB drive.

---

### Post by ronocdh on 2007-05-05
> **Chrisj303 said:**
> I don't know - the way he's worded his post, it could be taken both ways - if it's wrong i'm sure he'll be back.

You can boot from an ipod though - i'm sure of it. I *think* you just treat it as a USB drive.
Hm, with 4GB he could mean a Nano, but he could also mean an absolutely ancient firstgen FireWire, couldn't he? Heck if I remember, you needed a backpack to carry those things around. Made you look like a radio operator from WW2. Anyway. Oliver, what's up?

---

### Post by benanzo on 2007-05-05
I don't see why he wouldn't be able to boot Ubuntu from an iPod.  So long as his machine supports USB booting.  It's really just an external drive.

---

### Post by ronocdh on 2007-05-05
> **benanzo said:**
> I don't see why he wouldn't be able to boot Ubuntu from an iPod.  So long as his machine supports USB booting.  It's really just an external drive.
But I thought the huge issue was that the MBPs *don't* support booting from USB right away, and you really have to fight to make it work? BIOS users can just flip an option to make it work, but we EFI MacTel people have it rougher. Or so I thought. I personally have never tried myself, but that's what I've read.

---

### Post by Lt_Data on 2007-05-05
I'm definitely going to attempt this with my old iPod which I rarely use (save for running). My 60GB black video iPod is like my freakin' life support, though, so I won't be as daring as to try putting Ubuntu on that. I'll update my response on this thread once I've succeeded or failed. 

Peace

---

### Post by benanzo on 2007-05-05
I'm trying it right now, I'll let you know in about 20 mins.  The ipod disk is really slow..installing is taking forever.

---

### Post by benanzo on 2007-05-05
well, the installer was successful.  I just booted to the feisty livecd and partitioned the ipod with a 5gb / a 500 mb swap a 5gb /home a 13 gb fat32 partition then installed Ubuntu to it.  I installed grub without any errors, but none of my machines will boot it.  My Macbook doesn't even give me the option and the BIOS on my old dell just hangs while it's looking at the usb boot disk.    hmmmm.

---

### Post by ronocdh on 2007-05-05
> **benanzo said:**
> My Macbook doesn't even give me the option and the BIOS on my old dell just hangs while it's looking at the usb boot disk.    hmmmm.The former is, I think, because Apple intentionally made it difficult to boot these computers from USB; something they did with EFI. I hear it's easier when the USB volume is formatted to HFS+, but that doesn't help us here. As for the latter issue, geez, good luck. =)

---

### Post by Oliver Barker on 2007-05-07
nonono! u don't get it sorry, i wasn't saying enough i mean't is it possible to partician a iPod so it has Ubuntu on  it as well as can still play music, and i just select when i want to run from it (firewire cable) when i restart by holding down alt....

:lolflag:

---

### Post by Chrisj303 on 2007-05-07
> **benanzo said:**
> well, the installer was successful.  I just booted to the feisty livecd and partitioned the ipod with a 5gb / a 500 mb swap a 5gb /home a 13 gb fat32 partition then installed Ubuntu to it.  I installed grub without any errors, but none of my machines will boot it.  My Macbook doesn't even give me the option and the BIOS on my old dell just hangs while it's looking at the usb boot disk.    hmmmm.

When you partitioned your ipod, did you flag it as bootable? - this can be done via qtparted (right click on partition > manage flags > bootable)


chrisj303

---

