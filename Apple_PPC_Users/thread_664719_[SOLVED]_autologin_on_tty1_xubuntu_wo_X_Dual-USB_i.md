---
title: "[SOLVED] autologin on tty1 xubuntu w/o X Dual-USB iBook"
date: 2008-01-11
forum: Apple PPC Users
---

### Post by curly_nostrill on 2008-01-11
Ok, this may be a shot in the almost dark since ppc is dying but here goes.

I'd like to have my user autologin on tty1 at startup.  I tried the well known how-to thread  [here]("http://ubuntuforums.org/showthread.php?t=31310") but most of the steps are quite outdated for Feisty.  I couldn't get it to work even substituting editing /etc/event.d/tty1 instead of /etc/inittab which doesn't exist in Feisty.  It seems there are other differences with PPC Feisty on top of that which I can't figure out.  I also don't want to start X automatically as that how-to wants to do.  I disabled gdm in "Services settings" and that works great so if I want X I still have the option to ```
$startx
``` on one of the tty*.

Ultimately, my goal is to autologin on tty1 and autorun "ncmpc" on that vt at bootup making this basically an embedded device yet still retaining other capabilities in case they are desired at some point.

**_I'm hoping someone has the perfect suggestion.  It can't be that complicated... can it?_**


notes:
Xubuntu runs considerably better than OS X 3.9 on this 600mhz iBook .  Without GDM and X it runs even way better staying cool with plenty of ram leftover for contingency and/or other programs.  The laptop was boiling hot with OS X and was pretty much unusable for anything beyond just looking at the finder and cocoa. Apple has updated iTunes to a practically unusable state for this machine.  

Aside from the initial resolution problem for X on Feisty this seems to be the best install so far where most everything just works.  I did ```
$sudo nano /etc/X11/xorg.conf
``` and commented out (added # at line beginning) the subsection under ' Section "Screen" ' which allows 'Depth 24' for 1024x768.  This display does not support such resolution ergo the whacky screen.  Then when installing the changes are saved to the install!  

MPD also works fantastically (only locally so far -- can't connect from remote but that's for a different thread) with music on an NFS mount through wireless to a [FreeNAS]("http://www.freenas.org/") file server.

If I need a quick graphical web session I can ```
$links2 -g
``` and links2 comes up on tty7 in framebuffer.  If I don't need the graphics, it's links2 on the same or different tty.

Ideally, I'd also like to take that fully functional install + config and make a live-CD ala Geexbox for when the hard drive ultimately dies.  I already have another identical iBook with a dead HD and it's a real pain to r&r the internal disk

---

### Post by curly_nostrill on 2008-01-12
Problem solved by installing mingetty with [FONT="Courier New"]sudo apt-get install mingetty [/FONT]Then edited /etc/event.d/tty1 to run mingetty with the autologin command.  

So simple, so eeesy, papi.

---

