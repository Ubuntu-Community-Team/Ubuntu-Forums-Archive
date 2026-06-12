---
title: "iMac fan issues?"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by MikeSz on 2009-10-29
I have an iMac 20" 2.66 Aluminium Intel version which is about 12 months old running both OS X and Ubuntu 9.04.  Sometimes, when you power the unit up from cold, after about 2-3 seconds (just before you get the boot menu) a fan kicks in from what sounds like the lower left hand corner of the unit (as if you were looking at the screen) which is really loud - it actually sounds like a jet engine taking off.  It doesnt die down any time soon if you leave it on and the only way of getting rid of it is if you simply power the unit down and then power it back up again.  After that its fine and you dont hear a peep out of the unit.  It's only doing it once out of every 5 power ups or so but it is quite annoying.  

Ive not had any other issues with the unit, it doesnt crash and isnt doing anything unusual otherwise.  Has anyone else had this or know what it might be and how to address it?

---

### Post by MikeSz on 2009-10-30
Bumpety bump bump.....

---

### Post by INTENSETUX on 2009-10-30
Hi Mike

Have you installed SMC fan control on your mac at any time ?

I have it on mine , but if you remove it the fans continue to run at smc levels.

Try this , [http://support.apple.com/kb/HT1379](http://support.apple.com/kb/HT1379) 

Not sure if this is anything to do with your problem but it may be worth resetting the pram/nvram ???

Daz

---

### Post by MikeSz on 2009-11-08
I dont think its to to with that to be honest, Although it is getting worse now so I think its perhaps a heat sensor or possibly a fan thats starting to stick so it thinks it has to work twice as hard.  I may just take it in to the Apple shop and see if they can take a look at it.

---

### Post by Joushou on 2009-11-09
The applesmc kernel module doesn't handle the fans very well by itself, but it gives you a nice vfs-style interface to set the speeds and read the sensors as you wish...
With no other fancontrol than the kernel module, it will wait for the temperature to become critical before it fires up the fan to full speed...

You could try the script i wrote for my MacBook Pro to deal with the issue, which is located [here](http://ubuntuforums.org/showthread.php?t=1102465&highlight=fancontrol)... I designed it to handle anything i could think of that applesmc could throw at it, so it *should* be able to deal with an iMac as well.

Try to run it, and look at the logs (Which is at /var/log/smcfancontrol by default)... Should throw you a line every time the temperature changes, with the updated fanspeed... Hopefully, this will quieten your iMac...

EDIT: I think i made a non-laptop bug in the scrip, wait for the 0.3.2 update! (Which will be in a couple of secs...)
EDIT: Quickly updated the script, so it *should* work on an iMac now... I haven't tested it though, so please tell me what happens! (The worst thing that could possibly happen is... Nothing.)

---

