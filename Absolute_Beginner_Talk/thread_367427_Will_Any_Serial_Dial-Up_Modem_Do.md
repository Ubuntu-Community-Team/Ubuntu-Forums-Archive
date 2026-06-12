---
title: "Will Any Serial Dial-Up Modem Do?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by IronMac on 2007-02-22
I am wondering if any serial dial-up modem will work? I have an old USRobotics serial modem for Mac and I was wondering if I can use it? Thanks!

---

### Post by ^rooker on 2007-02-22
External, serial modems (classic 56k...) should work like a charm with any linux flavor, since all the logic is in the modem - no driver or something needed.
(Note: The modem will not show up anywhere as connected hardware)

I've been using almost only USRobotics with linux and never had problems. 


If I remember correctly (sorry, it's been quite a while since I've configured dialup on linux), you only need "pppd"(for handling the connection) and "wvdial" (for dialing and talking to the modem).

If you search for "linux dialup howto" or "dialup wvdial" either in google or here in the forums, you will find a lot of information of how to set things up.

Good luck!

---

### Post by IronMac on 2007-02-22
Thanks ^rooker for the good news! I am assuming that my T20 uses a Winmodem inside so it would have been great to be able to use this old USRobotics 56.6k modem.

---

### Post by ^rooker on 2007-02-22
yikes! Winmodem.... 
Yeah, you better stay away from them. (I'm so happy that this AMR slot became extinct!)


Good luck!


btw: 
With an external modem you can have A LOT of fun! If you have a USRobotics Voice/Fax modem, they have internal support for handling stuff, like audio - In combination with "festival" & "vgetty" you can call your computer and let it speak to you... (no need to connect soundcard with modem) - if you're interested I can provide more details, since I did that once.

Additionally: If you have even more time to waste, check out the datasheets for USRobotics AT-modem commands... there is some interesting stuff inside that box (like room-monitoring using the built-in microphone, etc...)

---

### Post by IronMac on 2007-02-22
LOL! I think I will stick with just making sure it works as a dial-up modem for those times when I am stuck at my parent's place. I was there in late December for almost a week and my T20's WinXP install had gone kablooey. **NO** Internet for a week!  :mad:

Thanks for all of the info!!!

---

### Post by ^rooker on 2007-02-22
you're welcome.
(damn! you reminded me that I wanted to play with the old analog-modem again.... and I'm currently short on time and far away from it. thank you!) ;)

---

