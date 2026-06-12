---
title: "Why can't keyboard use in grub?"
date: 2007-10-14
forum: Apple Intel Users
---

### Post by Jeongtaek Kim on 2007-10-14
I boot three OS, Ubuntu Feisty, Mac OSX and Windows XP.

I boot linux and windows by grub.

But I can't often use keyboard in grub, but sometimes I can use keyboard.

So I reboot again, I'm afraid of my HDD.
 
I use macbook, Core 2 Duo 2.0Ghz and 1GB RAM. :confused:

---

### Post by duffman25 on 2007-10-14
> **Jeongtaek Kim said:**
> I boot three OS, Ubuntu Feisty, Mac OSX and Windows XP.

I boot linux and windows by grub.

But I can't often use keyboard in grub, but sometimes I can use keyboard.

So I reboot again, I'm afraid of my HDD.
 
I use macbook, Core 2 Duo 2.0Ghz and 1GB RAM. :confused:

There's a firmware upgrade from apple that solves this issue.
[http://www.apple.com/support/downloads/macbookefifirmwareupdate11.html](http://www.apple.com/support/downloads/macbookefifirmwareupdate11.html)

---

### Post by Jeongtaek Kim on 2007-10-14
I already upgraded firmware.

But I can't still  use keyboard.

Is it problem of refit?

---

### Post by cyberdork33 on 2007-10-15
> **Jeongtaek Kim said:**
> I already upgraded firmware.

But I can't still  use keyboard.

Is it problem of refit?

Please confirm that your update is successful:
[quote=Apple]After the firmware is successfully applied to your computer, your BootROM Version will be:
MB21.00A5.B07

 You can confirm the version of the BootROM installed on your computer using System Profiler.[/quote]

---

### Post by pa_nilssen on 2007-10-17
I had same problem.

Don't know if this goes for your MacBook Pro, but I used another firmware update.
The link here showed one in an earlier post, was one I could not use.

I used the 1.4 version, and everything worked out fine after that.

---

### Post by cyberdork33 on 2007-10-17
> **pa_nilssen said:**
> I had same problem.

Don't know if this goes for your MacBook Pro, but I used another firmware update.
The link here showed one in an earlier post, was one I could not use.

I used the 1.4 version, and everything worked out fine after that.
Macbook Pro has different firmware than the Macbook... but yes. You should just be able to use the software updater in OSX to get the correct firmware update for your system.

---

### Post by ivesjd on 2007-10-19
one solution would be to install grub on the Ubuntu partition and let windows have the mbr then you wont have to select windows from grub. Just which kernal you want to use.

---

### Post by cyberdork33 on 2007-10-31
My keyboard is broken again. It may be related to Leopard.

---

