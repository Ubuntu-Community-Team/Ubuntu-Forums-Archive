---
title: "Install ubuntu on Power Mac"
date: 2011-03-01
forum: Apple Hardware Users
---

### Post by jfla on 2011-03-01
I've been trying to install Ubuntu 10.10 on my Power mac g4 and it won't boot from it.

I burned the cd and put it in the drive. After some googling I discovered that you have to open the mac up and change some jumpers on the cd drive. I can't do this because I might break it. I have a usb drive so I plugged it in and switched on. I pressed the option key and it displayed the drive. I clicked on it and the screen suddenly went blank. Then it came back on to the boot menu like it was before but the writing had gone fuzzy and the cursor had changed colour. I tried open firmware and it said: "method <load> not found" and lots of other stuff.

Could someone help me?

---

### Post by jfla on 2011-03-01
The command I used in open firmware was: "boot usb0:,tbxi".

---

### Post by linuxopjemac on 2011-03-01
I can recommend MintPPC.

---

### Post by jfla on 2011-03-01
I would prefer to use Ubuntu.

---

### Post by linuxopjemac on 2011-03-01
Why don't you boot from a USB stick?

---

### Post by jfla on 2011-03-01
I will decide after I see the speed of Ubuntu on a g4.

---

### Post by jfla on 2011-03-01
Whats wrong with booting from a cd?

---

### Post by jfla on 2011-03-01
I'll try booting from a usb stick.

---

### Post by jfla on 2011-03-01
Plugged in...

---

### Post by jfla on 2011-03-01
I can't burn the iso file onto it for some reason.

---

### Post by jfla on 2011-03-01
Trying dd.

---

### Post by jfla on 2011-03-01
Still writing...

---

### Post by jfla on 2011-03-01
Yessssssssssssssssssssssss!! It worked. Thankyou so much!

---

### Post by linuxopjemac on 2011-03-01
no problem...enjoy.

---

### Post by flatlined on 2011-03-06
Did you run it off of USB? How do you go about doing this? I have a eMac G4 PowerPC and can't get it to boot from USB.

Thanks

---

### Post by linuxopjemac on 2011-03-06
To know how to boot off USB, see installation instructions MintPPC...

---

### Post by teachop on 2011-03-06
Beside the point now... but on the Mac if you hold "C" key while powering up it will boot the CD (or DVD) in the internal drive.  Works for Ubuntu 10.10, that is how I did it on an eMac.  Next time I need to do this, I will try the USB method too, saves the DVD.

---

