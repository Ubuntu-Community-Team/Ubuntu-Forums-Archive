---
title: "[SOLVED] Auto shutdown not working"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-10-21
Is there a way at the present time to fix the shutdown problem in gutsy 7.10...

---

### Post by llamakc on 2007-10-21
What problem? Shutdown works for me. What sort of rig are you on? How are you initiating shutdown?

---

### Post by alienexplorers on 2007-10-21
My machine is an old K6-III 450 and when I boot it says the BIOS is out of date.  It tells me to add acpi=force.

---

### Post by llamakc on 2007-10-21
Do you know how to add that to the menu.lst file?

---

### Post by alienexplorers on 2007-10-21
Not sure if I added it right.  I put it after quiet in menu.lst....

---

### Post by llamakc on 2007-10-21
An easy way to get help with config files is to cut/paste the config file here.

---

### Post by jerrylamos on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/119308](https://bugs.launchpad.net/ubuntu/+bug/119308) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is out of my post Workarounds on Installation & Upgrades:

"Shutdown" doesn't
This system powers off with Edgy, Dapper, Knoppix, ... but not Feisty. If I select Shutdown after a while nothing's happening, there's no message on the screen, and the keyboard and mouse are dead. Someone on some forum (where?) suggested:
Do sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Power off however you can, power back up and on "Shutdown" it should. Mine did.
Usual cautions apply when changing system files.....

There's also a fix that works for someone else if you go to the Launchpad Bug URL.

I reported this bug on Feisty and also Ubuntu.  There hasn't been any Ubuntu developer activity on this bug so don't expect a fix.

Jerry

---

