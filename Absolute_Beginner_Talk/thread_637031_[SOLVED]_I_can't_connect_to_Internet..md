---
title: "[SOLVED] I can't connect to Internet."
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-12-10
Lo ppl.
I can connect to Internet everywhere but not at my home...
I connect through wifi and have a broadcomcard with the properitery drivers installed. When I try to connect the thing just go round and round and never connects.
It would be really nice if someone could help me. :)

---

### Post by Law506 on 2007-12-10
You doing a dualboot with Windows???

If not did you use the the restricted drivers that come with 7.10 only?  I use wifi on my laptop with 7.10 on it and I placed the restricted drivers on there and it came up.  However, there is one other file that might be needed, something along the lines of bcmxx, I am at work right now and don't have the file name on me.  If you search through synaptic you will see what I am talking about.  If you dont find it I will get back to ya in a few hours once I am home.

* One time the restricted driver worked straight with no hiccups and then another time I had to download the bcmxx file in order for the restricted driver to work.  Sounds like you might be experiencing something similar.

---

### Post by spydon on 2007-12-10
> **Law506 said:**
> You doing a dualboot with Windows???

If not did you use the the restricted drivers that come with 7.10 only?  I use wifi on my laptop with 7.10 on it and I placed the restricted drivers on there and it came up.  However, there is one other file that might be needed, something along the lines of bcmxx, I am at work right now and don't have the file name on me.  If you search through synaptic you will see what I am talking about.  If you dont find it I will get back to ya in a few hours once I am home.

* One time the restricted driver worked straight with no hiccups and then another time I had to download the bcmxx file in order for the restricted driver to work.  Sounds like you might be experiencing something similar.

If you mean bcm43-fwcutter that's the one that installs when you use the restricted drivers app...

---

### Post by dward526 on 2007-12-10
what security protocol do you use at home?  Check your settings, I had similar problems once.

---

### Post by Law506 on 2007-12-10
> **spydon said:**
> If you mean bcm43-fwcutter that's the one that installs when you use the restricted drivers app...

Not necessarily, installing the restricted driver failed the first time because bcm43-fwcutter was not installed.  Something happened somewhere in process, but it was simple fix, went and got the bcm off synaptic and then went with the restricted driver and all was well.  

Might not be the problem at hand, but none the less it was problem for someone else :guitar:

---

### Post by spydon on 2007-12-10
> **dward526 said:**
> what security protocol do you use at home?  Check your settings, I had similar problems once.

WEP I think, but it works on Windows computers...

---

### Post by PhoenixP3K on 2007-12-10
> **spydon said:**
> WEP I think, but it works on Windows computers...
WEP works on Linux as well, their are different settings in the Network Manager when you select a WEP encription. Just make sure the settings are the right ones for your home network (ASCII or hexadecimal WEP key).
Also Ubuntu will ask you to record that key in the password manager so that each time you attempt to connect to that network it will ask you for a password you selected (instead of the full WEP key)

---

### Post by jeffinhburg on 2007-12-10
Hi all,

Didn't want to start a new thread, and this one seemed close enough...

I'm having a problem on 7.10 running off the CD, and don't know if it will be any different if I partition and install.  It's a broadcom 43xx.  The help file said to install ndisgtk iin Synaptic Package Manager.  The problem is that when I view all the files in Synaptic Package Manager, there is no ndisgtk.  Venturing a total guess, but I suppose it has to connect to the internet to download ndisgtk, and isn't that a catch-22?  Need the driver to work to connect to the internet in order to get the driver files to come over from Windows....  I already tried the enable restricted drivers check boxes, but got popups repeating that they were not enabled when I checked them and pressed "enable."  

Thanx for any help!

I know this is my first week trying linux and have no idea what I am doing, but I'm starting to wonder if it's worth it if I'm too stupid to do the most simple things with it, or just too old to learn anymore.  Made sense at the time, since Vista completely sucks, has thousands of things I don't want or need, and  is too resource heavy for my uses, which are just surfing (have used Firefox since the first beta), word processing, spreadsheets (already have been using openoffice for years) and some simple music mixing/editing/controlling.

---

### Post by spydon on 2007-12-12
> **PhoenixP3K said:**
> WEP works on Linux as well, their are different settings in the Network Manager when you select a WEP encription. Just make sure the settings are the right ones for your home network (ASCII or hexadecimal WEP key).
Also Ubuntu will ask you to record that key in the password manager so that each time you attempt to connect to that network it will ask you for a password you selected (instead of the full WEP key)

Yes I know that it works, but it doesn't work on all routers for me...

---

### Post by spydon on 2007-12-15
I installed ndiswrapper and took a windows driver and now it truly works outside the box! :)

---

