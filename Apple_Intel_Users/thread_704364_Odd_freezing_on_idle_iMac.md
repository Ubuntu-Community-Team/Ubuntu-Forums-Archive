---
title: "Odd freezing on idle iMac"
date: 2008-02-22
forum: Apple Intel Users
---

### Post by cyberdork33 on 2008-02-22
For a little while now, I have been getting a strange issue with my iMac freezing after letting it sit idle for awhile. It is not going into sleep mode (puposely prevented, although putting the machine to sleep actually works, and it wakes up just fine). 

I thought the problem might be related to the ATI drivers since this started back in Catalyst 8.1 when [trying to stop xorg cause the whole thing to freeze]("http://ubuntuforums.org/showthread.php?t=671235") (this was related to atieventsd, which was fixed in 8.2). Then I tried disabling the screen saver and have tried various options in acpi-support. Nothing seems to work. It is especially annoying since it takes a certain while after the screen blacks for the freeze to actually occur. i.e., when I wake up in the morning, it is unresponsive, but if I leave it an hour and come back, it comes up when moving the mouse.

Anyway, I guess I am just asking for suggestions for config files I might check, or how I might capture a log / debug message or something so I can figure out what is happening.

---

### Post by prana on 2008-02-22
Can you ssh into the machine from a remote computer when it freezes? By the way, I have a Macbook Pro running 64 bit Gutsy and the ATI 8.1 driver and mine doesn't freeze on idle. It does freeze occasionally while I am doing some something and I think that may be related to the flash player. Usually, I try to just pause a flash video before getting rid of the flash page nowadays and I am hoping that will solve my freeze issue.

---

### Post by cyberdork33 on 2008-02-22
> **prana said:**
> Can you ssh into the machine from a remote computer when it freezes? By the way, I have a Macbook Pro running 64 bit Gutsy and the ATI 8.1 driver and mine doesn't freeze on idle. It does freeze occasionally while I am doing some something and I think that may be related to the flash player. Usually, I try to just pause a flash video before getting rid of the flash page nowadays and I am hoping that will solve my freeze issue.
I knew someone was going to suggest this. I believe that I have tried that before with no luck. I actually meant to try that this morning but forgot (no coffee yet). I removed the init scripts for atieventsd on Catalyst 8.1 which prevented freezing for it, but that was all fixed in 8.2 anyway so I really don't think it is related (at least not directly).

---

### Post by prana on 2008-02-22
> **cyberdork33 said:**
> I knew someone was going to suggest this. I believe that I have tried that before with no luck. I actually meant to try that this morning but forgot (no coffee yet). I removed the init scripts for atieventsd on Catalyst 8.1 which prevented freezing for it, but that was all fixed in 8.2 anyway so I really don't think it is related (at least not directly).

You could try disabling flash completely and see if that improves the freezing problem.

---

### Post by cyberdork33 on 2008-02-22
> **prana said:**
> You could try disabling flash completely and see if that improves the freezing problem.I will try that, but I don't that that is the issue since flash isn't even running then.

---

### Post by cyberdork33 on 2008-02-22
That's a definite no for ssh access.

---

