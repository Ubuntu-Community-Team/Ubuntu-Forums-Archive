---
title: "Noooooooooooooooooooooooooooo!!!!"
date: 2005-01-29
forum: Apple PPC Users
---

### Post by DirtDawg on 2005-01-29
Aw crap. 

I have an imac g3 that is NOT hooked to the internet.  I was working on it  earlier when the power went out. I went to use the computer again after the power came back on. The boot up went fine, then I put in my user name and password.  BUT, I got 3 error boxes. 

First: "There was an error starting the GNOME settings daemon. Some things may not work correctly, sound <etc, etc>. Gnome will still try to restart next time you log in.

Then: Nautilus can't be used now due to unexpected error from Bonobo when attempting to locate the factory. Killing Bonobo-activation-server and restarting Nautilus may help the problem.

Finally, and most foreboding: The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet"
 Details: Unknown COBRA exception id: 'IDL:omg.org/COBRA/COMM_FAILURE:1.0'
Do you want to delete the applet from your configuration? 

Then a couple buttons labeled "delete Appleet" and "don't delete applet"

Now, I am a semi-Linux-n00b and have no clue what any of this means, but it doesn't take Scotland Yard to connect these problems with the power outage (an external outage, nothing to do with our apartment). The computer is still running with all those boxes on a blank screen. I tried the "do not delete" option in that final box, but it just comes right back up. I am afraid to delete anything called "showDesktopApplet" Sounds important.

Question: Is there anyway to save this mess, or am I just screwed and need to reinstall the entire system :( ?

What a drag.

---

### Post by slux on 2005-01-29
These things may happen if your personal GNOME setting somehow become corrupt, removing .gnome etc. might well help. If it's worse, reinstalling a few packages  such as gconfd will most likely do the trick. 
 
If you don't have a really customized gnome I'd just try removing the relevant config dirs first. Most of the time this has been the easiest solution for me.

---

### Post by patrickallo on 2005-01-29
I've had exactly the same a few months ago... also with an iMac G3

The problem was - as I noticed later - due to date and clock-settings.
After power down date was set back to 1900 or something...
Setting the right date fixed the problem for me.

---

### Post by DirtDawg on 2005-01-29
Yes! You guys are awsome! I simply chose to delete the files it asked me about (it didn't go down easy, duplicate windows kept popping up asking the same question again and again). Then , the screen was blank and a bunch of the icons were missing or corrupt. But once I reset the date and rebooted, everything came up _exactly_  as it did before the outage!! 

 :-D  Thank you thank you thank you thank you thank you! :-D

---

### Post by bromo33333 on 2005-02-03
I have a Powerbook G3 Pismo (Running Warty right now) -- and had a similar issue with losing the date that I traced to the PRAM battery (In my case it prevented me booting!  :cry: ). 

 You may want to check into replacing the system battery so you won't lose the date when you power down - my previous iMac G3 was having similar issues with OS9 and the date resetting to 1904!.  It will cost about $20 or so to get a new battery, and will save you a *lot* of trouble!

I am also a noobie when it comes to Linux and am finding the Ubuntu Linux to be much better than OS9.2 which was on this book beforehand.

---

