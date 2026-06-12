---
title: "screensaver problems"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Bri0 on 2007-10-20
Previewing them works fine, and having it start at 1-or-2min works fine, but when having it start at 15min, it just shows a blank screen. Whats up with that?

Thanks

---

### Post by barkej on 2007-10-20
Have you checked System>Preferences>Power Management to make sure your screen is not going to sleep?

---

### Post by Bri0 on 2007-10-20
The screensaver is set to start at 15min, and the monitor is set to go off at 30min.

I let the computer sit while I watched to see if it goes to the screensaver, yet the monitor goes blank at 10min.

---

### Post by Bri0 on 2007-10-21
So, what could be causing my screen to go black when the computer is inactive for 10min?

When this does happen I am able to move the mouse and it goes back to the desktop or the lock screen (depending on how log it been inactive).

But its kind of lame without a nice screensaver.

:confused:

---

### Post by Shazaam on 2007-10-21
I am still researching it but I think it is related to "DPMS" 
[http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling](http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling)
All versions of linux that I have installed have the same problem (monitor blanking after 10-15 min).

---

### Post by Bri0 on 2007-10-22
It works now. I'm sure it was because I had 'xserver-xgl' installed for the effects.

I don't really need the effects anyways I guess, even tho I have a 'ATI x1200'. Unless there's something I missed, or perhaps a bug (I don't know).

---

### Post by riverfr0zen on 2007-10-28
I posted a workaround (it is a total hack though), which seems to work for me with xgl installed:

[http://ubuntuforums.org/showthread.php?t=584406&p=3651954](http://ubuntuforums.org/showthread.php?t=584406&p=3651954)

---

### Post by tony40 on 2007-10-29
Recently upgraded myself and installed Webilder Applet 0.6.2 which changes my backdrop on my desktop.  

That inspired me to try out the screensaver which resulted in the problem described here.

Your 'Hack' works great. 

Thank You!

---

