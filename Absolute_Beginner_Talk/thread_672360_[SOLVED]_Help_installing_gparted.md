---
title: "[SOLVED] Help installing gparted"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by dankdave on 2008-01-19
Hi,

I'm trying to install a second hard drive on my computer.  I have xubuntu 7.10 successfully installed on my pII computer with a 15gb hard drive.  I have a second 80 gb hard drive hooked up as the slave drive, now I'd like to format the drive so I can start using it.

I get the following error when I try installing gparted

dankdave@oldbruiser:/media$ sudo aptitude install gparted
[sudo] password for dankdave:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for gparted
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  

Any idea how I tell it where to look for gparted?

---

### Post by smartboyathome on 2008-01-19
I would suggest downloading GParted from getdeb.net (it is newer than the one in the repos). Get it [here]("http://getdeb.net/search.php?search_distro_id=5&keywords=gparted"). Just open it with GDebi (you should get a dialog box with an option to "open" it) and click install. It should now be available from the System Tools portion of your menu.

---

### Post by Aurora@FleetBuzz on 2008-01-19
You can also install via the Synaptic Package Manager.

---

### Post by dankdave on 2008-01-19
I was able to install gparted via the link you sent me.

Any idea why it said

"No candidate version found for gparted"?

---

