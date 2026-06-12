---
title: "Problems starting Ubuntu LiveCD"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Alain2k5 on 2006-05-05
Ok, I have a Compaq SR1210NX Computer and I'm having a tough time running the Ubuntu Live CD. The CD loads fine, i get the boot prompt. I hit eter for the default and the system just reboots, I tried "acpi=off" and it works.. And voila! Ubuntu starts loading but, as soon as it gets to the loading screen (ubuntu logo and progress bar) the system freezes when it gets to "Setting up hotplug" I tried various other boot instructions listed on F1 but none worked. What should I do?

---

### Post by Papa-san on 2006-05-05
One of the options (I think) is to check the integrity of the cd. Sometimes the ISO image is corrupt, depending on the speed at which it was burned. I even got bad live cd's when I ordered them. (4 out of the 5 were bad!) If you made the cd yourself, check it to see if it is 'correct' (thru 'check-sum') Then it should be burned at a slow speed, like at 4x...

Other than that suggestion from a noob, hang in there for some of the linux guru's that pop in here! Don't woory, they can walk you thru most anything. The only unsolvable problems are when the hardware has issues.

Good luck, and don't give up! Ubuntu kicks butt!

---

### Post by Sef on 2006-05-05
Did you do an md5sum check after it finished downloading?

---

### Post by Alain2k5 on 2006-05-06
I did that and it's fine, I did some googling and found out that the bios video setting must be set to **Onboard**, plus the acpi=off boot instruction for it to boot properly.. Thanks though!

---

