---
title: "Dual boot: what's the easiest way to switch?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by tolremeno on 2007-07-06
I'm dual booting Feisty and xp pro. I have to have xp for proprietary office stuff that won't work in wine.

But I want to stay in ubuntu as much as I can, so I'm wondering: what's the easiest/quickest/best way to go back and forth between the two? 

Or is there really only one option: hitting restart every time?

---

### Post by Cypher on 2007-07-06
Since you aren't running Ubuntu within a virtual machine on XP or vice versa, you're going to have to restart.

---

### Post by Maxtorm on 2007-07-06
Another option is not to dual-boot at all.  Use VMWare Server to run your Windows XP install inside your Ubuntu session.  Easiest way to install VMWare is through Automatix ([www.getautomatix.com](www.getautomatix.com)).  Once you have it up and running, you can delete your Windows XP partition altogether and expand your Ubuntu partition to use the newly found space.

---

### Post by Raineer on 2007-07-06
> **Cypher said:**
> Since you aren't running Ubuntu within a virtual machine on XP or vice versa, you're going to have to restart.

Which makes the answer, VMWare :)

Just run XP inside of Ubuntu, works like a charm. Alt-tab between operating systems works nicely for me.

---

### Post by AlexenderReez on 2007-07-06
> **tolremeno said:**
> I'm dual booting Feisty and xp pro. I have to have xp for proprietary office stuff that won't work in wine.

But I want to stay in ubuntu as much as I can, so I'm wondering: what's the easiest/quickest/best way to go back and forth between the two? 

Or is there really only one option: hitting restart every time?

try to learn about VMware or virtual box....search using google.com to find it.....

---

### Post by candtalan on 2007-07-06
This recent article looks interesting and you might also be interested:
It gives what looks like a good walkthrough to using the vmware-server:

'10 minutes to run every Windows app on your Ubuntu desktop'
[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)

hth

---

### Post by tolremeno on 2007-07-06
Thanks! I'll look into it!

---

### Post by Old Pink on 2007-07-06
> **candtalan said:**
> This recent article looks interesting and you might also be interested:
It gives what looks like a good walkthrough to using the vmware-server:

'10 minutes to run every Windows app on your Ubuntu desktop'
[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)

hth
I was going to link that ;) 

Just stick a start bar on your desktop and have them both together. May be a bit slow, but worth a shot.

Personally I'd say loose Windows and go 100% Ubuntu, but that's just me. ;)

---

### Post by tolremeno on 2007-07-06
> **Old Pink said:**
> Personally I'd say loose Windows and go 100% Ubuntu, but that's just me. ;)
I wish I could, but this computer has to be used for work, and some of the work programs are very windows specific (requiring ie, among other things).

---

### Post by p_quarles on 2007-07-06
> **tolremeno said:**
> I wish I could, but this computer has to be used for work, and some of the work programs are very windows specific (requiring ie, among other things).
Just FYI, you can use IE6 under Wine. Not a reason to get rid of Windows, if you need it for other things, but that might help you cut down on the time you spend with it. :-)

---

