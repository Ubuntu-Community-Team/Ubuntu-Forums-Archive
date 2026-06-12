---
title: "powerbook to Airport Extreme ARRRRGGHHHH"
date: 2007-07-17
forum: Apple PPC Users
---

### Post by neatokino on 2007-07-17
I am in a state of Extreme aggravation, trying to get my 12" Powerbook connected to my Airport Extreme base station.  I have read through numerous posts on the subject here, tried many things, reconfigured the base station four different ways, and can't get anything to work.  

I CAN connect in Ubuntu with a wired connection through the base station LAN port.  I CAN connect wirelessly (easily) if I run the computer on OSX Tiger (it's a dual boot system).  My system DOES recognize my base station in Ubuntu, it just won't connect to it.

I set up the base station with WEP and have set a 13 digit password.  That works fine if I boot up in OSX.  So I know that my Base Station is working and I know that my wireless card is working.  

Oh, and to make matters more frustrating, I was able to connect with a WEP password on my son's Airport Express when visiting him earlier this week.  So, I know that I can, in theory, connect to an apple wireless router on this computer running Ubuntu.

Is there any chance that anyone can walk me through this process?  It's frustrating, to say the least.

I'm absolutely willing to reconfigure my Airport Extreme to make things easier, but, clearly, the problem is on my powerbook's side.  

There must be some way to make this work.

---

### Post by guidop on 2007-07-22
Have you configured your Airport Extreme to support both  802.11b and 802.11g protocols?

I have read that the fwcutter only supports 802.11b 11 MB/sec communication.
Don't know if that's still the case, but you might give it a look.

I don't yet have personal experience with Ubuntu wireless on a PPC Mac,
but was thinking of trying Ubuntu on my 12" Powerbook soon, so I've been reading up.

---

### Post by neatokino on 2007-07-23
Yes, I configured the Airport Extreme to cover b and g networks, as well as 'n', but it still won't work.  The airport card does work, however, with a Belkin router I had before I got the Airport Extreme, so I know I can get good functionality with the airport card.  

I'm still hoping someone will help me figure out how to configure the Airport Extreme to work with the 12" powerbook and ubuntu.

---

### Post by Zaelore on 2007-08-05
First make sure you've used the firmware cutter and put the firmware in the proper directory and have done $ sudo modprobe bcm43xx to load the appropriate module.

When you try to connect to your wireless net in linux are you using an ascii version of the key? If so here is what you should do. 

In mac os x open up airport admin utility in /Applications/Utilities/ 

This will bring up a window showing airport base stations on your network. There will probably be just one. Double-click it or click configure.

In the window that comes up there will be an icon at the top with password written under it, click here. This should give you a hex value to use when not connecting with apple hardware.

Reboot linux and connect using this instead.

---

