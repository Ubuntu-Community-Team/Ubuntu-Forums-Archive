---
title: "Dvd Drive Problems"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by metalfanatic07 on 2007-06-10
I'm at a total loss here. my DVD drive won't play dvds and i've tried every freaking program and plugin out there and still no results. what do i do now?

---

### Post by johnny4north on 2007-06-10
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2) go to this link and install automarix.  here is the link to complete how to for automatix =http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html
you need to install the plug-ins using automarix...:)

---

### Post by eagleeyed on 2007-06-11
Believe me, I had the same exact problem you were having.

I finally found out what was causing it.

Xine always tries to access the DVD's with the mount point /dev/dvd/ or something like that.
However my drive was not doing it this way, my drive was making it /media/disk name.

Here is how I fixed it.  Hopefully this helps you and if there is a better or easier way please tell me.

1. With a DVD in the drive go to Places> Computer, right click on the drive you play dvd's from, then in the last tab labelled 'Volume' look at the information in Mount Point.  If it says '/dev/dvd' i cannot help you, however if it says '/media/disk name' or something simular continue.

2. If it is not saying '/dev/dvd' go to the tab 'Drive', then click the setting's drop down menu, then enter in Mount Point 'dvd' without the '.

3. You will need to eject the disk then put it in again to reset it.

4. When the disk has been read again, go back to the drives properties, go to volume and take note of the new Mount Point.

5. Next open up 'Kaffeine', Go Settings>xine Engine Parameters.  Now click the Media section.  If you have a look you will see an input box labelled dvd.device, enter the new mount point there.

That is how I got mine working, hope it works for you.

---

### Post by compiledkernel on 2007-06-13
Uh yeah -- 

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624) 

Gives you all the needed stuff for DVD playback.

---

