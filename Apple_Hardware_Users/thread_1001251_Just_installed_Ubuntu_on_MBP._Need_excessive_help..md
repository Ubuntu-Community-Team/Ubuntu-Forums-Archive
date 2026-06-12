---
title: "Just installed Ubuntu on MBP. Need excessive help."
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by Rocket Sock on 2008-12-03
I'm sure all of this has been posted before, but Id appreciate it if you bear with me anyway.

I just managed to get ubuntu dual booted on my MBP (Getting rEFIt to work was hard enough. It would just never install, and Im still not sure it is working, but its booting directly into ubuntu now, so Im happy). I've tried to follow the instructions on the Community documentation, but I've run into a few roadblocks, and it's not really working out.

Basic info:
Ubuntu 8.10
MBP Santa Rosa
OSX updated 100%

Help Needed:
1. In the hardware drivers, I cant seem to activate the Nvidia drivers listed. Heres what I did.
     A: Click on the driver
     B: Click activate
     C: type in my password
   After I do that, it for a brief second, has a loading bar pop up, and then disappears. After that, the "light" next to the driver does not turn on to indicate its active.

2. Need help getting the touch pad to turn off while typing. The documentation recommends pommed. But when I apt-get or look in synaptic, I dont see pommed. Do I need to add a new repository?

3. Wireless seems to be really weak, any fixes?

4. Anything else you can recommend I do. It seems most tutorials are written for previous versions of ubuntu, and 8.10 seems largely ignored. 

5. This one isnt Mac related, but is something I've wanted to know. The last time i used Ubuntu, everything I installed via synaptic/addremove, downloaded and installed to the root directory. My root is 10 gigs, how do I get it to download and install to my /home partition. (For the sake of mentioning it, my partition is 10gb /, 2gb SWAP, 90gb /home)

Thanks for helping a noob.

---

### Post by Rocket Sock on 2008-12-03
Ok, I now have another problem. When I try to update, I get errors in getting all the packages, and when I attempt to install the updates I DO get, It just idles and doesnt do anything.

---

### Post by Rocket Sock on 2008-12-03
UPDATE: Nvidia driver seems to be working now....dont know why.

---

### Post by cyberdork33 on 2008-12-03
Use the "Before You Post" link in my signature to properly identify your Macbook version and find the correct documentation.

If you have a problem with any particular section of the docuemtation, you can ask about it here, but you need to be more specific.

pommed is depreciated.

what do you mean by "wireless is weak"

---

### Post by Rocket Sock on 2008-12-03
My first post explained I was using a Santa Rosa MBP. Me reading the wrong documentation is not the issue.

Anyway, pommed is depreciated means nothing to me. What does that mean?
And as for "Wireless is weak". Exactly what I said. My wireless connection is weak, and I can only get things done when I connect with an ethernet.

---

### Post by cyberdork33 on 2008-12-04
> **Rocket Sock said:**
> My first post explained I was using a Santa Rosa MBP. Me reading the wrong documentation is not the issue.MacBook3,1 - 5,1 use the SantaRosa chipset, so that means nothing. Using the wrong documentation can mean everything because the fixes you are trying to do are possibly not for your machine (and thus would not work)

> **Rocket Sock said:**
> Anyway, pommed is depreciated means nothing to me. What does that mean?It means don't use it. i don't think pommed matters for what you are trying to do anyway since it has nothing to do with the touchpad.

> **Rocket Sock said:**
> And as for "Wireless is weak". Exactly what I said. My wireless connection is weak, and I can only get things done when I connect with an ethernet.

That is not a good description though. What do you mean by that? Signal Strength? Speed? Operation? 

If you mean that the computer indicates the signal is weak, it is normal that signal strength is indicated as lower in Ubuntu than in OSX. That doesn't mean that the signal strength is actually lower. The strength of the signal is determined by the output power of the AP and any interference in the area.

Furthermore, if you want help with issues you are having, you need to give more information about what you have done (or tried to do). What wireless driver are you using? What steps did you follow to get it to show up? What documentation ARE you following?

---

