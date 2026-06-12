---
title: "Problems Hibernating"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by McMagic on 2008-03-19
Ok, so like alot of other laptop users I'm having trouble hibernating and suspending. I have an HP laptop with 1 gig of ram and 2 gigs of swap, so i should be ok for hibernation. However, when i click hibernate, it just goes to a black screen and suspends, and i end up having to hard-restart.

Any suggestions would be awesome!

---

### Post by bro on 2008-03-19
my suggestion would be to forget about it. I tried to get such things fixed on laptops where it didn't work with. After many attempts it sometimes works without crashing but was so slow one mitght just as well reboot. 

I now have a Dell D830 where suspend and hibernating works fine. Just wait until it works out of the box with maybe the next release and next time choose your hardware carefully.

If you want to give it a try anywasy you might want to try[ these kind of solutions]("http://ubuntuforums.org/showthread.php?t=471855")

---

### Post by louieb on 2008-03-19
One possible reason for hibernation to not work is its not looking in the right place for you swap partition.  I've fixed hibernation on my IBM T30 like this:
1st make sure swap is being used you can run the the **free **or **top** command to find out
If you find swap is zero available.
Find the [COLOR=Blue]**uuid**[/COLOR] of your swap partition. : **blkid**
check ** /etc/fstab** to make sure swap is using right[COLOR=Blue][B] uuid

[/B][COLOR=Black]and for hibernation check [/COLOR][/COLOR]**/etc/initramfs-tools/conf.d/resume **for the right uuid.

if you have to change the above file then to make the change go into effect run 
```
 sudo dpkg-reconfigure  initramfs-tools
```

[Nuts Ubuntu FAQ]("http://louboldt.com/ilinuxmisc.htm")

---

### Post by gasparov on 2008-03-21
> **bro said:**
> my suggestion would be to forget about it. I tried to get such things fixed on laptops where it didn't work with. After many attempts it sometimes works without crashing but was so slow one mitght just as well reboot. 



I should have red this post earlier, it used to work for me with 7.04 even after upgrading, with a new fresh install it doesn't anymore.I did spent some time on it but no joy.

It's not about chosing the hardware is about luck, you are the proof of it cause you have a dell....

Taken from /usr/share/doc/hibernate/HOWTO.gz
> **** TROUBLESHOOTING: HARDWARE ISSUES AFTER AWAKENING

Some kernel modules need to be unloaded prior to hibernation.  This is
largely preconfigured, but some carelessly built hardware, for
instance many Dell laptops (Dell is notorious for sloppy engineering)
require that particular modules be unloaded.  For example, on my Dell
X200, a particularly worthless piece-of-crap laptop which is also
surprisingly slow, the 1394 (firewire) interface failed after
hibernation.  This was cured by adding the line....


---

### Post by bro on 2008-03-22
I'm not sure if one man's trouble with firewire on another (much older) model of Dell proofs it's a random thing that depends on the hardware builders hormone cycle. 
To give another example: Ubuntu 7.04 didn't boot on the Fujitsu SIemens of my girlfriend. Why? The x1400 ati graphics. It did boot on 6.10 and before. The hardware didn't change, the software did. 

Why can I hibernate and suspend flawlessly now? On the Dell D830 I'm free from any proprietary software. These kind of thinks improve compatibility with Ubuntu a lot. I really think that explains it better. However I'm opposed to the 'random hardware failure' argument because itmoves the problem out of my sphere of influence. And like all of us, I'd like to rule the world. :mrgreen::tongue:

---

