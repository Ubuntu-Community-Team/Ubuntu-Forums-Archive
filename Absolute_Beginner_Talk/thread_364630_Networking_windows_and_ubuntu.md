---
title: "Networking windows and ubuntu"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-02-18
I would be grateful if anybody could provide info or point me towards a solution.

Currently I have a desktop PC running Ubuntu 6.10. This is wired into the router via the ethernet port. I have installed samba (through synaptic) but gone no further.

I also have a laptop running Windows XP. This is connected to the router via a USB wireless adapter.

Both computers have access to the internet.

How do I set them up so that the Windows pc can read files from ubuntu, and so that the desktop (ubuntu pc) can see files on my laptop.

Please make any instructions idiot proof as after "googling" for a solution I have come up empty handed.

Many thanks

nathan

---

### Post by jonathan.lees on 2007-02-18
The Ubuntu Edgy guide has really easy to follow instructions on setting up Samba for sharing folders in Ubuntu to access on XP:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Edgy#Samba_Server)

And for XP shares you can use CIFS to mount them in Ubuntu, see this thread here:

[http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

---

### Post by V-600 on 2007-02-18
thanks. will try now.

---

### Post by WinterWeaver on 2007-02-18
May I recommend that you also install *Network Manager,* as this help with your network connection between the two. Before I installed Network Manager, I had many connection problems between the two.

---

### Post by V-600 on 2007-02-18
Thanks. Could you elaborate on network manager. Where do i get it.

I had a good go at the two links but ended up getting rather confused and gave up.

---

