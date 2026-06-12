---
title: "Screen brightness issues with a new Gutsy install"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by gambleb on 2007-11-11
Just installed Gutsy on my Sony Vaio PCG-7M1L today.  A bit of an upgrade from Dapper.  Anyway.  In Dapper I had control over my screen brightness.  Under Gutsy it looks as if it's stuck around 65-70%.  The sliders in the power management control and the function keys have no effect.  Any ideas?

Brian

---

### Post by xiombarg on 2007-11-12
Have you tried Applications>Settings>Display Settings, and adjust the Gamma sliders? Not sure if that's what you're after. I'm just a beginner.

---

### Post by gambleb on 2007-11-12
Not really what I'm looking for but thanks,  

I thought the problem fixed it self last night, but I guess it didn't.  I have the screen brightness set to 100% on AC and 75% on battery.  When I plug it it there is no change in the screen brightness.  In fact I don't think it's even at 75%.  Seems to be more like 60% or so.

Anybody have any ideas?

Brian

---

### Post by gambleb on 2007-11-12
Anybody?

---

### Post by xiombarg on 2007-11-13
Hi,

I can't really help, but I believe a number of Ubuntu users have had trouble with ACPI control of their laptops. This is what you're talking about, right?

---

### Post by gambleb on 2007-11-13
Forgive me, but what exactly is ACPI?

---

### Post by xiombarg on 2007-11-14
> **gambleb said:**
> Forgive me, but what exactly is ACPI?
ACPI: Advanced Configuration and Power Interface

It's basically a power management interface for computers. It controls events like suspend or hibernate, or power down a hard drive. Have you been using some form of settings control panel, to choose how Ubuntu handles power management?

I don't actually use Ubuntu (Xubuntu is different in this regard) so I can't give you more specific help. Not sure why no one else is jumping in.

---

### Post by gambleb on 2007-11-14
The only thing that I have changed is in the power managment app under system->preferencens  that comes with the normal install of Gutsy.  

I just noticed that the screen is really dim on the Grub boot screen also.  Is there a BIOS setting that controls this or is it all O/S driven?

Brian

---

### Post by xiombarg on 2007-11-15
> **gambleb said:**
> The only thing that I have changed is in the power managment app under system->preferencens  that comes with the normal install of Gutsy.  

I just noticed that the screen is really dim on the Grub boot screen also.  Is there a BIOS setting that controls this or is it all O/S driven?

Brian

I think you are using the appropriate app; perhaps you could try different settings in that app.

If you have access to your BIOS settings, then have a look at what options are available. If the GRUB screen is already dim, then it is not being caused by Ubuntu (the OS hasn't yet loaded at that stage). It is possible your screen is still warming up when the GRUB menu is displayed. You could try leaving your screen in the GRUB menu display for a couple of minutes, to test for that.

---

### Post by gambleb on 2007-11-15
Tried that and it stays the same.  I have no controls over screen brightness in the BIOS.  I guess I might try to reload Dapper and see if the problem goes away.  

This may be a dumb question, but could it be a function in the GRUB?  I'm pretty new to all of this so I don't even begin to know where the video output functionality starts.

---

### Post by Inxsible on 2007-11-15
There have been reports of screen brightness issues with Gutsy. Lemme see if I can find that thread for you.

---

### Post by benhur99ph on 2007-11-19
I'm having the same problems. The brightness adjust applet worked fine on feisty, but when I installed gutsy, I can't adjust it anymore. Also the Fn keys don't work. I use a Sony Vaio FS940.

---

