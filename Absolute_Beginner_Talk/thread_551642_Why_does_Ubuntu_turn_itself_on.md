---
title: "Why does Ubuntu turn itself on?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-09-15
Strange but true.

I turn off Ubuntu using 'Shut Down'. Sometimes it reboots immediately. Other times it starts itself hours later.

Am I being hacked, trojan'd or similar? Is it a feature of Ubuntu that I don't understand?

Any help gratefully appreciated.

Regards,
Bob

---

### Post by oilchangeguy on 2007-09-15
possibably a bad power switch, or short. because even if you had a virus (which i doubt) once you kill the power it can turn it on again.

---

### Post by Wim Sturkenboom on 2007-09-15
Check your BIOS settings for:
wake on lan (wakes your PC up when a so-called MAgic Packet is received over a LAN connection)
wake on ring (wakes a PC up through the telephone line)
timed startup

Specially the startups after a few hours don't have to do with Ubuntu as Ubuntu is not running at that moment.

---

### Post by oilchangeguy on 2007-09-15
> **Wim Sturkenboom said:**
> Check your BIOS settings for:
wake on lan (wakes your PC up when a so-called MAgic Packet is received over a LAN connection)
wake on ring (wakes a PC up through the telephone line)
timed startup

Specially the startups after a few hours don't have to do with Ubuntu as Ubuntu is not running at that moment.

good point, i forgot about bios settings.

---

### Post by larry Gaminde on 2007-09-15
do you have microsoft wireless mouse and keyboard??

I had the same thing happen and changed some settings in bios and stopped the problem. I think it had something to do with the wireless setup which I had just installed.

another answer
1.    It Just wants to run !
2.    It really likes itself !
3.    Because it can !

---

### Post by bwallum on 2007-09-15
Amusing answer, thank you.

I'll check the BIOS settings. I use wired mouse and keyboard and wired LAN.

Off to check BIOS.....

---

### Post by bwallum on 2007-09-16
I have checked the BIOS and have no remote network log on or wake up from LAN call.

The only thing that appears to have made a difference is the ACPI setting. i have a choice of S1(POS) or S3(STR). I presume these refer to the various versions of ACPI

It was set on S3 and so I changed it to S1. So far my system has not restarted itself when instructed to turn off.

No idea if what I did is related to the result but offer it as a possible area of interest shopuld anybody have similar problems.

Thanks everybody for your help.

Kind Regards
Bob

PS I have subsequently found Ubuntu switching itself on again so ignore the above comments. I am now very confused!
Bob

PPS I have discovered that I can turn the computer on by moving the mouse. So if you accidentally move it the tiniest amount, up fires the computer. I have just started using a new mouse which co-incides with the problem starting so I am very confident about the mouse being the source of the problem. It is a Logitech two button and wheel mouse,  wired to PS2 motherboard connector, and is ball less. That is, it works on light reflecting off a surface rather than a ball driving two rollers. I can't seem to do anything about it with system/preferences/mouse control. Do let me know if you have a solution please.
Bob

---

