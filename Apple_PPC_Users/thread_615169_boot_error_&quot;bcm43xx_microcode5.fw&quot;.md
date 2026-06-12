---
title: "boot error &quot;bcm43xx_microcode5.fw&quot;"
date: 2007-11-16
forum: Apple PPC Users
---

### Post by Pokefan on 2007-11-16
I get the error every time I try to boot up:

first it comes up "cannot allocate resource region 0 of device....."

then I get

bogl_init failed: EXPLODE

screen init failed

goes through other stuff then finally it says:
No resume image, doing normal boot...

then the 

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
it gives this error over and over if I just let it sit. I can get a log in but it won't ever load anything.

I'm sure doing a good job of screwing this up:) That's alright I'm here to learn!

---

### Post by kugn on 2007-11-17
Not entirely sure what you're conveying. Are you experiencing any problems at all? 

For myself, I don't remember seeing bogl_init failed: EXPLODE, so I can't say anything about it.

As for the bcm43xx, the problem is that your Airport /Airport Extreme needs firmware. That can be gotten by 
apt-get install bcm43xx-fwcutter
which includes a script that downloads the firmware and installs them to /usr/lib/firmware

---

### Post by Pokefan on 2007-11-17
Yes, I'm having problems. I guess I could have been a little more clear on that!:)

I can't even get to a splash screen at all it just will not go past this error. I'll give this a try thank you!!

---

### Post by Doctor J. on 2007-12-08
> **Pokefan said:**
> I get the error every time I try to boot up:

first it comes up "cannot allocate resource region 0 of device....."

then I get

bogl_init failed: EXPLODE

screen init failed

goes through other stuff then finally it says:
No resume image, doing normal boot...

then the 

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
it gives this error over and over if I just let it sit. I can get a log in but it won't ever load anything.

I'm sure doing a good job of screwing this up:) That's alright I'm here to learn!

The 1st part "cannot allocate..." is a standard warning.  I see it too.  Nothing to worry about.

The 2nd part "bogl_init ... screen init failed" is much more serious.  It means that the kernel wasn't able to talk successfully with your graphics card.  Until this happens, you're not going to see any pretty windows or much of anything else.  Does the LiveCD run well on this machine?  Also, it might help if you tell us more about what hardware you've got there.

The 3rd part "bcm43xx: ..." is telling you that the kernel wasn't able to talk to the Airport card.  The driver isn't included by default because it is copyrighted information and the Ubuntu project doesn't want to get sued for putting it on the disk.  Running the command that Kugn gave you in a Terminal *might* fix it, or visit this forum thread: [http://ubuntuforums.org/showthread.php?t=526901&highlight=fwcutter](http://ubuntuforums.org/showthread.php?t=526901&highlight=fwcutter) .  In any case, you won't be able to do anything about it until you get properly logged in, and WiFi isn't exactly needed to make the system run.

So your priority is to get the screens up okeh, and you might find more knowledgable folks in the Video forum: [http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)

---

### Post by jreubens on 2008-03-23
i dont know if this is the right place to ask or not.

I face the same problem. I am having a compaq presario machine model v6502EO comes with vista pre installed, i am trying to install ubuntu as a dual boot, i am experiencing the same problem...

I am installing from a live CD, i cannot proceed it says.. bcm43xx_microcode5.fw not available or load failed.

I am very new to linux, can you help me out.

i have nvidia graphics card.

Thank you,

---

