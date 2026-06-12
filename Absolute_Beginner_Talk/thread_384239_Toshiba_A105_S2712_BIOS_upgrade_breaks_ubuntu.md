---
title: "Toshiba A105 S2712 BIOS upgrade breaks ubuntu"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by bobreeves on 2007-03-14
Greetings:

Wanted to share a recent experience with 'upgrading' Toshiba bios on an A105 S2712 laptop. This is an Intel based laptop with onboard 2200BG wireless. I have had Ubuntu 6.10 Edgy with Beryl and VMWare server (with XP guest) working for about a month. I'm setup to dual boot Ubuntu and XP. Trying to wean myself off Windows, but still need the dual boot for some work related stuff (VPN to MS 2000 Server and office workstations), as well as some multimedia stuff that just works better and faster in native XP than in a virtual machine. 

Never satisfied to leave well enough alone, I checked Toshiba's website yesterday and discovered there was an 'upgrade' available for my bios - from V1.7 to V1.8. It was supposed to allow me to run Vista (which I had tried previously and failed) - so I thought I'd load it in case I wanted to attempt Vista again. Anyhow, the bios update (from Windows) completed OK. When I rebooted - 1st into Windows, everything was fine. Next I rebooted into Ubuntu - and that's where the problems began. (My initial install was from the LiveCD which detected all my hardware - including sound and wireless - without any problems).

Ubuntu came up to the logon screen with the logon sound playing repeatedly. When I logged in, the display manager never started - just a blank desktop wallpaper and mouse cursor. I logged out and back into the terminal to look around (logon sound still playing over and over) and NO WIRELESS. I assumed I had an IRQ conflict problem, but was unable during the day to find a solution. Booting from either an Edgy or Feisty CD produced exactly the same behavior. 

I'm just too new to know where to start to fix this. I figured the easiest way would be to downgrade the bios back to V1.7, but was concerned as there was a prominent notice on Toshiba's site that you COULD NOT go back from V1.8 to any previous version. I called Toshiba tech support, and basically they responded with Linux? <click>. I called a local Toshiba repair facility and spoke with a tech, who gave me the same advice - and said the only way I might be able to downgrade the bios was with some 3rd party utility, and the he didn't recommend it. I did read that someone had downgraded another Toshiba model using a boot CD, so figured I'd give that a shot - and it worked perfectly. Actually - I booted the CD to see what choices there were - and it just flashed the bios then turned off the machine without any question or intervention. 

Anyhow - wanted to share this in case others have experienced Ubuntu breakage as a result of bios upgrade, and also to ask how I could have fixed this any other way besides downgrading bios, as I'd still like to at least look at Vista, although I'm certain I don't have enough horsepower in this laptop for decent performance.

Look forward to hearing from those with more experience!

Thanx

---

### Post by ThrobbingBrain66 on 2007-04-01
I had the same experience with my toshiba a few months back.

[http://www.ubuntuforums.org/showthread.php?t=361066](http://www.ubuntuforums.org/showthread.php?t=361066)

---

### Post by fasttimes on 2007-08-02
.

---

### Post by asmoore82 on 2007-08-02
never do a BIOS update unless there is some fix that you desperately need.

---

### Post by fasttimes on 2007-08-03
> **asmoore82 said:**
> never do a BIOS update unless there is some fix that you desperately need.
Agreed, but in this case, v2 fixes the brightness control not working. :(

---

