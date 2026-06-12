---
title: "CTRL+ALT+DELETE on G3 iBook"
date: 2006-06-14
forum: Apple PPC Users
---

### Post by scottlpatterson on 2006-06-14
I've installed Kubuntu Dapper 6.06 on my G3 iBook and it is working fine. However, when I connected to a Windows 2000 computer at my work via VNC using KDE Remote Desktop (krdc), it asked for me to press CTRL+ALT+DELETE to activate the login prompt. Whenever I press this sequence of keystrokes on my iBook keyboard, it restarts the X-server.

The CTRL and ALT keys appear to be mapped correctly as they report those keys in the prompt. While researching this issue, I believe I saw somewhere that the DELETE is actually the BACKSPACE key which explains the xserver reboot. Regardless if that is correct, I could not find what keystroke to press to activate the Windows login in krdc.

Is there a way to remap the DELETE key to actually be the DELETE key? Or maybe a different solution to get CTRL+ALT+DELETE to work???

---

### Post by aysiu on 2006-06-14
With VNC, you never actually *press* Control-Alt-Delete. You usually send the Control-Alt-Delete.

Try right-clicking on the top panel of the krdc window and see if there's an option to *send* CAD.

---

### Post by Slim Odds on 2006-06-14
[quote=aysiu]With VNC, you never actually *press* Control-Alt-Delete. You usually send the Control-Alt-Delete.

Try right-clicking on the top panel of the krdc window and see if there's an option to *send* CAD.[/quote] 
Yes, this is always true even when using two "Windows" machines.

---

### Post by scottlpatterson on 2006-06-26
[QUOTE=aysiu]With VNC, you never actually *press* Control-Alt-Delete. You usually send the Control-Alt-Delete.

Try right-clicking on the top panel of the krdc window and see if there's an option to *send* CAD.[/QUOTE]

Where is this at? There is a "Special Keys" menu option, but, that then presents me with a screen to press CTRL+ALT+DELETE. When I press CTRL+ALT+DELETE on my iBook keyboard (works fine on a PC keyboard) there, it reboots the X-server. I also tried right clicking on the menu bar with no success.

Any ideas???

---

### Post by aysiu on 2006-06-26
What happens when you press F8?

---

