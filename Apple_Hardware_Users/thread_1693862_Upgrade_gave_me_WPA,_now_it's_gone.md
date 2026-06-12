---
title: "Upgrade gave me WPA, now it's gone"
date: 2011-02-23
forum: Apple Hardware Users
---

### Post by Chris Grk-O-Matic on 2011-02-23
Hi all. When I recently upgraded my PowerBook G4 to Lucid from Karmic a wonderful thing happened, my WiFi was finally able to connect to WPA. This was great! Now I don't know what I did because the laptop is not finding my network anymore. Could it have been a routine upgrade or perhaps installing MythFrontend?
 
Sorry I don't have the laptop on me at work, but does anybody have any ideas what it may be?
 
 
Thx,
Chris
 
--------------------------------------
1Ghz PowerBook G4
1Gig RAM

---

### Post by linuxopjemac on 2011-02-23
We are experiencing trouble in MintPPC / Debian too...You might want to try wicd 1.6.2, don't give you guarantees though.

---

### Post by Chris Grk-O-Matic on 2011-02-24
Thanks I'll look into that.
 
I was really excited that WPA finally worked -- I was able to upgrade the security for all my other wireless devices as well. It was like a relief.
 
But oh man was it a tease!

---

### Post by Chris Grk-O-Matic on 2011-02-24
I tried wicd 1.7.0, it was the only one available in Synaptic. When trying to connect to my wireless network it said Connection Failed: Couldn't Obtain IP Address.

Any ideas if there's going to be a fix in an upgrade? Maybe I'll just reinstall off my 10.04 disk [when WPA worked] and not do any updates or upgrades.

Thanks
Chris

---

### Post by linuxopjemac on 2011-02-26
There is no fix yet, but people are informed. All we can do is wait. In MintPPC we have a few workarounds to this problem:
[http://www.mintppc.org/forums/viewtopic.php?f=10&t=233](http://www.mintppc.org/forums/viewtopic.php?f=10&t=233)

---

### Post by Chris Grk-O-Matic on 2011-03-01
For the heck of it, in Wicd I clicked on the advanced tab and I enabled debug mode... wifi now works on my Powerbook!

---

### Post by linuxopjemac on 2011-03-02
that is interesting...

---

### Post by Chris Grk-O-Matic on 2011-03-02
Now it's not working. I unchecked and rechecked debug mode and rebooted and now it does not connect.

---

### Post by rsavage on 2011-03-03
This might be a stupid question, but are you using different user accounts?  I'm just wondering if you have the necessary privileges?  See the bottom post of [http://ubuntuforums.org/showthread.php?t=1676488](http://ubuntuforums.org/showthread.php?t=1676488)

I'm sure you've already tried this though!

---

