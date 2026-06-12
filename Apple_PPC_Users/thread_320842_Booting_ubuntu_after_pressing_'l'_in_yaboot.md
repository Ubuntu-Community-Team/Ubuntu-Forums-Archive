---
title: "Booting ubuntu after pressing 'l' in yaboot"
date: 2006-12-18
forum: Apple PPC Users
---

### Post by vengeance316 on 2006-12-18
I currently have Ubuntu and Mac OSX installed on my iBook. In the standard ubuntu yaboot setup, I would have to type 'l' for the linux menu, then 'Linux' to boot Ubuntu. I've used YellowDog on my iBook before, and the way it configures yaboot is to boot Linux after just pressing 'l'. Since I'm only using one version of Linux I'd really like to set up yaboot this way... does anyone know how it's done? Thanks...

---

### Post by linear on 2006-12-18
You could set the "timeout" parameter in yaboot.conf to a low number (it's in tenths of seconds). I don't know if "timeout=0" is valid, or will disable the timeout altogether.

---

### Post by handylinux on 2006-12-18
> **vengeance316 said:**
> I currently have Ubuntu and Mac OSX installed on my iBook. In the standard ubuntu yaboot setup, I would have to type 'l' for the linux menu, then 'Linux' to boot Ubuntu. I've used YellowDog on my iBook before, and the way it configures yaboot is to boot Linux after just pressing 'l'. Since I'm only using one version of Linux I'd really like to set up yaboot this way... does anyone know how it's done? Thanks...

Well, I'm just a beginner at this, but I've never had to do anything so complicated to get my iBook to start in Linux. It just does it automatically once I get yaboot to load instead of OS X.

I have Ubuntu installed on the 1st partition, Mac OS X on the 2nd. I have set it in firmware to start in Mac OS X (using the Startup Disk preference pane), so it starts in OS X automatically. If I want to start in Linux, I just press D on the keyboard during startup. This forces the Mac to start from the 1st partition, which loads yaboot, which then automatically starts up in Linux, without having to type anything. I can make it a little faster (a few seconds) by typing **l** in the first yaboot screen, then **return** in the second, but neither is necessary. Then when I restart, it goes back to Mac OS X, unless I press D again to start in Linux.

So it seems that Ubuntu's "standard yaboot setup" will automatically start Linux, without any instructions required. Maybe that differs from other distros; I have no experience with any, having just started with Ubuntu a week ago.

See my thread "[How to switch OS on dual-boot Mac?]("http://www.ubuntuforums.org/showthread.php?t=318682")" for more discussion.

---

