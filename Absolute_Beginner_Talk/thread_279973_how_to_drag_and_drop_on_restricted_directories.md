---
title: "how to drag and drop on restricted directories?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by scuzzo84 on 2006-10-18
Say I have some icons and I want to copy the directory of icons to /usr/share/icons is there anyway to do this? I mean I tried it but the message "error while copying you do not have the permissions" 

I could use terminal with sudo but how come it cant popup the gksu or enter admin pass box?

---

### Post by Tomosaur on 2006-10-18
Unfortunately not, it's one of the biggest complaints with Nautilus (the file manager). You either have to start nautilus with root permissions (by typing 'gksudo nautilus' in the command line), or do all your file operations within the command line.

---

### Post by PriceChild on 2006-10-18
Please be very careful while root in nautilus, its easy to forget :)

Close it as soon as you're done.

---

### Post by Malakia on 2006-10-18
Here is the link for a whole bunch of bash commands, they have come in handy many times and you don't have to worry about being in root because I use sudo.

[http://gd.tuwien.ac.at/linuxcommand.org/lts0050.html](http://gd.tuwien.ac.at/linuxcommand.org/lts0050.html)

---

### Post by aktiwers on 2006-10-18
Yes I use the one from Automatix alot. "Sudo nautilus here"  Love it!

---

### Post by scuzzo84 on 2006-10-19
> **aktiwers said:**
> Yes I use the one from Automatix alot. "Sudo nautilus here"  Love it!

Huh? I am lost. The automatix nautilus is different? Would it solve my problem? Please elaborate :)

---

### Post by aysiu on 2006-10-19
The command you're looking for is *gksudo nautilus*, not *sudo nautilus*. I'm not sure what that has to do with Automatix, anyway.

Press Alt-F2 and type ```
gksudo nautilus
``` in the dialogue that pops up.

If you like it enough to want to do it often, you can create a launcher with that command or a keyboard shortcut for it.

---

### Post by orb9220 on 2006-10-19
Or you can just drag a places item like computer or home folder icon to panel
Then right click properties and change command to:

gksudo nautilus

Now when you click on icon it will ask for password then launch a sudo nautilus that will allow you to drag and drop files anywhere. Also will allow you to delete or copy anything.

And as pricechild quoted be careful since you can also delete critical system files.

But it is the only way to have a file manger like xp that allows you to copy and delete anywhere.

---

### Post by aysiu on 2006-10-19
There is a difference between *sudo* and *gksudo*--probably won't make a huge difference for Nautilus in particular, but in general, you should get in the habit of using *gksudo* for graphical applications.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dannyboy79 on 2006-10-19
> **aysiu said:**
> The command you're looking for is *gksudo nautilus*, not *sudo nautilus*. I'm not sure what that has to do with Automatix, anyway.

This is because Automatix has an option in it to install bash scripts that will add an entry into a right click menu when you're in Nautilus that will allow you to open Nautilus at that location with sudo capabilities.

---

### Post by aktiwers on 2006-10-20
> **dannyboy79 said:**
> This is because Automatix has an option in it to install bash scripts that will add an entry into a right click menu when you're in Nautilus that will allow you to open Nautilus at that location with sudo capabilities.

Yes exactly! Sorry for not being more clear. But it is a great script though :mrgreen:

---

