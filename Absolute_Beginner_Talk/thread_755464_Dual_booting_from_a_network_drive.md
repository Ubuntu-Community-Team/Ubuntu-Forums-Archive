---
title: "Dual booting from a network drive??"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by AndrewEsther on 2008-04-14
Question: I want to take Windows off of yet another desktop in the office and throw ubuntu onto it. However, the user of said computer does my accounts, and she uses QuickBooks. Because I'm not the one who makes the decisions about what accounting software to use, we'll be sticking with QuickBooks. What I want to do is put WinXP on an external usb hdd and use it to boot from when she works on the accounts, and for all else she would love to use ubuntu (doing this is, in my opinion, an easier and more stable way to get around not having a version of QuickBooks that gets along with ubuntu) Is there a way that I can keep that usb hard drive plugged into my server and boot from it as a network drive on the desktop? Or should I just keep it plugged into the desktop that will be using it to boot off of?

---

### Post by Inxsible on 2008-04-14
Your bios needs to be able to support usb boots or network booting capabilities.

The newer BIOS' seem to be able to do that. So if your rig is new, you should ne ok either way.

But I still am not clear about why you would want to connect it to the server and have her connect to the server before she can boot into Windows. If she is the only one needing Windows, then it might just be better to keep it on an external drive on her own machine.

Better still, why go with Ubuntu at all(at least for her machine), if using QuickBooks is her primary goal, she might as well use Windows for ease of use.

---

### Post by AndrewEsther on 2008-04-14
I think I will just keep it on her machine. It would be nice to keep in plugged into my server just so that it's out of the way and off of her desk and doesn't get turned off.

The user of this computer happens to be my mother, and she has a way of fouling up her computer within the first 3 minutes of a fresh reformat/reinstall of windows. I'm constantly having to do maintenance on her machine, and she has this ungodly love of downloading and installing everything that she sees online. I'm hoping that by using ubuntu I can 1. limit her to installing only things that I have a look at first and 2. not getting nearly as many viruses. I know that I can limit what she does with windows, but this usually just succeeds in pissing her off because if I make her account limited then it asks her for a password "every 5 seconds" and she "can do nothing productive" with it. WIth the dual boot, she can mess up windows all she wants and all I have to do is system restore without worrying about deleting her files.

---

### Post by Inxsible on 2008-04-14
> **AndrewEsther said:**
> ........ she has a way of fouling up her computer within the first 3 minutes of a fresh reformat/reinstall of windows. I'm constantly having to do maintenance on her machine, and she has this ungodly love of downloading and installing everything that she sees online. LMAO !!!!!!

She sounds like my mother ;) .

I had to reinstall Windows everytime i visited her. But she is on ubuntu now (thank God!)

---

### Post by AndrewEsther on 2008-04-14
hahaha :lolflag: good to see I'm not the only one who has to do this. I'm glad to hear that ubuntu will help with this.

how do I configure GRUB once I load ubuntu on there? (I'm doing the WinXP install on the usb drive right now, which means I'll be installing ubuntu in like 19 hours after it finishes *sigh*)

---

### Post by Inxsible on 2008-04-14
> **AndrewEsther said:**
> hahaha :lolflag: good to see I'm not the only one who has to do this. I'm glad to hear that ubuntu will help with this.

how do I configure GRUB once I load ubuntu on there? (I'm doing the WinXP install on the usb drive right now, which means I'll be installing ubuntu in like 19 hours after it finishes *sigh*)If you install Ubuntu after you install Windows, grub should be configured for you automatically.

It is very important however, to keep your External drive connected while installing Ubuntu, so that the Ubuntu loader can recognize the presence of another OS on the external drive.

---

### Post by AndrewEsther on 2008-04-14
oh okay sweet! and now one more thing I love about ubuntu :-)

so how hard is it to configure GRUB to boot from a network drive, assuming my BIOS can support it?

---

