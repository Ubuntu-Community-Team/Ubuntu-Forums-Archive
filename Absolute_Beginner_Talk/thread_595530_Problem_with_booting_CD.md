---
title: "Problem with booting CD"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by hedera on 2007-10-28
I, on the other hand, carefully followed the documented procedures for burning an ISO CD, and every time I try to boot from the CD in my laptop CD drive, I get this error:

/bin/sh: can't access tty; job control turned off

and then I'm at a system prompt with no indication what to do to bring up the graphical desktop.  And no man pages, I tried.  Having a small amount of sysadmin experience, I doubt that much will happen if the job control really is turned off...

Someone at the Dell booth at LinuxWorld gave me what purported to be a live, bootable Ubuntu CD, and I get the same error every time I try to boot the laptop from that in the CD drive.  

There's obviously something I don't know here, can someone help?  Was it unreasonable of me to expect that booting Ubuntu from the live CD would bring up a graphical desktop?

Yours in confusion,
hedera

---

### Post by overdrank on 2007-10-28
> **hedera said:**
> I, on the other hand, carefully followed the documented procedures for burning an ISO CD, and every time I try to boot from the CD in my laptop CD drive, I get this error:

/bin/sh: can't access tty; job control turned off

and then I'm at a system prompt with no indication what to do to bring up the graphical desktop.  And no man pages, I tried.  Having a small amount of sysadmin experience, I doubt that much will happen if the job control really is turned off...

Someone at the Dell booth at LinuxWorld gave me what purported to be a live, bootable Ubuntu CD, and I get the same error every time I try to boot the laptop from that in the CD drive.  

There's obviously something I don't know here, can someone help?  Was it unreasonable of me to expect that booting Ubuntu from the live CD would bring up a graphical desktop?

Yours in confusion,
hedera

Hi and welcome if you could give us some specs on the system we maybe able to help. I the mean time if you would like to try 
When you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you recieve the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot.

---

### Post by hedera on 2007-10-28
Sure, I was trying to boot from the CD drive of a Dell Inspiron 1420 laptop running Windows Vista Home Premium.  My thought was that I might turn the laptop into a dual-boot Vista/Ubuntu system, but the inability to get Ubuntu to start is a little daunting.

I'll try your suggested workaround tomorrow and see how that does.

Thanks,
hedera

---

