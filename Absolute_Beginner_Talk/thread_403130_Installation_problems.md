---
title: "Installation problems"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Pinck on 2007-04-06
Hey,

Both with 6.06 and 6.10 I can't seem to get past the screen that informs me that it installed the initial drivers alright, then gets stuck on setting up the file system.  If you need the exact wording I'll reboot and grab it.  Its very early into the installation.

Where should I start my troubleshooting?

I did do the md5 checksum and my downloads seem fine.  If I try to check my disk with the installation CD it unfortunately still needs to set up the file system and craps out.  Nero seemed to think that my burn was fine (had it verify the burn) and because I'm getting this with both versions I burnt I doubt it to be a bad burn.

Some system specs if it helps:
mobo is a8n-vm CSM-UAYGZ (Asus)
the mobo has integrated Geforce 6150
cpu is an AMD 64 3000+ (I'm trying to install 64-bit versions, but verified that the 32-bit version of 6.10 takes a dump at the same stage of the installation).

Let me know your thoughts on where to go here.

Thanks in advance!!

-John

---

### Post by FunnyLookinHat on 2007-04-06
Hey dudes,
You're probably using the 64 bit CD and that's why you are getting errors.  Go ahead and download the regular 32 bit version of the LiveCD and you should be fine.

---

### Post by houstonbofh on 2007-04-06
There is a bug in the 6100 series video driver support.  Run with the alt-install, and use the 'nv' driver until it is resolved.

---

### Post by doobit on 2007-04-06
I have also found the alternate install CDs easier to use than the live CDs.

---

### Post by Pinck on 2007-04-06
I actually tried both 64 and 32 bit versions (as mentioned above somewhere in my ramblings).

I'm burning the alt CD right now and will post back with my results.  Thanks for the tip on the 6100 drivers!  That's the kind of thing that makes a newbie scratch their head and say "wtf?"



> **FunnyLookinHat said:**
> Hey dudes,
You're probably using the 64 bit CD and that's why you are getting errors.  Go ahead and download the regular 32 bit version of the LiveCD and you should be fine.

---

### Post by Pinck on 2007-04-06
Hmmm, still looks like a no-go.

In text-only install on the alt disk it only gets as far as "Loading Kernel" before it hangs.

Any way for me to get a more verbose set of error messages to help narrow things down?

---

### Post by Kedma on 2007-04-06
I got the install to work.. but it hangs at the desktop after the login screen..

AMD X2 3800 / 7800GT

---

### Post by houstonbofh on 2007-04-07
> **Pinck said:**
> I'm burning the alt CD right now and will post back with my results.  Thanks for the tip on the 6100 drivers!  That's the kind of thing that makes a newbie scratch their head and say "wtf?"
Not just a newbie.  I fought with that for a few hours myself!

As to the faults, try the latest Feisty Live CD and see if it comes up.  Feisty has some additional hardware support.  However, the Asus Commando **Requires** the SVN build of feisty.  You may want to wait for the last Beta on April 12th.  (I don't know where herd6 is.  It should have been out Thursday.  Herd6 should have the Commando patch.)

Kedma, You have an install, but X is messed up.  Boot to a (recovery mode) and run 'dpkg-reconfigure xserver-xorg' and use the nv driver, and it might just work. :)

---

