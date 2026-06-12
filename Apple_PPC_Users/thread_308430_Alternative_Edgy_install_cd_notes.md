---
title: "Alternative Edgy install cd notes"
date: 2006-11-28
forum: Apple PPC Users
---

### Post by stream303 on 2006-11-28
Even though my G5 iMac boots from the normal desktop live cd, I thought I'd give the *alternative* text-based cd a shot to see how it would work.

The first thing I noticed is that it would hang when detecting my Microsoft wheel-mouse.  (debounce errors leading me to believe something wrong with keyboard, mouse)

I did not follow through with a full installation, but did have **success** only when I **left nothing but my ethernet cable and keyboard attached.**  Voila! 

I'm going to assume that the mouse would work later, but I didn't go that far.  Of course the G5 iMac fans were screaming, but that can be easily fixed after install by either recompiling a fresh 2.6.18.x kernel, or just simply following these instructions for loading the module manually for the stock edgy kernel.  (These forums rock!)

For G5 iMac owners:
> Immediately control the fans
1) sudo -s (get into a root shell)
2) cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
3) ls | cut -d. -f1 | xargs -n1 modprobe

Make sure fans are controlled at boot:
lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules

Maybe this will help someone get over that first hurdle on a different Mac using the alternative cd....

**UPDATE:** I finally did a full install onto a firewire drive and have yet another tip:
Seems that "testing" the keyboard would lock, so I just accepted what was offered without trying a typing test.
Also, when the system says "wait...." at some points it really means it - like 10 minutes or so, so don't be to hasty to shut down thinking it is locked up. :)

---

### Post by stream303 on 2006-12-08
Update: Got the alternate cd install fully booting on an external firewire drive.
[http://www.ubuntuforums.org/showthread.php?t=314237](http://www.ubuntuforums.org/showthread.php?t=314237)

Also noted that the alternate cd installation correctly determined my 20" iMac's video resolution, whereas with the live-cd, I had to do it manually. (sudo dpkg-reconfigure -fgnome -phigh xserver-xorg)

---

