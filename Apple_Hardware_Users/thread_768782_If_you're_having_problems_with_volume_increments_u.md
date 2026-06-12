---
title: "If you're having problems with volume increments using pommed..."
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by CodeSamurai on 2008-04-26
Hey all.  When I installed 8.04 on my 3,1 macbook pro and then installed pommed, I had some really strange volume problems including bad adjustment, non-audible ranges and "popping".  Here's how I fixed them:

Open volume control, then make sure your selected device is HDA intel.

Right click on the volume icon on your bar and select preferences.  Set your selection to "Master".  

Go to System>Preferences>Sound and set your device to PCM.  

Open a terminal:
> sudo gedit /etc/pommed.conf 

Go to the audio section and set the step value = 3.  Make sure your mixer element for volume adjustment is "PCM".  Save and close.  

Uninstall pommed:
> sudo apt-get remove pommed

Reinstall pommed
> sudo apt-get install pommed

Log out and back in.

The reinstallation of pommed starts using the new conf file.  Not sure what the deal is there. After I did this, i was able to adjust the volume correctly.  In the volume controls, I set "Master" to a little below full, PCM is adjusted by you, and Front all the way to full.  Sorry if any of this is confusing.  I'm getting back into the swing of ubuntu information, it might take me a bit. 

Trent out

---

### Post by dustynus on 2008-05-17
Awesome nice fix. Worked great for me. I had the same problem, glad you found the solution :)

---

### Post by cyberdork33 on 2008-05-17
you shouldn't have to completely reinstall though, just restart pommed.

---

### Post by Rog-Mahal on 2008-06-01
I tried your fix and I still have the same problem, it seems like the problem is my volume controls raise or lower both the Master and PCM controls at the same time which causes the big increases and decreases. Any thoughts? Is there a way to unlink them?

---

### Post by cyberdork33 on 2008-06-01
System > Preferences > Sound

At the bottom you can select the channel(s) that your keyboard adjusts.

---

