---
title: "a dream project"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-20
I have an idea and need help finding any guides or outlines on how I might accomplish my idea.

I want to burn a DVD with Ubuntu and the associated programming on it that is bootable. All data such as saved email and favorites or other particular saved data would be directed to the hard drive. The purpose of this is to eliminate the possibility of any bugs worms viruses or other invaders plus hitting the wrong key and scrambling the system. At worst you might have to reboot. Granted there would be no adding or removing of programs but thats not important. A new burn would take care of that.

Wife and grandkids need this. Anyone got any suggestions

Thanks

---

### Post by EdThaSlayer on 2007-01-20
Quite interesting. The OS itself is on a dvd while the application data and personal data is on the hard drive. Sorry, I can't help, but it does sound like a interesting idea.

---

### Post by mcglnx on 2007-01-20
You can have a look at Tripwire: [http://www.tripwire.com/index.cfm](http://www.tripwire.com/index.cfm)

The idea is to detects filesystem modifications... could help!

---

### Post by mcglnx on 2007-01-20
Or this one: [http://www.cs.tut.fi/~rammer/aide.html](http://www.cs.tut.fi/~rammer/aide.html)

---

### Post by jvc26 on 2007-01-20
Is basically what you are considering a DVD UA install (Unattended) Like the ones offered by WPA for windows and the like? I'd be very interested if you could get one - are you suggesting, a DVD which has the OS on it, also other main apps, and your backed up docs? Then you burn the docs settings and favourites etc to the HDD during the install and get the OS all up and running in one straight install. You can definitely do this in windows - I've done it myself, but not sure about linux,
Il

---

### Post by tagra123 on 2007-01-20
You  can do exactly what you are trying with the live cd.  I believe you press F12 or F6 (one of those) something like that and add persistent at the end.

You also need to create a usb stick/drive or hard drive -- I think it needs to be labeled casperrw

I used reconstructor and added the persistent as a boot options for the kids. reconstructor lets you create a live cd with your favorite programs.

A quick google jsut found the page I was thinking of.

I've done this and have a system that can be used this way.

Whats really cool is that you can take the usb and live cd and bootm computers with similar hardware and have all your settings. If you go to a computer with a different graphics you will need to reconfigure your graphics card. I suppose a workaround to the graphics card thing would be to use a low resolution setting and use vesa -- just thinking out loud here.

Anyway here's the link.

(EDITED) -- Included the wrong url
Persistence
[http://ubuntu.wordpress.com/2006/02/14/persistent-settings-and-files-with-livecds/](http://ubuntu.wordpress.com/2006/02/14/persistent-settings-and-files-with-livecds/)


Backups
[http://www.ubuntuforums.org/showpost.php?p=1402091&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1402091&postcount=1)

Reconstructor
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

using the persistent mode you can still add programs using apt.

---

### Post by squrl on 2007-01-20
Not quite.   The OS with whatever apps you used like thunderbird or whatever configured and burned to DVD. All the users data like emails or favorites stored on the hard drive. 

To use the system you boot your DVD and it would direct the programming to your hard drive space for your personal data. If things crash you just reboot. The worst that could happen id the loss of your personal data. 

Each person would have their own DVD. The data would be in their personal directory of the hard drive. You would only have access to your personal area of the hard drive. 

Might be a lot of work to set up but it would save a lot of headaches with the kids crashing the system but would also keep them out of each others files. 

Just an old man's dreams surfacing.

---

### Post by aysiu on 2007-01-20
Knoppix makes this really easy.

---

### Post by Duck2006 on 2007-01-20
If trgra123 does not work for you, you may find with the dd commands you can get it done

[http://www.linuxquestions.org/questions/showthread.php?t=362506](http://www.linuxquestions.org/questions/showthread.php?t=362506)

This may help

---

### Post by tagra123 on 2007-01-20
Here's the correct url for persistence

[http://ubuntu.wordpress.com/2006/02/14/persistent-settings-and-files-with-livecds/](http://ubuntu.wordpress.com/2006/02/14/persistent-settings-and-files-with-livecds/)

I also edited th post above

---

### Post by squrl on 2007-01-20
Thanks to all.    I think I have enough info to do the deed. 

Dapper plus livecdpersistence may just be the answer.

Thanks again

---

