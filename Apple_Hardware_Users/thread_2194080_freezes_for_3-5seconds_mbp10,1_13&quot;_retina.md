---
title: "freezes for 3-5seconds mbp10,1 13&quot; retina"
date: 2013-12-16
forum: Apple Hardware Users
---

### Post by bcc2 on 2013-12-16
Hi All,

Ubuntu works pretty well on my MBP 10,1. It is a 13" (so intel 4000) and a i5 with 8gb.

Its starting to get seriously annoying. I am forever hitting these random 3-5 second freezes when doing stuff. I will be scrolling down a page or typing, pc will freeze for a few seconds then catch up. 

Any got any suggestions what I can do? 

I boot into ubuntu using Refind...

---

### Post by kjano on 2013-12-18
Did you add libata.force=noncq to your grub configuration and updated grub?

---

### Post by bcc2 on 2013-12-18
I wasn't sure if that affected the 10,1 as well.

I have however just added it to /etc/default/grub.

Will give it a try and report back.

---

### Post by bcc2 on 2013-12-18
still does it :( 

I'm on 13.10 3.11.0-14-generic

---

### Post by kjano on 2013-12-18
Are you sure you updated grub  (*update-grub* from the shell) after editing the file?

---

### Post by bcc2 on 2013-12-19
i did run update-grub.

today i have been using it all day and haven't noticed any stalls, so thanks!

I'm not sure what has changed with my audio, but now the red light (digital) is always on and sound comes out of speakers + headphones. I normally have to choose my audio output, disable digital in alsamixer. If I unplug headphones and plug them back in, it will come out of speakers again!

---

### Post by katmeef on 2013-12-27
> **bcc2 said:**
> I'm not sure what has changed with my audio, but now the red light (digital) is always on and sound comes out of speakers + headphones. I normally have to choose my audio output, disable digital in alsamixer. If I unplug headphones and plug them back in, it will come out of speakers again!

I have a macbookpro10,2 and I think when pulseaudio starts it unmutes one of the spdif outputs bringing up the red light.  running "amixer set 'IEC958',16 off" turns it off for me.

---

