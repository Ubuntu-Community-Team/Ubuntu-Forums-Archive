---
title: "WinXP having no net after one Ubuntu restart"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by poisonborz on 2007-02-22
...I can't even imagine what could be wrong: Normal Kubuntu Edgy install, but everytime I use Edgy, and restart my computer, I boot WinXP Prof, and it has no network connection whatsoever (as if I plugged out the cable). After another restart, everything works again - but after every Kubuntu restart, the problem reappears. Any ideas...? Thanks...

---

### Post by Yoooder on 2007-02-22
This is most definately strange.  Is your NIC on-board?  Are you doing a Reboot, or a Shutdown followed by booting back up?

If it's onboard then you could try upgrading your firmware perhaps...

---

### Post by netkid91 on 2007-02-22
Try doing a full shutdown instead of a restart, so we can see if a cold boot fixes it.  If it does, it might be an issue with your motherboard's BIOS not cooperating with your network card after a hot reboot.
(Note: After any modern OS finishes shutting down, it reboots the system by returning execution to the BIOS, and sometimes the BIOS doesn't reset things properly)
Also, what is the model of your MoBo and network card if you have a non-integrated one.

---

### Post by poisonborz on 2007-02-23
Yes, the card is on-board, Broadcom Gigabit chipset on a good old ASUS A7V8X.
After a cold boot, everything works fine, as I said, the problem only comes up after (one) soft reset.

Sadly, I can only upgrade the Broadcom firmware with a new bios, but in the past, new versions caused troubles for me (motherboard not detecting my samsung ram, etc).
Sigh... Cold, freezy resets from now on, I guess.

---

### Post by nudnik on 2007-02-23
> **poisonborz said:**
> Yes, the card is on-board, Broadcom Gigabit chipset on a good old ASUS A7V8X.
After a cold boot, everything works fine, as I said, the problem only comes up after (one) soft reset.

Sadly, I can only upgrade the Broadcom firmware with a new bios, but in the past, new versions caused troubles for me (motherboard not detecting my samsung ram, etc).
Sigh... Cold, freezy resets from now on, I guess.

When using XP, you might try going to the Control Panel and clicking on Network Connections. Once you have accessed the icon, you should be able to right click  and select the Repair option. This is sometimes an easy way to reset things without having to reboot the entire system.

---

