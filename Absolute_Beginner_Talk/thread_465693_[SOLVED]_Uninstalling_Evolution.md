---
title: "[SOLVED] Uninstalling Evolution"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-06
While uninstalling evolution, aptitude also tries to remove 
```
evolution-exchange
evolution-plugins
ubuntu-desktop
contact-lookup-applet recommends evolution (>= 2.0)
evolution-common recommends evolution
nautilus-sendto recommends evolution (>= 2.4)
openoffice.org-evolution recommends evolution
nautilus-sendto
evolution-common
```
I am ok with everything else except nautilus-sendto and contact-lookup-applet. The nautilus send to currently sends to Evolution (Email) and to my Bluetooth phone via gnome-obex-push. If i remove this package, will my send to bluetooth (which i use heavily) still work ?

Also does anyone know what openoffice.org-evolution and contact-lookup-applet are used for?

---

### Post by bobbybobington on 2007-06-06
I would be worried about it trying to remove ubuntu-desktop!
I would think if that was uninstalled, you would be left with Command line

---

### Post by Inxsible on 2007-06-06
> **bobbybobington said:**
> I would be worried about it trying to remove ubuntu-desktop!
I would think if that was uninstalled, you would be left with Command line

no ubuntu-desktop is a meta-package which only points to which packages should be installed on installing Ubuntu. Removal of ubuntu-desktop doesn't remove the GUI. 

Removal of it can cause issues when you upgrade your OS -(for eg Feisty --> Gutsy), but i dont plan to do that. I will perform a fresh install if and when Gutsy releases.

---

### Post by Inxsible on 2007-06-06
Or can I uninstall nautilus-sendto now, and after I uninstall evolution, i can re-install nautilus-sendto by
```
sudo aptitude install nautilus-sendto
```

Will this put my sendto Bluetooth device in there again ?

---

### Post by Inxsible on 2007-06-07
Bump. Anyone?

---

### Post by Inxsible on 2007-06-07
Bump again !

---

### Post by fatsheep on 2007-06-07
If no one replies it's probably because nobody knows.  Neither do I.  Why don't you try removing evolution and reinstalling nautilu-sento and then if it removes your sento Bluetooth device capabilities then reinstall evolution?

---

### Post by TriggerHappyChewie on 2007-06-07
Just try it! :D

---

### Post by gridsleep on 2007-06-09
Thanks for the info on ubuntu-desktop.  I want to uninstall Evolution, which is about as useful to me as Lotus Notes.  I use Thunderbird, and that's all I need.  With all those other dependencies listed when attempting uninstallation, I was fearing Evolution was as tightly integrated into Ubuntu Linux as Internet Explorer is into Windows.  Which thought led me to suspect that Novell is involved with Ubuntu design and distribution, or, at least, influential over it.  I would hate to think that this, the first Linux distribution that actually works more or less perfectly with all my laptop hardware, is under corporate influence.  Now, if Ubuntu would only work with the ATI Theater 550 Pro TV card in my workstation, and with my HP 6200C scanner via USB, it would be completely perfect and I could dispose of Windows once and for all.

---

### Post by RawMustard on 2007-06-11
You can get rid of all the evolution crap no problems.  Just re-install nautilus-sendto and your bluetooth stuff will work fine :)  Remember to killall nautilus for the changes to take effect.

Anyone know how to browse your phone via nautilus?

---

### Post by Inxsible on 2007-06-11
Done it already. Removed Evolution, serpentine and ubuntu-desktop. Everything works fine still. :D

---

