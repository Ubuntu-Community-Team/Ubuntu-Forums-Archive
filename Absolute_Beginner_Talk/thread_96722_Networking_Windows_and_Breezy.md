---
title: "Networking Windows and Breezy"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by tacidsky on 2005-11-29
Hello,
For a project in school I was given a computer, had to install breezy on it. that is complete. 
now i am trying to network it.

i have a netgear hub(not router)

is it possible to network breezy, with a windows xp pro (ntfs) computer? if so what do i need? 


-tyrel

---

### Post by Aenyn on 2005-11-29
It'll likely already be on the network, assuming you're using workgroups.  Open Nautilus => Ctrl + L =>  smb://[computer name]/

You can also do samba sharing to allow your linux box on the windows network.  I've not yet fooled around with allowing access from a windows box to my ubuntu box, but I'm sure it's pretty simple.

---

### Post by The Mekon on 2005-11-29
I suggest that first you look at the Ubuntu 5.10 Starter Guide by clicking on the lifebouy on the top menu bar.  Next go to Networking and the Samba Server section where you will get a comprehensive guide to manually setting up Samba.

---

