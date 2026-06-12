---
title: "Approprate size for a partition"
date: 2009-09-13
forum: Apple Hardware Users
---

### Post by Jakob H. on 2009-09-13
Hello,

I am just downloading the file "ubuntu-9.04-desktop-i386.iso" and have an empty DVD prepared. (I just couldn't find an empty CD.) As for now I just want to try Linux and see if I like it and keep Mac OS X 10.6.1 on the other partition.

I have got a Mac Mini (2nd gen) with a 2GHz Core 2 Duo CPU, 1GB RAM and no additional hardware besides a memory stick and a Huawei E169 to connect with the internet.

I have just upgraded to Mac OS X 10.6.1 and have carefully read the installation guide at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu)

I think that everything should work out fine. Maybe rEFIt will be a little tricky to install but I ought to be able to get it to work. Internet access would be nice but I can do without.

One question remains for me: My hard drive has a capacity of 120GB. Currently I have about 80GB free disk space. (No big downloads intended.) So how much disk space shall I allocate for Ubuntu in order to get a reasonable first impression? The recommanded 8GB don't appear much to me. I was thinking of 20, maybe 30GB.

Kind regards,
Jakob H.

---

### Post by SuperSonic4 on 2009-09-13
20GiB should be fine if you don't intend to download much (or store it externally). Ubuntu isn't too difficult to remove anyway

---

### Post by Jakob H. on 2009-09-13
> **SuperSonic4 said:**
> 20GiB should be fine if you don't intend to download much (or store it externally). Ubuntu isn't too difficult to remove anyway

Thank you. This solves my question.

Jakob H.

---

### Post by GadgetFreak on 2009-09-15
Jakob H,

Neat coincidence. I have the exact same Mac as you do, have just upgraded to Snow Leopard, and was doing a search to get a recommended HD partition size because I want to run Ubuntu also.

I'm going to try the 20GB partition for Ubuntu but, in my case, I'm after a server edition.

 I'm running an external firewire HD (Western Digital My Book Studio Edition 1TB). Mac OS X sees this no problem (original format on the drive) as does Xubuntu, which is just an Ubuntu variant for which I had a bootable "Live" CD (I could test if things would work without touching the Mac in any way). Xubuntu and, therefore Ubuntu will, see(s) the external HD so I suspect that both OS's can share the same external drive without having to partition it. (If anyone knows this not to be the case then please let me know. Perhaps there's something "hidden" here that I don't realize.) I'll report back on my success (or failure).

Please let me know, Jakob, how things work out on your end.
Thanks.

---

### Post by GadgetFreak on 2009-09-18
Followed instructions (link provided by Jakob H.):

[INDENT][/INDENT][https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu)

Ubuntu 9.04 server installation failed on first attempt because I panicked on the GRUB question in the installer. I thought, since I already had rEFIt set up, that installing GRUB would clobber it. That's not the case.

So, starting from scratch, the second attempt at installing Ubuntu 9.04 server went perfectly. Instructions (from above link) indicated to put GRUB into /dev/sda3, resulting in the correct behaviour.

A 20GB partition was allocated, in total, for Ubuntu and its swap, on the internal HD. rEFIt works fine and Ubuntu server seems to load up without issues. I'm not fully operational, however (and haven't done any serious testing except to say that Snow Leopard seems to be running fine on the internal HD!), since I still need to get my external HD configured and that's proving to need a bit of research. The issue is that Mac OS X uses "journaling" in HFS+ and Ubuntu cannot write to this (only read, evidently). Journaling can be disabled permitting both OSes full access, I believe. I question, however, the wisdom in allowing two operating systems full access to the same partition especially since I'm finding anecdotal evidence that Snow Leopard is doing something new in HFS+.

More on the external drive issue here...

[INDENT][/INDENT][http://ubuntuforums.org/showthread.php?p=7969693#post7969693](http://ubuntuforums.org/showthread.php?p=7969693#post7969693)

---

### Post by Jakob H. on 2009-09-19
@GadgetFreak 
I have to tell you that I still haven't tried to install Ubuntu on my machine. Some of my software (probably Vodafone Mobile Connect and possibly Skype) are doing unexpected things under snow leopard. rEFIt might cause even more trouble. So I decided to wait until new versions of my software are issued. 
Kind regards, 
Jakob H.

---

