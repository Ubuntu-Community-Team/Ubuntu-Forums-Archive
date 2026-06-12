---
title: "No volume control in KDE"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-06-19
I recently had to rebuild my system, and installed Ubuntu, and then put KDE on top.  (I like the flexibility).

However, I have no volume control.  The sound is playing in KDE, but it's very very quiet, and the volume control I used to see in the lower right hand corner is no longer there.  

Anyone have any ideas?

---

### Post by Alex&amp;Linux on 2007-06-19
In terminal:

  alsamixer


Thats a basic and handy tool for the job.
I also have KDE with my Gnome ubuntu, but ive not played with it enough to know more!

---

### Post by adamklempner on 2007-06-19
The volume control thing that docks into the task bar is called "KMix".  (K -> Multimedia -> KMix).  From its settings you can make it stay docked.

---

### Post by mohnkern on 2007-06-19
Thanks.  However after today's updates, I'm getting no sound at All.  I've got audio disabled on my motherboard, but in Kmix it's still showing up. (At least I assume that's what VIA 8237 is.)


I turned up the audio full in Kmix on my Sb live card, and on my Logitech USB headset.  Both are plugged in, and I have speakers plugged into the Sound card, in the right place.



Is there any way to tell what device audio is going out to?

Sorry to sound frustrated, it's gone from bad to worse.

---

### Post by Alex&amp;Linux on 2007-06-19
I know how you feel, as I had a brief experience with this problem (nothing like trying to work without music for me :))

Lets first make sure that your sound device is recognized. In terminal: "lspci" without quotes.
See if you can find it there next to "audio device"

If it is, then (as I previously recommended) run "alsamixer" in terminal (no quotes).
Everything should look like the screenshot ive placed below.

If everything looks cool there, its possible that sound service is only available to root user, so you could try to launch an app from terminal, for example:  "sudo rhythmbox" without quotes, as root launching the application, if you can get sound, then changing the permissions should fix!

If that fails, maby theres a problem with driver?
Here is a link to more information in that regard

[http://bugtrack.alsa-project.org/main/index.php/Matrix:Main](http://bugtrack.alsa-project.org/main/index.php/Matrix:Main)

Thats about all of the useful stuff I could find, and now I must sleep as there is an early morning awaiting me :(

Here is a link to a ubuntu support site, specifically looking at sound issues!

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

What an adventure!

---

### Post by mohnkern on 2007-06-20
Thanks for the reply.  I'm on my way out to work, so I'll try this tonight, but wanted to let you know the picture you showed didn't appear.

---

### Post by mohnkern on 2007-06-20
nm, this time it came around, I'll Try that tonight.

---

### Post by Alex&amp;Linux on 2007-06-20
Sweet!

---

### Post by fede on 2007-06-21
Hello, 

I hope you've got your sound fixed once and for all. In my experience, sound would work or not upon reboot: ie sometimes it did and after rebooting it didn't, or viceversa. Sometimes it would work (or not) for several consecutive reboots. It seemed to be entirely random.

I had also an onboard via card, disabled in the BIOS. The problem was that sometimes the VIA sound driver was loaded instead of my pci sound card driver. I guess that it depended on which one loaded first - and only one was loaded. The via driver would load regardless of being disabled in the BIOS, and when it did, it blocked the other card's driver from loading.

The permanent solution was to blacklist (ie permanently disable) the via driver, by adding:

```
blacklist <<module name>>
```

to the file blacklisted under /etc/modprobe.d directory. <<module name>> was the via sound card's module name, I don't remember the module name presently since I've changed motherboards and the line is no longer there. As far as I understand it, this blocks your system permanently from loading an undesirable driver, which in my case was the VIA driver and might also be a problem in yours, if you happen to still have sound problems later. 

Or maybe it might help someone else. Good luck.

---

