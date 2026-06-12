---
title: "Keyboard not working"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Gillette on 2007-12-31
I installed 7.10 on an old Gateway computer about 4 weeks ago. Yesterday was the first day I used the computer extensively (storing pictures). Today when I turned it on, it froze up at a certain point--when the line fills up across the screan left to right. I had to shut it off and when I restarted I had no mouse and no keyboard. I rebooted it a couple times with no improvement. When I changed to a usb mouse I did get mouse control but still no keyboard. I tried two different keyboards as well as two different ps2 mice. Any suggestions on how to get this thing to work again?

---

### Post by mattismyname on 2007-12-31
I'd check to make sure the keyboard is detected by the BIOS.  Also, check in the BIOS settings to make sure it is enabled.  Make sure you've flashed the latest BIOS for your mobo.

If your keyboard is usb, try a ps/2.  If it is ps/2, try a usb.

---

### Post by tgalati4 on 2007-12-31
Clean the dust out of the machine.  You may have dust bunnies that are shorting the important bits.

---

### Post by Gillette on 2007-12-31
Both keyboards are ps/2 and the one I was using yesterday worked fine. I went into bios and am able to use arrow keys etc. 

I'll give it a good dusting. I've got a can of air. Last time week when I opened it up it did look rather dusty.

---

### Post by Gillette on 2008-01-01
I blew out the dust and started the computer. It works fine now. It did go through some sort of test. Message said something about a forced test because of 20 mountings. Anyway whatever the test was, it passed. Thanks for the suggestion.

---

### Post by tgalati4 on 2008-01-03
Linux will check the file system (sort of like Microsoft scandisk) every 20 to 30 boots.  You can change this to 50 or turn it off if you want to.  It basically tunes up the file system between long stretches of time.  In your case, sounds like you were booting a lot due to a hardware problem.  One of my machines was up for 217 days before a power outage forced a controlled shutdown.  So checking the file system every 20 boots is not a bad idea.

I'm glad you got your system working again.  Linux is not really tolerant of bad hardware.  That's one advantage Windows has, it doesn't really care if you have wonky hardware.

---

