---
title: "problems restarting ubuntu +snow leopard"
date: 2009-10-08
forum: Apple Hardware Users
---

### Post by andrew markworthy on 2009-10-08
I'm not v.computer literate, so please be gentle with me ...

I loaded ubuntu onto a MacPro 17 inch to run alongside Snow Leopard. I followed the download instructions on the ubuntu site and on loading from the ubuntu disc and ubuntu appeared to load correctly. BUT: on closer examination, there are problems:

(1) if I switch the machine on and press nothing, the machine boots up as ubuntu by default
(2) if I switch on the machine and press the ALT key, the machine offers me the choice of Mac or Linux
(3) Mac and Linux work appear to work fine by themselves. However:
(4) If I restart when using Mac, unless I also press the ALT key down, the machine restarts as Linux (and if I keep ALT pressed down, I get the choice of Mac or Linux)
(5) If I restart when using Linux, the machine freezes

My gut reaction is simply to delete *everything* on the disc (I have all my stuff backed up) and re-install Snow Leopard from scratch, running Linux from a memory pen. However, Linux appears to be stuck solid- I can't remove the Boot Camp partition nor can I delete LInux. 

Help!

---

### Post by mocoloco on 2009-10-08
Everything but #5 is normal, the system will default to booting in to Ubuntu every time, and if you want OSX you'll need to always press Option(Alt).  If you want to change it to boot OSX by default you will need to boot in to Ubuntu, then change the boot order in Grub.  This can be done manually in a config file but the easiest way is to install Startup-Manager.  Go to Applications -> Add/Remove, and search for "startup". After installing it, you will be able to choose the default operating system.

For your #5 issue with Ubuntu freezing when you shut down, next time you do a shut down or restart, when you see the Ubuntu logo press Ctrl+Alt+F2, which will switch to showing you text as it shuts down. Post the last thing it gets stuck on, that may give a clue as to what's going wrong.

---

### Post by andrew markworthy on 2009-10-09
Many thanks- will try these suggestions and get back.

EDIT: sorted!

---

