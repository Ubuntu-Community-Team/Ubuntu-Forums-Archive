---
title: "Monitor going to sleep ... but is unable to wake up again"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by HilliBilly on 2007-09-27
When my monitor turns off after certain time of inactivity, it goes into sleeping state, saying "monitor going to sleep" but is unable to wake up. The computer is still working (i can SSH in), but moving the mouse or pressing a key will not turn on the screen.

Switching off and on the screen, monitor says "DVI: no Input Signal"

In Power Management Preferences I choose:
"Put computer to sleep when inactive for:  >NEVER"
"Put display to sleep when inactive for: >NEVER"

I searched the forums and found nothing what solves this problem.

Desktop PC: Feisty 7.04 (2.6.20-16-generic), Intel Core 2 Duo E6750, Gigabyte GA-P35-DS3, ATI X1950Pro, Monitor HP W2207.

---

### Post by roschell on 2007-09-27
I used to have similar problem. The screen turns grey, after while (one still can get in by moving the mouse), and after even longer time it gets black (from this black hole even mouse wont help, I have to close a screen for few seconds and then open it, this will bring me to grey screen and I am back on). All this works fine on my notebook, but I think you wont be able to do it practically with monitor.

Have to had a look at the screensaver preferences? 
system > preferences > screensaver 

Make sure you correctly chose the activation mode accordingly.

---

### Post by gwoodard on 2007-09-27
Hey i had the same problem but when i shut off ubuntu and restarted the computer it gave that "DVI-I no signal... i just now use a vga to dvi connector with a vga monitor its not the video card its the dvi cable or the monitor itself

---

### Post by kyphi on 2007-09-27
There are many reasons why a monitor goes to sleep as well as the inability to reawaken from sleep.

In some cases pressing Ctrl+Alt+Backspace will do the job.

It may be worth looking into the BIOS Power Management to adjust a setting.

You can also, with caution, look into your Power Management System in Ubuntu by typing 'xset' in a terminal to play with the settings there but make sure that you save it first.

You could also disable your screensaver to see if it has any effect.

Check if the fan on your graphics card is working.  Perhaps it is getting too hot and shutting the card down.

Also check that all cards are fully seated and check that memory boards are fully seated and locked.

Whatever the cause, I think that it comes from your computer.

BTW, a very good description of your monitor fault.

---

### Post by HilliBilly on 2007-09-28
switched over to gutsy this night, problem seems to be gone. wakes up from black screen now.

only thing i changed: in bios i disabled on-board LAN (read something that this could make trouble on a dual boot machine having a RTL8168 or RTL8169 ethernet NIC driver).

[http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

---

### Post by kyphi on 2007-09-28
Disabling 'wake on LAN' is a good idea, I believe.  When my computer is off I want it to stay off.

I assume that the ethernet controllers are the motherboard inbuilt ones.  Mine are disabled ... I prefer a separate ethernet card.

Pleased to read that your monitor problem has been resolved.

Cheers

---

### Post by HilliBilly on 2007-09-28
yes, the RTL8169 ethernet controller is the GA-P35-DS3 motherboard inbuilt one. i have a D-Link System Inc DGE-528T Gigabit Ethernet Adapter card which is working fine.

---

