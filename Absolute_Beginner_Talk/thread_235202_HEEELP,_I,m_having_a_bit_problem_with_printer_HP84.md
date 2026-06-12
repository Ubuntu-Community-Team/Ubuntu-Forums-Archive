---
title: "HEEELP, I,m having a bit problem with printer HP840c"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by jaszman on 2006-08-12
And I know that I have to check the post but, none seem to talk about this, maybe I missed it maybe not...

Problem
No printer installed under Dapper Drake
Tried going to Sysytem/Administration/printing
Surprise ERROR-The CUPS server could not be contacted
Went to Synaptic
searched printer drivers
everything on the list is installed
Did Forum search
yadayada, found stuff on HP went to hplip-1.6.7tar.gz
downloaded it, its sitting in the Firefox box.
Don't know what script to run it with..jaja
Anyway decided to go back to the Forum found the user guide
It says
"How to install cupsd

    Cupsd should be automatically installed during standard instaltion. Checkout if there is a file "/etc/init.d/cupsys". If you want to manually install it, do 

 sudo apt-get install cupsys*

[edit]
How to add a printer

    In gnome click on "System/Administration/Printing. And choose "Add printer". A "add printer wizard" should start and tell you what to do. 

[edit]
Did the check cupsys is there, I ran the sudo and installed cupsys it ran but didn't install anything new.

I can't do the clicking because I get the error, any ideas?
I just want to print my thesis.
so again, HEEELP!

jaszman

---

### Post by taurus on 2006-08-12
Is it a USB or a parallel printer?  After cllicking "Add Printer" icon, tell it that you have a local printer and it should be able to search for you.  Just pick HP and the right model or something closest to your model.  No need to install any extra driver because it should come with a recommandation one for you.

---

### Post by jaszman on 2006-08-12
The thing is its not letting me add a printer, it just throws that error the CUPS server could not be contacted.

In Breezy Badger, its would configure my HP 840c as a HP895ex and its would work great, just add printer install driver and done. But Dapper Drake wont let me even add the printer.

---

### Post by jaszman on 2006-08-12
Huh, sorry, its a parrallel port and its works fine, I checked on the other machine, the one that has Breezy Badger on it and it configured the printer just fine. DD doesnt see it and when I try to print in OpenOffice it says no printer intstalled.

---

### Post by taurus on 2006-08-12
Do you have CUPSD running at all?  You may need to use apt-get/aptitude/synaptic to install it first before you can add a printer to your machine...

---

### Post by az on 2006-08-12
> **jaszman said:**
> And I know that I have to check the post but, none seem to talk about this, maybe I missed it maybe not...

Problem
No printer installed under Dapper Drake
Tried going to Sysytem/Administration/printing
Surprise ERROR-The CUPS server could not be contacted


That is the problem.  That shouldn't be.

Do you have the ubuntu-desktop package installed?

Boot the live cd and try to print something.  It should work out-of-the-box.  I'm sitting four feet away from one (Deskjet 842c).

---

### Post by Drakkor on 2006-08-13
I have an 845c and it works perfectly.

---

