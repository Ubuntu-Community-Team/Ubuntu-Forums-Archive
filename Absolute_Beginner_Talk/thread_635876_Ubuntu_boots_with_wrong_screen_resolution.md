---
title: "Ubuntu boots with wrong screen resolution"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by stueycaster on 2007-12-09
I'm dual booting Ubuntu 7.10 AMD64 and Windows XP Pro x64 Edition. After I use Windows for a while then switch to Ubuntu it restarts with the wrong screen resolution. I have it set to use 1152x864. It boots up with 1280x1024. Then if I reboot again it comes up with the right resolution. Does anybody know how I can fix this?

---

### Post by Balvinder25 on 2007-12-09
try this..
open terminal
type gksu nautilus
browse to /etc/X11/
search for xrog.conf file
open using gedit

now browse to teh location where it shows all the display modes that ur monitor supports...

now delete all the modes before the one u need..eg if u need 1024*768 u would have afew other modes before this line ..

delete all the others before this mode..

like u would have some thing like this//

  (  xxx*xxx )   1021*768   800*600

delet the xxx*xxx mode and dont delete the one after 

regards..

---

### Post by stueycaster on 2007-12-09
OK I did what you suggested. I rebooted to Windows and back and it came up right. Thank you.

---

### Post by stueycaster on 2007-12-26
> **stueycaster said:**
> OK I did what you suggested. I rebooted to Windows and back and it came up right. Thank you.

I was wrong. I guess it takes more than just a reboot for it to change. If I stay on Windows for a while or maybe because of booting Windows more than once it changes. Is there anything else I might try to fix this. The 1152X864 setting is the only one I've tried that doesn't run icons off the edge of my screen. Besides that I like it.

---

### Post by philinux on 2007-12-26
Install and run startupmanager from synaptic really nice gui. One of the things you'll see on the screen is boot resolution.

---

### Post by stueycaster on 2007-12-26
> **philinux said:**
> Install and run startupmanager from synaptic really nice gui. One of the things you'll see on the screen is boot resolution.

If I don't keep that set to 800X600 the Ubuntu startup splash screen doesn't show. Besides there is no setting for 1152X864.

---

