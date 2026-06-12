---
title: "GRUB Dual Boot problem with XP Pro"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by loswr86 on 2007-02-26
Hello all,

I spent my entire sunday attempting to correctly partition and set up a dual boot machine with edgy eft and MS xp pro. After many attempts, I believe I have the system set up properly, but I'm having a problem with the grub boot menu. The keyboard arrows do not work. infact no keys work with the grub screen, and now that I think of it, the edgy live cd menu screen the enter key didn't work either. I have a MS keyboard. After the time out at the grub screen, ubuntu launches fine and everything works as expected (I think). If someone will point me in the right direction I would appreciate it.

---

### Post by ramzai on 2007-02-26
Look for a BIOS setting named "USB keyboard support" or something like that. A friend of mine had a similar problem (not in grub, but in a windows bootloader), and that solved the issue.

Also, does your keyboard works fine in BIOS menu?

---

### Post by ~chinook~ on 2007-02-26
Wireless keyboard problem would be my guess.

---

### Post by loswr86 on 2007-02-26
Keyboard is not wireless, and it works fine in the bios menu. Still searching...

---

### Post by rplantz on 2007-02-28
> **loswr86 said:**
> Keyboard is not wireless, and it works fine in the bios menu. Still searching...

I'm having the same symptoms. If I connect my keyboard (MS Natural Keyboard Pro) to the PS2 port, I can use the arrow keys in the grub menu. But they don't work going through usb. After the timeout, everything works just fine.

Edit: I figured it out (on my system). I had to change a setting in my BIOS. On my system there is a BIOS item called "Integrated peripherals." I changed "USB Keyboard Support via" from "OS" to "BIOS".

---

### Post by old_geekster on 2007-02-28
If you have doubts about your install, here is a great guide for you to follow:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I have used it for help several times.  I have done 11 clean installs in the past three weeks, due to my desire to tweak too much.

---

### Post by loswr86 on 2007-02-28
Thanks for the info fellas. I'll check my bios when I get home.

---

### Post by loswr86 on 2007-02-28
I am an IDIOT. Do you think that plugging your ps/2 keyboard to a ps/2-->usb coverter, then into a off brand usb hub, then into your computer might prevent grub from recognizing it? The answer is yes. Thank's for opening my eyes to the obvious problem. 

If it was a snake....

---

### Post by rplantz on 2007-03-03
Benn there, done that many times. :)

It's known as an ID ten T error. (Write ten in numerals.)

---

### Post by highdef on 2007-03-27
I had the very same problem--just solved by Bios-Advanced-USB configuration-Enable Legacy USB Support. Thanks to previous posters for pointing out the right direction!

---

