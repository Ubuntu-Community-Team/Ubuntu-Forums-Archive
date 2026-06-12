---
title: "Installing to external hard-drive good idea?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by happysmileman on 2007-06-12
I will be installing Linux and would like to know whether it would be recommended to install onto an external hard-drive.

I'm almost out of space on my 80GB internal drive and could get a 160/250GB drive for €100-150 and would like to know whether the speed difference would be very noticeable...

I understand that external drives are slower than internal drives... but would it be very noticeable for just everyday things such as using Firefox or Thunderbird and playing music

---

### Post by KCormier on 2007-06-12
That would most likely make a very big difference!  I haven't tried it, but I know external hard drives can be MUCH slower depending on how they are hooked up.  USB drives are awful.  Firewire is much better but still slow compared to an internal ide or sata connection.  External sata would run ubuntu just like an internal drive would.  It all depends on your setup.

---

### Post by happysmileman on 2007-06-12
That's a problem because I already have Windows and Mandriva on main drive, and can't get a new internal one (not my computer, couldn't install it, external are easier to find)

---

### Post by Calash on 2007-06-12
As stated above it will be slower

Pulling numbers from my head here...

Sata - 300MBps
USB-2 - 480Mbps
Firewire - 400Mbps  (I think the new standard is faster)

The lower b is bits, the upper is bytes.  So compared to a SATA drive you will feel the speed loss, even on a solid state type drive (Flash memory).  However, it should be faster than the live CD, so if that is livable then it may be enough for you.

---

### Post by happysmileman on 2007-06-12
> **Calash said:**
> As stated above it will be slower

Pulling numbers from my head here...

Sata - 300MBps
USB-2 - 480Mbps
Firewire - 400Mbps  (I think the new standard is faster)

The lower b is bits, the upper is bytes.  So compared to a SATA drive you will feel the speed loss, even on a solid state type drive (Flash memory).  However, it should be faster than the live CD, so if that is livable then it may be enough for you.

Livable as in I only really intend to use Firefox/Thunderbird/Amarok, and from my basic knowledge of stuff the executable parts of these would quickly be loaded into RAM and not touch the drive except loading sonngs and saving stuff, which many recommend is done on drive anyway.,...

However another problem is that I might be using it for LFS and compiling would be very slow methinks... However compiling seems to be proportional to the size of code and therefore could probably be written to external disk faster than actually compile for me... Since I sure as hell can't compile anything close to 60MB/s... though temp data may be that?

Would it slow down compiling or would it be ok since most of the things would compile slowly anyway?

Edit: The source files wouldn't be on External drive, not at first anyway

---

