---
title: "Code: Bad EIP Value upon suspending ubuntu"
date: 2008-06-15
forum: Apple Hardware Users
---

### Post by `Yummy on 2008-06-15
When I try to suspend ubuntu, it goes into the kernel, and says "Code: Bad EIP Value." In the last line before it freezes, it says "Suspending consoles..." then just sits there and refuses to suspend.

Any ideas? I can get a picture of it if necessary.

Thanks for any help on this.

---

### Post by cyberdork33 on 2008-06-15
> **`Yummy said:**
> When I try to suspend ubuntu, it goes into the kernel, and says "Code: Bad EIP Value." In the last line before it freezes, it says "Suspending consoles..." then just sits there and refuses to suspend.

Any ideas? I can get a picture of it if necessary.

Thanks for any help on this.
you should always post what hardware you are dealing with when you create a new thread. Intel? PPC? What Mac type? What version number?

---

### Post by `Yummy on 2008-06-15
I'm on an iMac 20" Intel Core Duo - 2.0 GHZ. I have successfully triple booted my computer with xp, leopard (mac 10.5), and ubuntu - latest version.

---

### Post by cyberdork33 on 2008-06-15
i assume you have installed the proprietary ATI drivers? They tend to be troublesome.

---

### Post by `Yummy on 2008-06-15
Yes, I did install the ATI proprietary driver.

---

### Post by cyberdork33 on 2008-06-15
try this:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Suspend.2FHibernation](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Suspend.2FHibernation)

---

### Post by `Yummy on 2008-06-16
Still didn't work, I tried suspending the computer two times - once just after I made the changes to /etc/default/acpi-support and before rebooting, and another time after rebooting.

Whether you need it or not, I just uploaded the picture of the kernel. Excuse the blurriness - I tried my best to hold the camera still; I couldn't use the flash because it would only give me a bright white spot on the screen. Not the best camera in the world, either.

It's attached to the post.

Once again, thanks for the help.

---

### Post by cyberdork33 on 2008-06-16
Well, you are definitely getting a crash of some sort. Someone with a bit of technical know-how can probably use that output to see what the problem is, but I would guess that it is related to the ATI driver.

You might try filing a bug report in Launchpad, with the trace info you have, they can probably determine the issue. It looks like something that won't be fixed real soon though unfortunately.

---

### Post by `Yummy on 2008-06-16
Alrighty, I just reported it on launchpad. Thanks for the advice.

---

### Post by DonnieP on 2008-09-10
I'm having the exact same problem on the same hardware except without the ATI drivers.  Just wondering if this issue got solved?  The weird thing is that prior to a fresh reinstall of hardy I was able to suspend fine.  Because of unresolved f-spot problems I decided to download and reinstall the latest hardy CD.  Didn't resolve the f-spot problem and left me without a working suspend.

---

### Post by cyberdork33 on 2008-09-10
Well, I am on intrepid now, but I can try messing with this again on my iMac. I don't ever use suspend so I don't even know if it works or not.

I had no luck finding a (current) bug report on this.

---

### Post by motin on 2008-10-07
> **`Yummy said:**
> Alrighty, I just reported it on launchpad. Thanks for the advice.

Url?

Thanks

---

### Post by DonnieP on 2008-10-09
The continuing saga:  I upgraded to Intrepid alpha a while back and suspend started working again (I suspend every day rather than shutting down).  Suspend kept working through the Intrepid beta . . . until yesterday.  After yesterday's updates suspend is again no longer working.  But it's different than the problem under Hardy.  It suspends fine (or looks fine) and leaves the slowly flashing power light like it's supposed to.  But when you resume (by pressing the power button) you get console messages about ATA3 (whatever that is) being slow (whatever that means).

---

### Post by DonnieP on 2008-10-11
Yet Another Update:  After latest Intrepid updates including the latest kernel, suspend (and resume) is once again working.  This seems to be turning into a daily routine of regression and then a fix.

---

