---
title: "Pairing Apple Wireless keyboard (aluminum) using console in Jaunty"
date: 2009-07-13
forum: Apple Hardware Users
---

### Post by Fylke on 2009-07-13
I've successfully paired the Apple wireless keyboard to my laptop using a bluetooth dongle. The laptop is running Jaunty with bluez 4.23. However, when I attempt to pair the *same* keyboard to the *same* bluetooth dongle on my HTPC that is also running Jaunty, albeit a stripped version (it's running XBMC Live that uses a stripped Jaunty as OS) I can't get it to pair. And oh, it also uses the very same version of bluez.

So I guess what I need is someone holding my hand and telling me what the Bluez Gnome applet does behind the scenes that I can't reproduce on the command line (no fancy gnome applet in the stripped Jaunty of course).

What I've tried:
[FONT="Courier New"]hcitool scan[/FONT] -- Finds the keyboard okay
[FONT="Courier New"]sudo hcitool cc <MAC>[/FONT] -- Gives me a new prompt, just as if it succeeded pairing only I can't type anything

I also tried a lot of hidd solutions but since it works on the laptop that doesn't have hidd installed I'm that's not the way to go.

I also checked the [FONT="Courier New"]/etc/default/bluetooth[/FONT] settings file on the laptop after the pairing and it doesn't contain anything new. So I guess I should be able to get it to pair without modifying it.

How can I check if it has succeeded in pairing? [FONT="Courier New"]hcitool dev[/FONT] doesn't give anything on the laptop when the keyboard is paired.

---

### Post by asker on 2009-07-14
I am caving the same exact problem with my keyboard. Check and see if your caps lock key works after its "paired," mine doesn't. Its as if the keyboard just shuts off.

---

### Post by Fylke on 2009-07-15
> **asker said:**
> Check and see if your caps lock key works after its "paired," mine doesn't. Its as if the keyboard just shuts off.

Caps lock works fine when paired with the laptop (using the applet to pair).

I found where the bluetooth pairing data is kept (in [FONT="Courier New"]/var/lib/bluetooth[/FONT]) and I thought I'd try and copy that to my HTPC since the environment is exactly the same. It's worth a shot at least =)

---

