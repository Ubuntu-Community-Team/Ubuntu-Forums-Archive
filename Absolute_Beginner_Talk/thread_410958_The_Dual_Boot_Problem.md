---
title: "The Dual Boot Problem"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Harkainos on 2007-04-16
Like a goon and excited kid at christmas when he gets a toy - I installed Ubuntu with the intention of duel booting the system. I completely didn't make a backup of my system.... DOH....

The duel boot works... but it is unresponsive to my keyboard. It is a gaming keyboard and I am thinking that is the problem. Do I need to get a joe schmo keyboard?

---

### Post by taurus on 2007-04-16
Is it an USB keyboard by any change?

---

### Post by Harkainos on 2007-04-16
It is a usb keyboard (made by saitek) I hooked up the ps2 adapter and it is still unresponsive. IIRC Ubuntu loads only legacy drivers during the post process.... could this be the issue. Maybe my keyboard isn't a legacy keyboard...

Has anyone else had this problem? Should I just get a 15$ keyboard?

---

### Post by Terl on 2007-04-16
I use a usb keyboard also and had no issues with that.  It may indeed be the gaming keyboard is not recognized.  I always have a spare keyboard around...just in case :)   just as I have a couple spare mice too.

You may have to get a cheap keyboard so that you can at least get into the o/s and then you can work on getting the Saitek configured.  oh, the adapters don't work very well for keyboards.  I have a laptop for work and it will only take usb  and the IT dudes only had ps2 keyboards.  No adaptor worked. I had to get a usb.

---

### Post by rillip on 2007-04-16
My USB Microsoft keyboard (yeah yeah... flame all you want, it's a $#@%@ awesome keyboard!) was detected without issue - HOWEVER, while it would work in both Kubuntu and Windows, it did NOT work in Grub.  I'm a little unclear if you are having this same issue, or if even once booting to Linux it's not finding your keyboard.

What I had to do to resolve my problem was go into my Bios and change it to say "USB Keyboard support: BIOS" (as opposed to OS/Off).  After that, I got it working without issue in Grub, Linux and Windows.

I'm sure someone with more experience will be able to tell you how to force the detection, however, having an el cheapo model you can type the commands with would probably be prudent, if the above suggestion doesn't help.

---

### Post by Harkainos on 2007-04-16
@ rillip: thank you. that bios setting did the trick.

Now... when i try to load windows it stops at a black screen that says 'loading windows' (DOS style) Any ideas?

---

