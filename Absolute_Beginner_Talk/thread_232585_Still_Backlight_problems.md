---
title: "Still Backlight problems"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Talisker on 2006-08-08
I installed Dapper on a ICpowerhouse Laptop. It uses a Mobo with a SiSM760 +  SiS963L Chipset. I changed the CPU to a AMD Mobile64.

Dapper installed like a dream. The only worries I still have are Backlight and Screensaver issues.
I tried several settings in the Gnome Power manager.

Hibernate, suspend works ok.
The Screensavers work.

When I set "display to sleep" the screen goes just white. Which, of course is not the idea...;) 
How do I get that Backlight to shut off?

I checked other threads in the forum... but I'm still stuck.:( 

Thanks.

---

### Post by H.E. Pennypacker on 2006-08-13
What you're describing is not possible.  When a laptop actually goes to sleep, the screen is turned off as well.  Let's make sure that suspend is turned on by going to Power Management, and selecting "Sleep" for what to do when the lid closes.

Try that, and the next time you initiate sleep, the screen should be turned off.  By the way, I understand what you mean by the screen going white.  That means the screen shows nothing, and is black, but there is a white light coming from the bottom of the monitor (which is the backlight).

---

### Post by arvs on 2006-08-14
I have the same problem on an Inspiron 8000 using Xubuntu Dapper. Power management and screensaver works just fine, except for the power management of the monitor.

If I try 'xset dpms force off' the screen blanks, but doesn't turn off. Any help anyone?

---

### Post by Talisker on 2006-08-14
> **H.E. Pennypacker said:**
> By the way, I understand what you mean by the screen going white.  That means the screen shows nothing, and is black, but there is a white light coming from the bottom of the monitor (which is the backlight).

Well, the white light that is visible from the bottom of the Display is the problem...... I want it to shut off when the Laptop Display suspends. I'm still using batterie power and burn the lamp out when I run the Laptop on AC. Otherwise I could just use a "blank" screen saver.... 
There is a difference between "blank screen" with white light at the bottom and a proper "suspend" of the Display. :-k

---

### Post by arvs on 2006-08-14
I noticed another thing, which might be related, I don't know. When I close the lid of my laptop the screen does turn off, but then won't turn on anymore. Restarting the X-server with Ctrl-Alt-Backspace which someone suggested in another thread, doesn't help.

Not really a problem for me though, but I thought maybe it's related.

Thanks for any help.

---

### Post by Talisker on 2006-08-14
> **arvs said:**
> I noticed another thing, which might be related, I don't know. When I close the lid of my laptop the screen does turn off, but then won't turn on anymore. Restarting the X-server with Ctrl-Alt-Backspace which someone suggested in another thread, doesn't help.

Not really a problem for me though, but I thought maybe it's related.

Thanks for any help.

That sounds like you set your Laptop to "suspend" after you close the Lid...    Are you sure about your power settings?

---

### Post by gn2 on 2006-08-14
System>Preferences>Power Management>General>Tick "Dim the laptop panel when idle"

Worked for me...

---

### Post by arvs on 2006-08-15
> **Talisker said:**
> That sounds like you set your Laptop to "suspend" after you close the Lid...    Are you sure about your power settings?

I'm not sure about my power settings, and I don't know how to check this in Xubuntu. But I tried closing the lid while playing music, and the music just continued, so I guess it didn't suspend.

---

### Post by arvs on 2006-08-15
> **gn2 said:**
> System>Preferences>Power Management>General>Tick "Dim the laptop panel when idle"

Worked for me...

I don't understand. This is not an option with my Ubuntu system. Maybe different version?

---

### Post by arvs on 2006-08-16
I finally found what looks like a decent solution. I installed the nvidia-glx driver using the apt-system but this made my system crash on x-startup. Then I installed automatix and used that to install the nvidia driver. This worked like a charm and solved my backlight problem.

Using the Gnome Power Management facility still doesn't do a thing, but using 

xset dpms 0 0 180

(resp. being seconds untill standby, suspend and off) I can easily set it.

This driver might change other things too, like the font sizes, which might not be desirable.

---

