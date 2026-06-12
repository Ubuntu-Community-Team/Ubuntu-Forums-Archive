---
title: "How to Uninstall Azureus ?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-24
I checked both in Synaptic and Automatix and Add/Remove,but the little square box is not colored in,so I guess they don't recognise that I do have it installed ! Also tried this:
drakkor@drakkor:~$ sudo apt-get remove Azureus
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Azureus   :confused:

---

### Post by Paerez on 2006-07-24
how did you install it in the first place?

---

### Post by The Seeker on 2006-07-24
sudo rm -rf /opt/azureus
sudo rm -f /usr/share/applications/azureus.desktop

---

### Post by Roasted on 2006-08-04
Just curious, I found this thread in search and it helped, thanks. But in the future if I wanted to delete something, like say I wanted to delete wine. Would I use those SAME commands except replace Azureus with Wine to uninstall + remove programs?

Also - In terminal when I put those 2 command lines in to remove Azureus, it didn't say anything. It just showed no response when I hit enter. But right after I tried to ALT F2 and find Azureus and it was gone. Yay. But why didn't anything show up? Just curious.

---

### Post by Paerez on 2006-08-04
nothing showed up because it had nothing to say (i.e. there were no errors removing the program).

No, you cannot just replace "Azureus" with another program name. You should always remove programs with the same method you used to install them (usually Add/Remove Programs or Synaptic or Aptitude). That is the only way to make sure you get a clean remove.

Azureus here is an exception because I think he installed azureus from a non-ubuntu package.

---

### Post by Drakkor on 2006-08-04
Yeah,ummm, can't remember,but it'a all fixed now after uninstalling several times and getting rid of all the dependencies , so now I actually have a working Axureus.Perseverance pays off ! :p

---

### Post by Astarroth on 2008-03-07
I was looking for this information too! Thanks for the information\\:D/

---

