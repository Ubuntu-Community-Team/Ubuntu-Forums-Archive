---
title: "How to bring Windows back to Grub"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by CleverWilly on 2007-09-16
Hello!

Help, I'm in trouble!

I've installed Ubuntu as dual-boot with Windows XP. As I mainly use Windows I decided to bring it to the top of Grub boot options.  

So I opened menu.lst file and copied Windows XP entry with all the text on top of Ubuntu entries.

And then I have upgraded to Ubuntu Studio package. The problem is that Windows entry has disappered from menu.lst file. It's just erased!:mad:

The worth thing is that I don't remember what the hell was written there to bring Windows as boot option.:confused:

What am I to do?

---

### Post by skymera on 2007-09-16
can you post you grub menu?

sudo gedit /boot/grub/menu.lst

its most likely you added XP to Debian section.

try Start-Up manager, you can set windows as Default :D

---

### Post by Surkow on 2007-09-16
When you open the menu.lst file skymera mentioned you can find detailed instructions for adding Windows back into Grub.

---

### Post by anaconda on 2007-09-16
Yeah, and if you move windows to the Debian section it can be erased when upgrading to a new kernel version.

---

### Post by CleverWilly on 2007-09-16
Wow, guys, that was fast! :guitar:

My Windows is back. Indeed, I have coppied it to main Debian section, on top of all other Ubuntu options.
I've coppied instructions from menu.lst file and now everything boots.

So, thanks a lot!

I wonder where I can find this Start-Up manager? I've searched Prefences and Administration options and couldn't find anything like that

---

### Post by rahimveron on 2007-09-16
> **CleverWilly said:**
> I wonder where I can find this Start-Up manager? I've searched Prefences and Administration options and couldn't find anything like that
System->Preferences->Sessions
There you will find startup options

---

### Post by JBAlaska on 2007-09-16
Yuo can get SUM here;
```
http://ubuntusoftware.info/sum.html
```

Handy little tool, it fixed me up after I fubar'd my boot splash screen.

---

