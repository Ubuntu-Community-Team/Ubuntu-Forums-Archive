---
title: "dead x server"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-11-16
After restarting my PC (Edgy only - no XP) I got the dreaded "Failed to start the xserver - it is likely it is not set up correctly"

I searched other posts and found some suggested sudo commands to reconfigure it but I am unable to get a terminal window.

When I start up the PC I get as far as the Ubuntu loading line! and then a flashing cursor, then the Error Screen as mentioned above. I am offered an option to look at the error message in detail. I press NO, and get out of the screen and out of the next screens to be left with a blank screen with a flashing cursor. It will take input but nothing happens. The enter key just jumps down a line. I need a terminal. Any help is appreciated - I am running on the live CD now!

Tony

---

### Post by aidanr on 2006-11-16
ctrl-alt-F6?

---

### Post by tchoklat on 2006-11-16
> **aidanr said:**
> ctrl-alt-F6?

Thanks,

That worked but what I did next didn't.

I have a G-Force 2 32 meg card that runs my 15" HP CRT monitor fine in 1024 mode @32m colour depth.

When I went into the terminal I stopped the gdm OK
typed sudo /dpkg-reconfigure xserver-xorg
went through all the prompts as best as I could and then restarted the gdm

I got the same error telling me "Screen found but does not have suitable configuration" 

I then reduced the res and screen depth in the config utility and started ubuntu in 320X200 res @140 refresh rate only - nothing better.

Surprisingly the live CD works fine so there is nothing wrong with the hardware.

Can I copy the config files from the live CD perhaps.

Any help is appreciated.

Tony

---

### Post by aidanr on 2006-11-16
i guess you could boot the live cd, mount your / partition and copy the /etc/X11/xorg.conf over

---

### Post by PPAAUULL on 2006-11-16
You could try reconfigueing the Xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` that should get it working again like normal.

---

### Post by tchoklat on 2006-11-16
Hello,
 
I did this and received the same response - "Screen found but does not have suitable configuration" . If I select another driver 'brand' it tells me that screen not found.
 
I am selecting 'VGA' and the config I have always used as far as resolution and refresh rate. All others I left as prompted on the config setup screens. (PS using G-Force 2, 32 meg on 15" CRT screen)
 
Why does the live CD work and the on-disk version have this error? I am bamboozled!!
 
Tony

---

