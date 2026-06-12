---
title: "PPC - DVI to HDMI"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by flatblack on 2007-07-04
Hello!

I've gotten Ubuntu7.04 installed on our Mac Mini - and it works great!

However, I'd like to connect that PC to our TV in the main room. It is a Sharp Aqous LCD.

I purchsed a DVI to HDMI cable, but the TV says an invalid signal was recieved, check the devices output settings.  If I play aorund with the cord, or smack the unit a couple of times,I can actually see the login screen but it looks like I'm stealing cable.. You know, all garbled up, cant really see anything to do anything productive but I CAN see the Ubuntu logo.

Am I asking for to much?  Is this possible?  My TV only has HDMI and RCA inputs, btw.

Thanks for any advice!

---

### Post by Cypher on 2007-07-05
I'm unsure what Ubuntu have to do with this? Isn't this more a hardware issue? Does the MAC have some sort of a POST during boot-up? Can you see that on the TV before it even gets to starting Ubuntu?

..and I'm pretty certain smacking the PC is not a good solution..;)

---

### Post by flatblack on 2007-07-05
You underestimate the true power of a good computer smack! :)

I do see the bootup, but it's in the same "sorry" shape that the OS screens are in.  I agree with you, I to am not overly certain how software plays a role in this, but I was wondering if there was anything I could do from a software (or hardware) perspective to make it work.

Thanks!

---

### Post by Cypher on 2007-07-05
Since the boot-up (pre-Ubuntu) looks just as bad as Ubuntu does, it almost looks like there is some hardware limitation on the DVI/HDMI output to your TV. Since DVI/HDMI share the same video signals, I wouldn't think the DVI->HDMI converter is doing anything, but at the same time if the converter wasn't of good quality, it might be adding enough noise or whatever to make the TV unhappy??

---

### Post by punx45 on 2007-07-05
were you using a different monitor before the TV?
what exactly did "check the devices output settings." entail?


this will likely require some xorg.conf editing.

copy and paste the contents of /etc/X11/xorg.conf here   (I might have to double check that path!)   so we can get a look at what is going on.

also, there is a PPC subforum here.    A search there may be helpful; this problem has likely been addressed before.   Perhaps you can get some help from other Mini users!

---

### Post by soulanum on 2007-11-10
I have a 22" widescreen lcd that I am running via a DVI to HDMI cable that I am having the same issue with (nvidia geforce 8600 GTS btw...)

This works fine out of the box in windows, and I have been forced to resort to it. I'm thinking there must be some kind of a weird "recognition" issue via the nvidia driver in linux? As soon as I put on the nvidia restricted driver and restart it all goes black (occasional thin red ghosting of the login screen)...

Any ideas? Bueller?

---

