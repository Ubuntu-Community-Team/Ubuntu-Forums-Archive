---
title: "Keyboard press causes mouse pause"
date: 2007-04-05
forum: Apple Intel Users
---

### Post by allesfresser on 2007-04-05
Hello everyone.  I have a strange annoying anomaly with my Core 2 Duo iMac, running Feisty (updated to today's changes--5 April '07).  The machine is running Feisty just fine and dandy, except for one little glitch:  whenever I press an actual key on the keyboard (not a modifier key such as Shift or Option), the mouse freezes for about half a second, then zips over to where it should have been.  In other words, the mouse events are being received but their processing is paused for that short time.  This is of course a USB mouse and keyboard (no other option on this machine), and I have tried isolating it in quite a few different ways:  different keyboard; different mouse; plugging mouse into keyboard vs. directly into machine; changing X video driver (from fglrx to vesa and back); disabling Wacom et. al. drivers in xorg.conf.  Just now I stopped the X server entirely ("sudo /etc/init.d/gdm stop") and installed gpm (the console mouse daemon) just to see if it would happen without X running at all, and it does.  So it's something happening deep in the keyboard/mouse handling before it ever gets to X, possibly an interaction in one of the USB drivers.  But I am loath to go kernel-debugging at the moment--no luxury of time to spend trundling through "make menuconfig".

Anyone have any recollection of something similar, and any solution?  The USB controllers are Intel ICH7 if that helps any.

---

### Post by Michael_RP on 2007-05-23
I have a similar problem. I installed ubuntu 7.04 a month ago and I thought everything went fine, not until yesterday afternoon when I installed and played warsow. Whenever a hit something on the keyboard(except ctrl, shift) the mouse would freeze and the cursor would jump to where it should be pointing. The cursor would'nt moved untill I let go of the keyboard. 

I'm using an i386:  Intel Core 2 DUO, Nvidia Geforce 7300 GT,  1 GB ram, a4tech USB mouse with p/2 adapter and a4tech p/2 keyboard.

 Is there any way to fix this?

---

### Post by Ilove2023 on 2007-05-23
You just have to edit the file "/etc/default/mouseemu" and put 0 replacing 300 in the line  "TYPING_BLOCK="-typing-block 300"".

After that, you restart mouseemu (/etc/init.d/mouseemu restart)

---

### Post by Xavier Oddmon on 2007-09-12
Alright, I adjusted this, put it at zero, one, and (just to see if anything was changing), 5000. I did save over the original file, and after restarting the mouseemu program or even rebooting, there was no difference any of the three times. Please help, i'd love to be able to play quake without a joystick.

---

### Post by cyberdork33 on 2007-09-12
> **Xavier Oddmon said:**
> Alright, I adjusted this, put it at zero, one, and (just to see if anything was changing), 5000. I did save over the original file, and after restarting the mouseemu program or even rebooting, there was no difference any of the three times. Please help, i'd love to be able to play quake without a joystick.
did you uncomment the line?

---

### Post by arcticblue on 2007-09-13
Just wanted to say I was having this exact issue on my Core2Duo Macbook Pro.  Made WoW a little difficult.  Uncommenting that line in /etc/default/mouseemu and changing the value to 0 did the trick.  

BTW, this has been fixed in Gutsy (as well as the annoying vesa problem that should have been fixed a long time ago).  I'd say that Gutsy is in a completely useable state for those feeling adventurous enough to try it.  The support on Macs is much better (although you still need the svn madwifi drivers for Macbook Pros, but that's easy to set up).

---

### Post by Xavier Oddmon on 2007-09-14
> **cyberdork33 said:**
> did you uncomment the line?

...wow. *slaps self in face*.

With that out of the way, removing the comment works perfectly. Thanks.

---

### Post by cyberdork33 on 2007-09-14
> **Xavier Oddmon said:**
> ...wow. *slaps self in face*.

With that out of the way, removing the comment works perfectly. Thanks.
It's the simple things in life.

---

### Post by shinepuppy on 2007-09-27
Thank you, Thank you, Thank you!! This was driving me friggin nuts ](*,)

---

### Post by fatalGlory on 2007-10-12
Thanks heaps for the tip, I encountered this problem after installing CWiid to use a WiiMote on my desktop - just in time for the biggest LAN party on my calendar!  Had a little panic till I found this thread.

Thanks a lot.

---

