---
title: "HELP w/ chrubuntu!"
date: 2013-05-11
forum: Any Other OS
---

### Post by pokeyflan on 2013-05-11
hi there:

I installed chrubuntu on my Acer 7 chromebook some months ago and have been happily using it ever since as the default OS ... until last night when my husband turned on my machine while i was in the other room AND hit the space bar, thereby taking it out of developer mode and into Chrome.

So here's my problem -- and my research into the online sources has not given me quite enough insight to quite figure this out for myself.

If I reset the developer mode (power button + F3 + Esc), will that reset the entire DRIVE (which is really my chrubuntu install) or just the chrome partition? Once I'm in dev-mode, will I ostensibly be able to boot back into the chrubuntu OS because the script pointing to it as the default OS is still there? And actually, how does one switch from OS to OS? (Without the crouton install) I'm guessing it's at the log-in but I don't actually know how to do that either.

I hope this is obvious to some kind-hearted reader out there. I can usually figure out what to do from the forum's excellent posts, but I'm stumped here.

Thanks! 
~chris

---

### Post by Perfect Storm on 2013-05-11
Moved to Other OS/Distro Support.

---

### Post by aysiu on 2013-05-12
I also had a tough time finding any *definitive* answers on whether getting into developer mode again would wipe an existing partition or just the ChromeOS partition. My guess would be that Google would make it so that going in and out of developer mode would take the device back to factory settings (so taking out the Ubuntu partition).

---

### Post by pokeyflan on 2013-05-12
Ayisu:

Thanks for your reply. I'm still researching all the internet sources that I can find. If it'll be helpful to others, I'll post what I eventually discover to this forum (sortof a modern morality tale!)

~chris

---

### Post by aysiu on 2013-05-12
Thanks, pokeyflan. I'd be curious to know, certainly, even though I use Crouton instead of a dual-boot.

---

### Post by pokeyflan on 2013-05-12
Well, I guess if I have to reinstall, I can try the crouton route instead of the dual-boot!

~chris

---

### Post by bro on 2013-05-15
Acoording to [this source]("http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/") (seems reliable) everything will be wyped.  
> 
When you disable Developer Mode, your Chromebook will clean everything up, restoring you to a clean, safe locked-down Chrome OS system and overwriting all the changes you&#8217;ve made to your Chromebook&#8217;s software.

---

### Post by pokeyflan on 2013-05-15
Bro:

Yeah, that does seem to be what I am finding in my internet searching. I was maybe hoping someone else has dealt with the same issue, but maybe not!

~chris

> **bro said:**
> Acoording to [this source]("http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/") (seems reliable) everything will be wyped.

---

### Post by mips on 2013-05-15
Make him sleep on the couch tonight :biggrin:

---

### Post by oldrocker99 on 2013-05-21
OK, something similar happened to me. When you get the angry "no OS found" screen, just keep hitting ctrl-d until you get the Developer mode? screen, then git it back into dev mode.

It worked for me...

---

### Post by avernw on 2013-11-22
I have been wondering the ***exact*** same thing. It looks like all the "wiping" mentioned by the previous posters does indeed happen, but _only _to the ChromeOS partition.  I did some experimenting after deliberately hitting the spacebar, and when it seemed all else had failed these steps (originally posted at [http://www.linuxbrigade.com/rescued-little-acer-c7-chromebook/](http://www.linuxbrigade.com/rescued-little-acer-c7-chromebook/)) did the trick:


[LIST=1]
[*]Turn off chromebook
[*]Remove battery
[*]Press power button to drain anything else out of the system
[*]Put battery back on
[*]Power on
[/LIST]

---

### Post by murt2020 on 2014-01-07
I had the same problem with the Acer C7 running Chrubuntu. After accidently hitting space bar at the bootup frowny face screen the acer exited developer mode and booted to Chrome os. When I changed back to developer mode (using power button + F3 + Esc) and rebooted I got the 'preparing system for developer mode window' for about five minutes and then it booted into Chrome os. At this point I tried the other methods mentioned here but none of them worked for me. 

Fortunately though, it turned the Chrubuntu installation hadn't been wiped, it just wasn't set as the default os anymore. 

To fix this i opended a shell in Chrome os using Ctrl+alt+F2, logged in with user name chronos (no password) and ran 
[FONT=Arial][B]sudo cgpt add -i 6 -P 5 -S 1 /dev/sda

[/B]When I rebooted Chrubuntu was the default os again[/FONT]:P.

---

