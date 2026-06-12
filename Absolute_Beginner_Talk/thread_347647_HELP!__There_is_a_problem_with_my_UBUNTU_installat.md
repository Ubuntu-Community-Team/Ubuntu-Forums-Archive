---
title: "HELP!  There is a problem with my UBUNTU installation...!"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by mahdimc on 2007-01-27
:confused: Uh-OH!  I downloaded Ubuntu 6.10 and I checked the MD5 sums and they are correct...  When I started the PC in Microsoft Virtual PC 2004, the boot screen came up nice... with the ubuntu logo and under it the options (install ubuntu, safe graphics mode, etc.).  I picked 'install ubuntu' and then it gave me a weird screen!  It is filled with small pixels that are really spaced apart and the words are mashed together...  Can someone tell me what is wrong???  Please?  :confused:

---

### Post by Monkalou on 2007-01-27
I looked it up and this page ([http://vpc.visualwin.com/](http://vpc.visualwin.com/)) suggests the following changes for 6.0.6.  (This was the latest version they had notes on.)

Ubuntu 6.06 Desktop	-- Boot into "Safe Graphics Mode" and install normally	
Ubuntu 6.06 Server	  -- At Grub press ESC and edit the kernel line to include the option vga=0x314. To make it permanent edit /boot/grub/menu.lst

---

### Post by mahdimc on 2007-01-27
hmm... thanks, I'll try that.  I'll post back if it doesn't work...  and i'll also post back (but with three stars in a row) if it does work.

---

