---
title: "wireless internet in Ubuntu 7.04 on Parallels Desktop"
date: 2007-04-21
forum: Apple Intel Users
---

### Post by gotenks05 on 2007-04-21
I am having problems with the upgrade to Ubuntu 7.04.  I upgraded fine, but my wireless internet connection does not work anymore.  I installed Ubuntu in Parallels Desktop for Mac (for web development reasons) and the settings that I had it at with version 6.10, which is what I burned onto disc, worked perfectly to get connected to the internet and there were to icons on it.  However, after the upgrade, there was a tiny icon with an exclaimation point that said the network was not working well.  What can I do in Ubuntu 7.04 to make the internet connection work like it did in 6.10?  I might post this in the Parallels forum too, but this seems to be more of a Ubuntu problem than a Parallels problem to me.  Right now, I downgraded it back to 6.10, but an answer to this question is still necessary, in case anyone who visits my site needs help and they use version 7.04 instead of 6.10, and the problem was only in version 7.04 of Ubuntu.  Thanks in advance for any help or advice.

---

### Post by hajk on 2007-04-21
Used Bridged Ethernet setting in your VM. Once Ubuntu starts up in the VM, the connection appears as wired Ethernet (not wireless), but this is in fact a "tunnelled" Ethernet connection right through your Airport wireless connection. Of course, the Airport wireless in Mac OS X should be connected for this to work.

If this doesn't answer your question, may be you could rephrase what is was exactly that you were trying to do.

---

### Post by gotenks05 on 2007-04-22
> **hajk said:**
> Used Bridged Ethernet setting in your VM. Once Ubuntu starts up in the VM, the connection appears as wired Ethernet (not wireless), but this is in fact a "tunnelled" Ethernet connection right through your Airport wireless connection. Of course, the Airport wireless in Mac OS X should be connected for this to work.

If this doesn't answer your question, may be you could rephrase what is was exactly that you were trying to do.

I tried upgrading again, but your suggestion did not work.  You were right about me wanting to use my Mac's Airport.  I just installed Ubuntu 6.10 as a typical VM, so I could not configure the Shared/Bridged Ethernet until after the installation is complete.  It just worked after installing it, without needing to connect the Airport to Parallels.  That was the same way for the Windows installation.  That's kind of result I wanted.  Any other advice.

---

### Post by svenand on 2007-04-24
I have installed Ubuntu 7.04 on my MacBook using Parallels Desktop.
After I logged in to Ubuntu the network connection was disabled. When I
selected Wired Network from the popup menu the connection was established.
I am using a wireless network connection in Mac OS X.
See my blog: [http://svenand.blogdrive.com/archive/50.html](http://svenand.blogdrive.com/archive/50.html)

Sven

---

### Post by hajk on 2007-04-25
All you need to do to get the network (the virtual eth0 NIC) enabled automatically on boot is to ```
sudo apt-get remove network-manager
```which will also remove the Gnome or KDE wrapper.

---

