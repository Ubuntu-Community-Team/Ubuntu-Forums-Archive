---
title: "[SOLVED] composite extension unavailable!"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-13
im trying to setup compiz on my pc but when i go to System > Preferences > Appearance, selecting the Visual Effects tab, and selecting Custom at the bottom i get an error message stating that the "composite extension unavailable" i believe this is down to my graphics card but i have installed the restricted drivers as necessary 

Any help would be greatful

ps:i think my graphics card maybe ATI?

---

### Post by n3tfury on 2007-10-13
i ran into the same problem today setting up my frien'ds PC with gutsy.  he's got an ATI card also.  i checked the forums and came upon this which worked for me:

> **cifrancgx said:**
> I have a Dell Optiplex 745 that has a ATI X1300 in it and I am running Gutsy 7.10.  

I was also getting the Compsite Extention not available message.

I now have it working.

In order to get the desktop effects to work I first had to install the ATI driver using the Restricted Drivers Manager.

Then I had to install ***xserver-xgl*** using the Synaptic Package Manager located under *System-->Administration-->Synaptic Package Manager*. Just do a search for xserver-xgl in the Synaptic manager to find it.

While you are there you might want to install the ***compizconfig-settings-manager*** as well.

After those are installed reboot and then you should be able to select *Extra *in the *Visual Effects* tab under *System-->Preferences-->Appearance*.

Worked for me.

To run the CompizConfig Settings Manager, you just run /usr/bin/ccsm  (I created a entry for it in the menus using the *System-->Preferences -->Main Menu* tool.

Hope that works for you.

I am new to this so if there is an easier way to do this let me know.

---

### Post by kamitsukai on 2007-10-13
wow yay!!!! thank you sooooooooo much :P

---

### Post by n3tfury on 2007-10-13
thank cinfrancgx, i'm only passing it on :)  if this works for you, can you mark your thread as solved?  thanks!

---

### Post by seijling on 2008-03-09
This really made all the difference to me.  Thank you again!

Mike

---

