---
title: "Ubuntu 10.10: iMac 27&quot; i7: Mouse and Keyboard issue."
date: 2010-12-06
forum: Apple Hardware Users
---

### Post by jisaac on 2010-12-06
Just after the installation, Ubuntu detects the keyboard and the magic mouse (both working as previous versions). But after installing the ATI proprietary drivers, they don't work any more!?!?

Does someone manage to get them working on 10.10 with the ATI Drivers?

Thanks.

---

### Post by jisaac on 2010-12-08
Hi guys!

I can confirm this. If I boot in "Recovery Mode" my magic mouse and wire less keyboard work (partially) but if I boot in "Normal Mode" using ATI Drivers I lose them!?

Furthermore I'm not able to pair them, they appear and suddenly disappear in the "Bluetooth New Device Setup" wizard.

My Bluetooth icon disappear too...

Any idea? Someone experienced the same behavior?

Thanks.

PD: Uf! I still have to use another USB mouse and keyboard!

---

### Post by Old Codger on 2010-12-09
I have an iMac 21.5" and also have been unable boot Ubuntu 10.10 Maverick Meerkat in the normal mode after upgrading online because it doesn't seem to recognize either the Magic Mouse or the wireless keyboard. However, I am able to boot in the failsafe/recovery mode. Although neither the mouse nor the keyboard worked perfectly in Ubuntu 10.04 Lucid, they worked somewhat and I could boot in normal mode with no difficulty.

After thinking about this problem, I posted on a grub-related thread, thinking the boot/freeze problem might be a grub issue. Yet, after running line recommended line commands as a possible fix, I still couldn't boot in the normal mode. Another person suggested that it could be an issue with the Nvidia video card, but somehow they didn't make sense because I had no difficulties booting in 10.04 and can boot fine in the failsafe/recovery mode.

FWIW, I've also tried a clean install, etc., but when I boot, the log-in screen freezes and I'm unable to log-in as noted above. :confused:

---

### Post by arabis on 2010-12-09
You can install the Mactel PPA and install the packages "btusb-dkms" "bluetooth" and "blueman" for your bluetooth keyboard and magic mouse.

After that, in normal mode you have to pair them once with blueman to make them work. In normal mode you can use a regular mouse before you succeed to pair your magic mouse (code 0000). To pair your keyboard, use a virtual one (it is called "onboard") to write 1234 when blueman ask for code, and answer back with your bluetooth keyboard. Just make sure you make a shortcut on your desktop for "onboard" before, when you are in recovery mode.

It may be necessary to try many times before you succeed to pair the mouse or keyboard. Also, at login, it takes a few seconds after you press a key or clic the mouse before you gain the control of these devices.

---

### Post by jisaac on 2010-12-10
Hi arabis,

Ok, I'm now getting my magic mouse "working", far from OSX feeling but paired, thanks!

I'm still having problems with my keyboard. It is paired but only few keys are working. And it's like I have a BloqNum in the middle of it:
- If I press "u" I get a "4".
- If I press "i" I get a "5".
- If I press "o" I get a "6".
- etc.

I've tried to change the keyboard model but no way.

By the way, what do you mean by "To pair your keyboard, use a virtual one (it is called "onboard")..."?

Thanks.

PS: At login time, the keyboard works correctly, I mean the keys are mapped the right way...

---

### Post by arabis on 2010-12-11
> **jisaac said:**
> I've tried to change the keyboard model but no way.
By the way, what do you mean by "To pair your keyboard, use a virtual one (it is called "onboard")..."?

For keyboard model, I use "Portable Apple". To correct the mapping of your keys you have to specify the layout. You're getting numbers because you have, in some way, enable the numlock.

Open a terminal and write "onboard" without the quotes.

---

### Post by jisaac on 2010-12-12
Thanks arabis!

I had the numlock of the other USB keyboard enabled and it was clearly affecting the two ones! I disabled it and now everything works almost perfect ;)

I did not have to change my layout to make it work. Furthermore I could not find the "Portable Apple" Layout...
-> Do I have to install something else to get it?

Thanks.

PS: I don't mark this thread as solved because I'd like to make more tests with the magic mouse and this keyboard and configure them even better with your help guys...

---

### Post by arabis on 2010-12-12
"Portable Apple" is the model. You can specify your keyboard model just below the language layout.

---

### Post by jisaac on 2010-12-12
I have not the "Portable Apple" model. I'm using the "Macintosh" model and it works pretty well.

Thanks.

---

### Post by artik1024 on 2010-12-12
Hi jisaac. Since Maverick, I can't pair any BT devices. Impossible to pair my keybord for example. Default BT manager see it, but impossible to connect it. Same with my phone, all are rejected.

I tried to install "btusb-dkms" "bluetooth" and "blueman" ("btusb-dkms" doesn't exist) but that didn't helped me. Any help ?

---

### Post by jisaac on 2010-12-14
- Use the Mactel Support PPA to install "btusb-dkms" and try again. Boot first on OSX and make sure both of magic mouse and keyboard are paired. Then boot Maverick and try to pair them with "blueman".

- Pay attention to post #4 of aribis about the pairing codes.

---

### Post by arabis on 2010-12-14
+1 for jisaac

---

### Post by Old Codger on 2010-12-15
> **artik1024 said:**
> Hi jisaac. Since Maverick, I can't pair any BT devices. Impossible to pair my keybord for example. Default BT manager see it, but impossible to connect it. Same with my phone, all are rejected.

I tried to install "btusb-dkms" "bluetooth" and "blueman" ("btusb-dkms" doesn't exist) but that didn't helped me. Any help ?

I've also tried to install btusb-dkms. When I then tried to launch Bluetooth Manager, I received an error message. In short, this fix didn't work for me.

---

