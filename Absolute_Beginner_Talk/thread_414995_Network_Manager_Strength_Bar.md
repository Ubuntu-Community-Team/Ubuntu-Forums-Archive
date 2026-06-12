---
title: "Network Manager Strength Bar?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by skypilot105 on 2007-04-20
I'm new to Ubuntu.
Began with Edgy about a month ago and now have installed Feisty without a hitch (whew!)

I have one small, but annoying problem.

My small problem is that I can't seem to find a strength bar in the tray for wireless connections.  
Connections are working fine now (I had a little problem with case-sensitivity of wireless router names, but finally figured that out).

I was hoping that installing feisty would magically produce the **nm wireless signal strength bar** in the tray, but it did not.

How can I make it appear?  :confused: 

Thanks

Skypilot

---

### Post by lamalex on 2007-04-20
try running nm-applet. Did you upgrade to feisty or fresh install. If you upgraded try doing apt-get install ubuntu-desktop; sometimes it leaves some packages behind.

---

### Post by jimrz on 2007-04-20
> **skypilot105 said:**
> I'm new to Ubuntu.
Began with Edgy about a month ago and now have installed Feisty without a hitch (whew!)

I have one small, but annoying problem.

My small problem is that I can't seem to find a strength bar in the tray for wireless connections.  
Connections are working fine now (I had a little problem with case-sensitivity of wireless router names, but finally figured that out).

I was hoping that installing feisty would magically produce the **nm wireless signal strength bar** in the tray, but it did not.

How can I make it appear?  :confused: 

Thanks

Skypilot

what is your video card? also, does it display progress bars in other apps (FF, Synaptic, update manager, etc)?

i have an old Thinkpad 600x and on both edgy and feisty it's video card cannot handle showing the strengh bars or any progress bars using the default Human theme, although they worked fine up through dapper. try switching themes I am using Clear Looks on that box and it  displays all properly on mine running either edgy or feisty. So did Industrial Tango and I beleive some others , at least on edgy.

---

### Post by skypilot105 on 2007-04-20
Thanks for the ideas

Neither running nm-applet nor upgrading the desktop made any difference.

The two little computer screens do show in the tray, but no signal strength bars.

The video card is nVidia nForce3.  Progress bars show when upgrading, etc.

Skypilot

---

### Post by hermanlutz on 2008-03-25
I had the signal bars, then the icon switched to the two computers icon.  I was hoping someone would answer your question, but this finally worked for me:

System>Administration>Network.  Click on Wireless Connection, then Properties, and finally check Enable Roaming Mode.

This was the default setting.  I must've switched it off when playing around with settings.  Who knew that affected the Icon!

---

