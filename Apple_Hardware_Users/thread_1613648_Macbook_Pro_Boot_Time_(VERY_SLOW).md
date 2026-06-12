---
title: "Macbook Pro Boot Time (VERY SLOW)"
date: 2010-11-04
forum: Apple Hardware Users
---

### Post by vsh3r on 2010-11-04
Hi,

How do I speed up the Macbook Pro boot time?  In OSX when I boot it goes directly to the mac logo.  In Ubuntu there seems to be a 10 second or more hesitation before it access my hard drive.  Is there anyway to change some settings in the BIOS / EFI?

V$H.

---

### Post by linuxopjemac on 2010-11-05
Did you bless the partition?

---

### Post by OTSB708 on 2010-11-05
I have the same issue but I am using a single boot partition on my MBP 2,2.  Is this the blessing you are talking about? [http://mac.linux.be/content/single-boot-linux-without-delay](http://mac.linux.be/content/single-boot-linux-without-delay)

---

### Post by vsh3r on 2010-11-05
Hi,

Updating the bootloader to use rEFIt rather then grub may not work and still have the same issues.  Has anyone else tried using rEFIt?

V$H.

:popcorn:

---

### Post by vsh3r on 2010-11-05
Hold on.. from what I'm reading in that html file you posted all I need to do if I already have Ubuntu installed on my drive is boot from the OSX cd and type ...
[FONT=monospace]
```

[/FONT]bless --device /dev/diskXsX --setBoot --legacy --verbose 

```

where diskXsX is the location of my linux drive.
This sounds great.. however, if I put in my old OSX drive back in the system will this mess anything up?

V$H.

---

### Post by linuxopjemac on 2010-11-06
No, it should not be. In all cases, make a backup before doing this kind of stuff. I recommend CloneZilla.

---

### Post by SwedishWings on 2010-11-25
I have the same issue on my MacBookPro5,1 with both Maverick and Lucid (tripple boot).

I have tried both with and without rEFIt, but always with the same "hesitation" as noted above. 

In addition, sometimes the boot halts at that point, and i need to restart to get Ubuntu to boot.

Any ideas?

Thanks,
Mike

---

