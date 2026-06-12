---
title: "Macbook Pro and Feisty (w/ Beryl)"
date: 2007-06-06
forum: Apple Intel Users
---

### Post by DoubleDangerClub on 2007-06-06
Hey,

I've searched high and low and tried a ton of different install patterns, but I have yet to get this working successfully.
I'm hoping someone with the same config as me can lend me some tips.

I have a MacBook Pro (C2D 2.2, ATI X1600) and I've installed Ubuntu through Boot Camp.
Ubuntu works well, and I've successfully loaded the XGL drivers for the ATI card.
I have yet to get Beryl working though, I know it's beta, but I'd like to try it out and each time I try to run the Beryl-Manager, I get a white screen.

I've searched for solutions, but have yet to get one to work.

Is anyone else running the same system as me with this working? I'd really like to find a way to get this working, I plan on writing out how I did my install, etc. after I get it up and running.

Thanks!

DDC

---

### Post by ronocdh on 2007-06-06
I've a link in my sig pointing to the guide I used. Same hardware.

---

### Post by DoubleDangerClub on 2007-06-07
Thanks! I saw that before and followed it, but no luck. Any ideas?

---

### Post by ronocdh on 2007-06-07
> **DoubleDangerClub said:**
> Thanks! I saw that before and followed it, but no luck. Any ideas?
How's your Compiz performance? And how does the XGL session run compared to the default GNOME one?

---

### Post by DoubleDangerClub on 2007-06-07
My XGL session runs fine. I turned on desktop effects and those ran fine too. Not sure what's up with it.

---

### Post by ronocdh on 2007-06-07
> **DoubleDangerClub said:**
> My XGL session runs fine. I turned on desktop effects and those ran fine too. Not sure what's up with it.
If the built-in Ubuntu effects are working, then Compiz is treating you fine. If you followed the guide linked to to the T, well, I don't know what to tell you. I doubt it's reassuring, but on my same hardware I have had times when Beryl just didn't work, whether it was throwing a horrible recurring error every time I ran **beryl-manager** from the terminal, or just got the white screen.

All I can say is that on my last several installs I have been able to get it working very smoothly, and without any hitches. =/

---

### Post by russo.mic on 2007-06-08
Is it the white cube problem?  If you hit ctrl+alt+arrow keys do you see the cube rotate?

try this from a terminal if so.

beryl-manager --no-force-window-manager

if it works, put it in your sessions/startup for XGL!

---

### Post by Milamber_Cubed on 2007-06-14
The guide pointed to worked perfectly on my MacBook Pro... Thanks!

The only problem, if you can call it a problem, is that it works TOO well. All of the animations go really really quickly so that there's barely time to register what has happened. Is there any way of slowing them all down other than going through every single setting and tweaking them manually?

Thanks again for the pointer.

---

