---
title: "Stuck at 'Resizing Partition' screen whilst trying to install..."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by CAD-MAN on 2007-09-15
Hi

I'm currently trying to install Ubuntu alongside Vista in a dual boot configuration on my new laptop. I'm using the alternate CD because I'm following [this guide for Dell 1520 laptops.]("http://ubuntuforums.org/showthread.php?t=501195")

Basically, after selecting the time zone, country, keyboard layout, etc, the CD goes into creating a partition for itself. I went with the 'guided' option (but am now wishing I just went with manual). It starts partitioning, and was stuck on 0% for a few minutes. Just when I thought something might have been wrong with it, it jumped (almost instantaneously) to 100%. The trouble is, it has been stuck on 100% for an hour and a half.

Basically, I'm just looking for advice on what to do now. Do I leave it (in the hope that it may actually be doing something useful, but just not displaying its progress properly), or do I kill the power to my laptop. Would doing the latter pose a significant risk of damaging my hard drive?

Thanks in advance for any help offered.

---

### Post by CAD-MAN on 2007-09-15
Any ideas? :(

---

### Post by CAD-MAN on 2007-09-15
Well, I accidentally hit the magic button, and no damage appears to have been done.

I'll, err, just try and install again :)

---

### Post by Skidpad on 2007-09-15
I don't have any experience with Vista yet, but do note that in XP, many (including me) had laptop installation troubles due to the page and hibernation files.  These files/features often need to be temporarily turned off to allow the Windows files to me moved to the "left" side during disk defragmentation.  You may want to check this, but again I don't have any installation experience with Vista yet, so YMMV.

---

### Post by CAD-MAN on 2007-09-15
Sorry, im a bit of a newbie when it comes to installing operating systems and such (actually, this is my first time!), so could you please expand a bit and put it in simple terms please?

By 'the left', are you saying that Windows needs to be on the first partition in the hard drive?

Thanks

EDIT: Im trying the install again, and whilst running the installation process (after choosing my location and keyboard set-up), I was given the following error:

> Network Autoconfiguration Failed
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.

From here you can choose to retry DHCP network autoconfiguration (which may succeed if your DHCP server takes a long time to respond) or to configure the network manually. Some DHCP servers require a DHCP hostname to be sent by the client, so you can also choose to retry DHCP network autoconfiguration with a hostname that you provide.

Network configuration method:
**[Retry network autoocnfiguration]**
**[Retry network autoconfiguration with a DHCP hostname]**
**[Configure network manually]**
**[Do not configure the network at this time] **


Well, I don't understand a word of that, so can anybody enlighten me please?

Thanks

P.S. the bold text inside the "[ and ]" brackets are the options that I can choose from

---

### Post by Skidpad on 2007-09-15
No problem cad-man.  When I say "to the left" I mean al files have been consolidated to the left side of the Windows defragmentation window.  See [This Link]("http://www.linuxdevcenter.com/lpt/a/6554") for more info.

Regarding your network setup, I would skip it for now and configure it manually once the installation is done - select the bottom option in the **bold** portion of your post.

---

