---
title: "blacklist? still having disastrous wireless problems..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by noobbutnotboob on 2007-06-23
I'm trying to run blacklist from terminal to kill a driver that I think is blocking my wireless. Funny thing is that lshw lists my driver as acx_pci. If I try to remove that driver it says module not found'. When I try to blacklist it, it says "invalid operation blacklist". If I try to gedit etc/modprobe.d/blacklist, it will open and let me type in the change, but open "saving and closing" it says "file not found". 

Ndiswrapper, etc, is installed, as is the wpasupplicant.

Arg!  :mad: I need to get this up and running by work Monday morning or I'm gonna have to reinstall windows xp (!).

BTW there are two other threads from yesterday about this, so this is the one with my latest efforts given where I am at today in this process. 

I am running 7.04, have a Netopia (Motorola 802.11b) 3D reach, have installed the 3rd party linux driver, and although it all says I am connected the net, I cannot pull up anything. 

Anyone have any ideas?

---

### Post by diatribe on 2007-06-23
have you tried installing wicd? it worked for me and it cant hurt to try.  wicd.sourceforge.net

---

### Post by noobbutnotboob on 2007-06-23
tried to install wicd as suggested, but getting an error message "conflicting packages - not installing wicd"

?????

---

### Post by diatribe on 2007-06-23
oh you have to remove network manager first, check the install page at the site

---

### Post by noobbutnotboob on 2007-06-23
hi! thanks for the reply!

I removed network manager and rebooted (hard). But I still got the same message. So I went a little off and uninstalled ndis* and all the other things I had unpacked/installed in trying to fix the wireless problem. Rebooted again only to get the same error. 

Honestly, I am pretty fed up with this issue and am killing the disk right now for a clean installation of *something*... whether I give Ubuntu another chance is in the air as everyone and their brother seems to have a problem getting the wireless going on Feisty. Gosh I am just so super-frustrated with it all right now I'm not sure that I even want to waste more time trying another full OS install only to find that the wireless still doesn't work despite trying everything in the forums and in the guides. I can't take the chance that I might get pissed and chuck my laptop in the pond. :P

Somebody save me, I don't wanna go back to Windows!

---

