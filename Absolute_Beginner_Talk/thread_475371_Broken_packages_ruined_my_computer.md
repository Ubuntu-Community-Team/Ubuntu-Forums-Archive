---
title: "Broken packages ruined my computer"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Spensawr on 2007-06-16
So I log in today to see the update manager tell me I have 5 broken packages, which is something I've experienced once before a while ago. I put whatever it tells me to in the terminal which didn't work (just like last time) and so knowing what to do from searching in the forums I went to synaptic and clicked fix broken packages and applied. 

As it ends up synaptic got rid of things such as: nautilus, network manager, cups and a bunch of other stuff and I don't have internet (because no network manager) to reinstall them. Any help would be appreciated as this is extremely frustrating. Thanks.

---

### Post by Jimmyfj on 2007-06-16
Try this in a terminal

sudo dpkg-reconfigure - Don't remember but I think there must be a -a parameter at the end of the command giving you: sudo dpkg-reconfigure -a

This will take a while to complete but I managed to rescue my broken system that way

---

### Post by Spensawr on 2007-06-16
> **Jimmyfj said:**
> Try this in a terminal

sudo dpkg-reconfigure - Don't remember but I think there must be a -a parameter at the end of the command giving you: sudo dpkg-reconfigure -a

This will take a while to complete but I managed to rescue my broken system that way

It didn't seem to help :(  I'll just reinstall again. Thanks a ton though, and I totally dig your sig. Good thing I keep all my important stuff on my mac. ;)

---

### Post by 5-HT on 2007-06-16
You can check your apt logs in /var to see what exactly was uninstalled, but I have a feeling that it may be ubuntu-desktop. If you still have all the packages in your cache, you could try reinstalling it (or just the packages that were uninstalled). If not, you could try reinstalling ubuntu-desktop or the removed packages from an install CD if handy.

FWIW: Aptitude has a great resolver that could help avoid issues like this.
cheers,

---

### Post by Spensawr on 2007-06-16
> **5-HT said:**
> You can check your apt logs in /var to see what exactly was uninstalled, but I have a feeling that it may be ubuntu-desktop. If you still have all the packages in your cache, you could try reinstalling it (or just the packages that were uninstalled). If not, you could try reinstalling ubuntu-desktop or the removed packages from an install CD if handy.

FWIW: Aptitude has a great resolver that could help avoid issues like this.
cheers,

I'm reformatting as we speak but I'll look up Aptitude, I haven't heard of it.

---

