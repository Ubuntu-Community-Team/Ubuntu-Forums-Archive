---
title: "failed to start X"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by lx638 on 2006-01-11
i am also a newbie to linux. i tried booting from live cd and it did not work. my monitor just turns off. so i tried installing it already.  and i have the same problem. somebody told me to type **sudo dpkg-reconfigure xserver-xorg**. i followed instructions and rebooted. i used the minimum/lowest settings to make sure my hardware meets it. but then it says **x failed to start again** here are the errors (i think) i found:

**no screens found**

and i also found these

[B](WW) the directory /usr/share/X11/fonts/cyrillic does not exist
(WW) the directory /usr/share/X11/fonts/CID does not exist
(WW) fonts.dir invalid
(WW) open APM failed (dev.apm_bios) (no such file of directory)[/B]

i am just using a shared video 32mb, S3 Pro Savage DDR. i am a windows user and i want to try this stuff.i need help. thanks.

---

### Post by gregwa on 2006-01-11
It looks like you are using breezy.  I'm not sure that breezy uses xorg.  It still might use XFree86.  If so, you might try this...

"dpkg-reconfigure -plow xserver-xfree86". 
The -plow is for "priority low" just so it asks you everything it can.

This info came from [http://panuganty.tripod.com/debiantips/graphics.htm]("http://http://panuganty.tripod.com/debiantips/graphics.htm") and the site helped me many time when i was trying Debian 3.

Hope this helps

Greg

---

### Post by lx638 on 2006-01-11
thanks. do i have to do this on the standard mode?or recovery mode?i'll try what u have given.will post the results.thanks

---

### Post by gregwa on 2006-01-11
Either one should work, but recovery mode doesn't try to start X.

Besure to shutdown after and see if it works.

---

### Post by benplaut on 2006-01-12
**DON'T DO THAT!**

breezy uses Xorg ;)

do the reconfiggin xserver again (the command you already did), and choose the 'Visa' driver. It's pretty universal.

---

### Post by lx638 on 2006-01-12
hi guys thanks for all your replies. i agree breezy uses Xorg. i just changed my video card and it works fine now. i think S3 Pro Savage DDR is not compatible. i am currently using geforce 2 mx400.

problem solved. thanks.

---

