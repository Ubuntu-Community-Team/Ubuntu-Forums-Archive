---
title: "[SOLVED] no adsl connection after using a wi fi hotspot"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2008-01-10
hi, i was wondering what would cause my adsl connection to not work after using a wifi hotspot at my local library. this hotspot has a managed connection where you register your e-mail address and a password to use it. the wifi connection worked awesome, but when i get home, my wired adsl connection doesnt work with ubuntu, but with windows vista (the operating system that came with my machine that i dual boot) the adsl connection works fine. this adsl modem is not a usb modem. the adsl modem is detected. i was using ubuntu when i was on the wireless network (since i hate vista). any ideas?

---

### Post by Blutack on 2008-01-10
Was the laptop asleep when you moved it or actually powered off?  If not, reboot it first.

---

### Post by thebestofall007 on 2008-01-12
> **Blutack said:**
> Was the laptop asleep when you moved it or actually powered off?  If not, reboot it first.
i found the problem: what happened is when i used the connection the primary and secondary dns server listings that my adsl service uses were deleted and replaced with the server address of the wifi hotspot. i didnt change any settings myself.  i used wifi radar to find the signal, connected to the ip address of the hotspot server, and when i tried to get on a page, it redirected my browser to the library's registration form for their wifi usage policies ; it seems to have happened after i had to register my name, email address and a password for records on that form. in the network settings, i had to get my primary and secondary server dns addresses off of the windows vista os i dual boot with as a reference and input them back into the dns section of ubuntu.

---

