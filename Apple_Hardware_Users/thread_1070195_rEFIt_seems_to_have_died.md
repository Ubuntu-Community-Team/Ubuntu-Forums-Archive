---
title: "rEFIt seems to have died"
date: 2009-02-14
forum: Apple Hardware Users
---

### Post by spencercarran on 2009-02-14
I run a MacBook 3,1 (Santa Rosa) triple-booting OS X Leopard, Windows Vista, and Ubuntu 8.10 64-bit. I primarily (almost exclusively) use Ubuntu.

I was in OS X for a little bit today, not doing a whole ton. The only major thing I can think of that I did was uninstall Symantec antivirus (pointless in OS X, and a bloated pig that kills performance) and when I later tried to reboot into Ubuntu, instead of giving me the rEFIt boot menu as it normally does it went straight into the OS X boot process. This happened again on the next reboot (I have previously had times where rebooting from OS X bypassed rEFIt) and on the third try I hit the "option" key and got the Mac/Windows option that BootCamp provides. Selecting "Windows" got me into Ubuntu. Vista does not seem to be accessible, but I'm not too concerned about that right now.

My question is: can I, from inside OS X, reinstall rEFIt without seriously screwing something up in my current tri-boot configuration? Also, does anyone know why rEFIt would suddenly have vanished for no apparent reason? As I said, the only thing I did (other than routine stuff like web browsing) in OS X was to get rid of Symantec, and it seems surprising that their uninstaller would affect rEFIt at all.

---

### Post by pxwpxw on 2009-02-14
> **spencercarran said:**
> 

My question is: can I, from inside OS X, reinstall rEFIt without seriously screwing something up in my current tri-boot configuration? Also, does anyone know why rEFIt would suddenly have vanished for no apparent reason? As I said, the only thing I did (other than routine stuff like web browsing) in OS X was to get rid of Symantec, and it seems surprising that their uninstaller would affect rEFIt at all.

Quite safe to do a full auto install of rEFIt which should reinstate it,
or you could just run the "eneble-always" refit cli command. 
The OSX housekeeping just resets to OSX as the startup.

---

