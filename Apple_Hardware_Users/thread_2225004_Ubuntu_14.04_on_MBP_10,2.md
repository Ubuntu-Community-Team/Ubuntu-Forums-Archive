---
title: "Ubuntu 14.04 on MBP 10,2"
date: 2014-05-19
forum: Apple Hardware Users
---

### Post by Derek_Parker on 2014-05-19
[FONT=arial]I looked at the guides section [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) and noticed there is no information on the MBP 10,2 for any ubuntu version.

I'd like to dual boot, is there anything specific to 10,2 that anyone is aware of, or any 10,2 specific guide I could use? Should I use the mac iso, and do I need [COLOR=#444444]rEFInd or can I just install alongside using grub?

Thanks in advance for the help![/COLOR][/FONT]

---

### Post by este.el.paz on 2014-05-19
@D_P:

There is a sticky at the top of the apple users page here on Intel apple . . . but, I've got a triple boot set up on MBP 5 something . . . I used rEFInd . . . .  Depending on how paranoid you are you could try the "Install next to" option, however, the linux system install should go in after the OSX . . . .  I, being paranoid, used Disc Utility to partition the HD in OSX, and there used to be a "Install in largest free space" option, so in GParted you could the partition set up in OSX and labeled as "FAT" . .  and turn it into "Free" and then page back to the install options and pick "largest free space" . . . but that didn't show up in my recent 14.04 install . . . so I had to set up 3 partitions, something like 10MB for GRUB or "bios_grub" whatever you want for home that is over their minimum requirement 6GB+ . . .set as "ext4" & flagged as "/" . . . and one for "swap" with about 1.5x the system RAM . . . .  Don't forget to check the md5sum number.

I haven't tried the new "mac" file .iso edition, apparently you might not need rEFInd or it might do stuff that is apple friendly . . . you could try them both out . . . an install only takes 20+ mins.

e.e.p.

---

### Post by Derek_Parker on 2014-05-19
Cool, thanks for the reply. I'll try it out.

---

### Post by MikeBraxner on 2014-05-19
Take a look at the opening remarks on [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy).

---

