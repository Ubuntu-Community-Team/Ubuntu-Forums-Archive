---
title: "[SOLVED] Palm"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by johnnylong on 2007-05-01
Hi again gang, it's me (johnnylong). I just recently loaded Ubuntu's new version and I am unable to sync my Pal Pilot. New help asap! Any advice?

---

### Post by ubnewbie2 on 2007-05-01
Have you gone into the System >preferences > removable drives and media,  and selected Palm on the pda tab?

---

### Post by johnnylong on 2007-05-01
been there done that. sorry I didn't post the message I received so here goes:

 'failed to connect using device 'Sony Clie' on port '/dev /pilot'. Check your configuration, as you requested old style usbserial 'ttyUSB' syncing, but do not have the usbserial 'visor' kernel module loaded. You may need to select a 'usb' device.

I did not have this problem when I ran the previous version of Ubuntu so any advice will be not only considered, but appreciated. Peace Out!

---

### Post by thegreenman on 2007-05-01
I'm having the same issue. on Feisty/ sony clie

---

### Post by thegreenman on 2007-05-01
[COLOR="Red"]Solved for me: I changed my usb settings to "usb:" instead of '/dev/ttyUSB0' and the sync worked. dunno why but it did.[/COLOR]

---

### Post by kc0eks on 2007-05-04
I havent seen the fix of using usb: before and this worked perfect for me as well. 

Worked on a Palm treo650 anyway.

Thanks!

---

### Post by johnnylong on 2007-05-04
Hey Greenman, you rock. That fix you gave me worked like a charm. Hope I can return the favor. And yeah Ubuntu rocks. Made the commitment a month ago to put Windows on the self and don't regret it one bit. Hack The Planet.
Thanks again JohnnyLong!!

---

### Post by chudder on 2007-07-31
this basically solved it, it just doesn't go to completion.  It does lose the connection.  I do seem to have all the files transferred though.  I have been trying to get my several PDAs to sync for a while, over a year.  I'm a little frustrated that I wasn't able to get a solution quicker, I don't know if this was a new fix in feisty or not but I'm happy now.  

Thanx a ton!

---

