---
title: "unable to detect display and video adapter"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by astoroth88 on 2008-04-13
I tried out ubuntu 7.04, great OS, but i'm into gaming and couldn't find a way to support directx or any of my games. I downloaded 7.1 recently and decided to try it out again, but when i boot from cd and install, it gives me an error that it can't detect my display drivers and when i click configure or continue it always brings me to a DOS screen, does a couple checks that say OK and just stops till I cancel it and restart the pc.     Here are my PC specs:  AMD Athalon64x2 2.0ghz dual core, 1gb RAM, Nvidia GeForce 9600GT 512mb DDR3 memory, Creative LIVE! internal Soundblaster 24-bit, Linksys NC100 Faster Ethernet Adapter (a card, not integrated), and a 160gb Sata-300 7200 RPM Hard Drive.   I have 2 partitions, 80gb reserved for my XP Pro which I'm on at the moment, and 70gb raw partition reserved for ubuntu when i can get the installer to work properly.  XP Pro works completely fine w/ no errors what so ever, but I try the first Option (Run/install ubuntu) when i boot from CD and it gives me the display error and goes to DOS and stops reading the disc.  I will try to get this to install on my own, but any insight on this would be much appreciated.  Also, is there any way to run my PC games such as Dawn of War and guild wars, or Emulators (Basically any .EXE based programs) and Direct X 9.0c (possibly dx10) on Ubuntu?

I know that this worked fine in 7.04 with my GeForce 7300 GT, and had no issues w/ my ethernet adaptor, only reason i ceased from using it was that I couldn't get any games or directx to work properly.

Thanks for any help in advance :)

---

### Post by Duckyspetrie on 2008-04-14
You can run Guild Wars in Wine. Not sure on any of the other stuff though.

---

### Post by NightwishFan on 2008-04-14
Try wine.
```
sudo apt-get install wine
```

Also what you are trying to do is run Playstation games on an Xbox, Linux is not Windows. Also DOS is Microsoft.

---

### Post by astoroth88 on 2008-04-14
well, I was just asking if there was a way to run emu's on ubuntu, but i can't try anything, i can't install because it doesn't recognize my display driver or some stuff. That's my main issue at the moment.

---

### Post by NightwishFan on 2008-04-14
Try the alternate install cd, also make sure you did not burn with errors.

---

### Post by astoroth88 on 2008-04-14
Just burned a new install cd, same error.

Does ubuntu not support 9600 GT?

---

### Post by NightwishFan on 2008-04-14
Also did you try safe graphics mode? I meant to use the "alternate install cd" not an alternate one. :)

---

### Post by astoroth88 on 2008-04-14
oh lol my bad, didn't read into that too well i suppose. I clicked on always use safe mode and clicked on continue and it just went into that screen again and stopped readin the cd as it has been doing.

---

### Post by NightwishFan on 2008-04-14
Move over safe graphics mode, press other options, "f6" I think, and remove quiet and splash. Then push enter and tell me what you see, and if you get anything that seems like an error.

---

### Post by astoroth88 on 2008-04-14
I'll try that now, thx

---

### Post by astoroth88 on 2008-04-14
Installed just fine, thanks, now i just gotta remember how to work this lol. first on the list is whine

---

### Post by NightwishFan on 2008-04-14
Of course any help you need, I will try. If you mean wine, then:
```
sudo apt-get update && sudo apt-get install wine
```
When thats done run:
```
winecfg
```
Then autodetect drives and configure all the tabs right.

---

