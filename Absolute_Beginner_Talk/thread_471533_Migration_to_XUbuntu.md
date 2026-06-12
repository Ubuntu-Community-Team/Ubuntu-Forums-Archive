---
title: "Migration to XUbuntu ??"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by s_raghu20 on 2007-06-12
Hi Guys,

I have some storage issues (dont have much hdd space available) and wonder if it would be worth moving to Xubuntu.. I understand it takes less resources...

Current Ubuntu is running in a VMWare virtual machine.. dont want to remove that installation and redo all of the new one... Is there a way to do it relatively simpler... 

regards
raghav.

---

### Post by Tux Aubrey on 2007-06-12
I really don't think you'll save much HDD space switching desktops.  xubuntu is less resource hungry in terms of processor and RAM demands.  Its the apps that are chewing your storage space so the first step would be work out what you don't need and then apt-get uninstall remove each one.  You could then switch some of those you do need to less bloated equivalents - like ditching OpenOffice for Abiword or Firefox for Seamonkey.

---

### Post by huygens on 2007-06-12
I agree with Tux Aubrey. Using Xubuntu will spare some resource while running. However, you have a problem of storage resource (so offline data), basically changing of Desktop won't change this fact...

As Tux Aubrey suggested, you should try to clean up your list of installed applications. Check this [guide on how to clean up your repositories]("http://www.berthon.eu/wiki/foss:ubuntu:aptclean"). It is not complete, but might help you get rid of unnecessary files.

In addition, you could look in the Synpatic application (in the Gnome desktop menu, System -> Administration -> Synaptic Package Manager). Once Synaptic is launched, in its Settings menu, there is a Preferences item, select it. A preferences dialog box appears and you have to switch to the "Files" tab. There, there is a "Delete cached package files" which you can safely used. It will deleted some "cache" that Synaptic was using to download files.

Once you applied the above guide + the tip about cache files, you should have hopefully much more spaces.

---

