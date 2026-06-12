---
title: "Live CD problems - PC reboots before it can load"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by scapermoon on 2006-03-01
Hi! I just received my ubuntu disks in the mail today (thank you! :D) and I've been trying to load the live cd, but I'm having some problems. Everything seems to work fine until I get to the "loading kernel" part. As soon as I do, the computer reboots. I've tried typing in "live noapic nolapic" but the same thing happens. I'm stumped.

My computer is a compaq presario with a 2.53 GHz Celeron and 248MB of RAM (kinda slow I know, but it's all I could afford.) Any help would be most appreciated! :D

---

### Post by scapermoon on 2006-03-02
So, I tried to install ubuntu rather than continue trying to get the livecd to work, and I'm having the same problem. It boots fine from the CD until I get to the part where the kernel is loading, and then my PC suddenly restarts itself. I've googled the problem over and over, but I can't find anything that helps. Any ideas?

---

### Post by AtinLango on 2006-03-02
I would try (an)other CD(s).

I had problems installing Ubuntu ( I had downloaded and burnt) until I burnt another CD then it worked without problems. The CDs may not have been burnt right.

Or, try the live CD on (an)other computer(s) and see if it works. If it doesn't work, then its likely to be a bad CD.

---

### Post by scapermoon on 2006-03-02
Actually, both the install and live cd are giving me the same error. Could it be possible they could both be bad? :confused:

---

### Post by AtinLango on 2006-03-02
I am thinking of two scenarios:

1. Both CDs were burnt using the same device, so they could get the same defect.
2. They could have developed a problem in transit, e.g. mis-handling.

If you try as I suggested, it will help the gurus isolate the problem.

---

### Post by daredevil on 2006-03-02
Try to download new image of live cd, burn it and try again.

---

### Post by scapermoon on 2006-03-02
Unfortunately, I don't have access to another PC that will run ubuntu (my old one doesn't even come close to the system requirements, and I'm not even sure if it still works.) And because I'm still on dialup, it would take me more than three days online to download an image. So, I went ahead and put in another shipit order. I'll try this again when the new cds arrive. :)

Thanks for all of your help! I really do appreciate it. :D

---

### Post by pbaehr on 2006-03-02
I'd hate to see you wait several weeks to get your new CDs only to find out they do exactly the same thing.

I assume (I don't have a set) that the official Ubuntu CDs are pressed, not burned as burning CDs in the quantity they distribute them in would be a huge undertaking.

The fact that the Live CD and the Install CD do exactly the same thing at exactly the same spot would make be a HUGE coincidence.

I suspect it is your hardware. I would make every effort to try the Live CD out on a friends computer and see what happens.

---

### Post by sebimeyer@sebimeyer.com on 2006-12-08
Are you by any chance the scapermoon I've crossed paths with before? If my name doesn't look familiar, you probably don't know me.

I've been a lurker in these forums for a few weeks now because I'm interested in setting up and old PC as ubuntu server. If you're the one I think you are, I certainly wouldn't mind downloading an image, burning it and sending it to you before I leave the country on Dec. 17.

Global village indeed. If you're the one. ;)

---

### Post by altonbr on 2006-12-18
This is interesting. I'm trying to install on a Compaq Presario SR1224NX as well. I wonder if it's the hardware because I'm wiped the hard drives with BootIt NT after doing an initial format with the Windows CD and the Ubuntu Alternate Dapper CD STILL won't boot.

I've used this CD on 5 other computers, and they all work. I'm suspecting that it has to do with the inexpensive parts Compaq throws in.

This thread here: [http://www.ubuntuforums.org/showthread.php?t=314005](http://www.ubuntuforums.org/showthread.php?t=314005) suggests running Memtest86+ to see if it's your memory modules. I'll try it and give you the results.

I'm posting my CPU-Z log from before I formatted. You must change the extension to .htm from .txt to read it in your browser.


EDIT:: I almost forgot. I've also tried install DSL Not! and after I hit "enter" for it to install, it just hangs. I will try other distros soon.

---

### Post by altonbr on 2006-12-18
I just ran Memtest86+ on the Samsung 512MB PC3200 module, and it returned no errors. So it then replaced it with an AzenRam 512MB PC3200 module that was working in another computer of mine, and the Ubuntu Alternate CD (Dapper) still restarts when I try "Install in text mode" or "Check CD for defects". I've also tried the Dapper LiveCD and the Edgy Alternate and LiveCD. I will try other distributions soon. But it appears that it's NOT the memory module.

---

### Post by altonbr on 2006-12-18
SUSE Linux 10.1 with acpi=off seems to boot and install...

---

### Post by altonbr on 2006-12-18
[SIZE="5"]**_FIX_**[/SIZE]

So usually ACPI errors come up similar to this: "[4294667.296000] ACPI: Unable to locate RSDP" but in this case, it doesn't.

In order to fix the above error, or the restarting error, hit "F6" to edit the boot flags and add "acpi=off" before the final "--".

That's why SUSE 10 worked, because I had to option to boot with acpi=off... I just merely forgot to add it in during my Ubuntu install. You should be proud to know that Ubuntu is now  back on the computer 8)

---

