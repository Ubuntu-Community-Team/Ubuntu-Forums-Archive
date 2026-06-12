---
title: "Thinkpad feezing: bios problems?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Cociani on 2008-01-28
I have an older IBM iSeries thinkpad which I have loaded XUBUNTU 7.10 into. It would not recognize the BIOS year so I used the ACPI force code "vga=792 acpi=force irqpoll' This enabled me to load the operating system but now it freezes solid within a few minutes of bootin up; sometimes while booting up.

Do I need to use a different acpi force code? Mess with the bios?

The laptop has a PIII 750 MHz proccesor 192 MB of ram, 20 GB HD. The system bios version is V1.oop and the VGA bios version is TBAV04.07

I am totally new to Linux and about an average PC user so please forgive my ignorance.

---

### Post by spiderbatdad on 2008-01-28
have you looked into other parameters at boot, by hitting f6...then f1...then f6? I would think:
noapic nolapic noirqpoll

---

### Post by Cociani on 2008-01-28
I have not tried that, could you explain a little further what you mean? Again pardon my ignorance.

---

### Post by spiderbatdad on 2008-01-28
i was assuming you were still trying out the live cd. At the options screen, you can hit F6, and from there F1 and F6 again for some examples. I would suggest editing the grub line that appears on the options screen after F6 by deleting everything back to and including "ro --quiet splash" and replace with noapic nolapic vga=791

see if that works...there are other parameters, as you know.

---

### Post by Cociani on 2008-01-29
I am using the alternate install cd. I tried what you said but I think I must have placed the code in the wrong spot in the line as it is different then the live CD. Where should I place it with the Alternate cd?

---

### Post by Paulmd on 2008-01-29
> **Cociani said:**
> I have an older IBM iSeries thinkpad which I have loaded XUBUNTU 7.10 into. It would not recognize the BIOS year so I used the ACPI force code "vga=792 acpi=force irqpoll' This enabled me to load the operating system but now it freezes solid within a few minutes of bootin up; sometimes while booting up.

Do I need to use a different acpi force code? Mess with the bios?

The laptop has a PIII 750 MHz proccesor 192 MB of ram, 20 GB HD. The system bios version is V1.oop and the VGA bios version is TBAV04.07

I am totally new to Linux and about an average PC user so please forgive my ignorance.

What is the machine-type/model?

For example: 6643-12u, (An ibm netvista all-in one) this would enable me to research the machine and determine if there is a bios update, (preferably one after the cutoff date, which would eliminate the need to force acpi)  whether the machine supports acpi, and if not, what the best options are.

---

### Post by Cociani on 2008-01-29
It says on the back- Type 1161 -93U

---

### Post by Paulmd on 2008-01-29
> **Cociani said:**
> It says on the back- Type 1161 -93U

You already have the latest bios. Further, you should not be failing the cutoff date on that machine, even the first release bios is written after the cutoff date.

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4WURG4](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4WURG4)

Edit:

I suggest diagnosing the machine

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4X2P56](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4X2P56)

---

### Post by Cociani on 2008-01-29
Ok, is there a seeting in the bios I should look at changing? It definatelly is not recognizing the BIOS year for some reason.

---

### Post by Cociani on 2008-01-29
Ok I will try the diagnosis.

---

### Post by Paulmd on 2008-01-29
> **Cociani said:**
> Ok, is there a seeting in the bios I should look at changing? It definatelly is not recognizing the BIOS year for some reason.

I am still looking into that question.

---

### Post by Cociani on 2008-01-29
The computer does not have a floppy drive only a cd rom using xp and infra recorder how would I burn these files onto a cd/r would I just burn two cds as image files or is there a different mothod?

---

### Post by Paulmd on 2008-01-29
> **Paulmd said:**
> I am still looking into that question.

Found something, Not very useful, but it seems others have had issues installing linux on that machine.

[http://ubuntuforums.org/showthread.php?t=433108](http://ubuntuforums.org/showthread.php?t=433108)

[http://ml.osdir.com/org.user-groups.linux.canterbury/2005-02/msg00001.html](http://ml.osdir.com/org.user-groups.linux.canterbury/2005-02/msg00001.html)

---

### Post by Paulmd on 2008-01-29
> **Cociani said:**
> The computer does not have a floppy drive only a cd rom using xp and infra recorder how would I burn these files onto a cd/r would I just burn two cds as image files or is there a different mothod?

That diagnostic program should be available in cd format. Let me check.

---

### Post by Paulmd on 2008-01-29
> **Paulmd said:**
> That diagnostic program should be available in cd format. Let me check.

It seems it's not available in iso format for that machine.

---

