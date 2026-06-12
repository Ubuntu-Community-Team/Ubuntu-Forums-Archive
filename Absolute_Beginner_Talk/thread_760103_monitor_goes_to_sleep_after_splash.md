---
title: "monitor goes to sleep after splash"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by tgood on 2008-04-19
Hardy 8.04 after the spash, the monitor gets an error message, "unknown mode going to sleep". I've tried typing in terminal: "sudo dpkg-reconfigure -phigh xserver-xorg".  That gets me this message: "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf. 20080419133348"

Graphics card is Geforce FX 5200

---

### Post by bwallum on 2008-04-20
Warning is normal. Run "sudo dpkg-reconfigure -phigh xserver-xorg". You will end up with a default US keyboard setup. If you are not US then you can change your keyboard like this:

[http://ubuntuforums.org/showthread.php?t=760401](http://ubuntuforums.org/showthread.php?t=760401)

To change your monitor setting (if you still need to) go to System>Preferences>Screen Resolution. It should stick in your xorg settings. Come back if it doesn't.
Regards
Bob

---

### Post by tgood on 2008-04-21
I should've been more specific.  When I try to reconfigure x, all I get is the warning message and then a blinking cursor. 
Thanks,
Tim

---

### Post by tgood on 2008-04-27
Could I get some help please.  I've searched the forum and can't find a similar problem to mine.  My computer seems to boot fine, the monitor just doesn't like the graphics mode that it's in. This all started when I tried to enable Compiz and I might have downloaded the wrong driver. 
 I downloaded the live cd and booted it.  It did the same thing, no graphics after the splash. Then I booted it in safe graphics mode with the live cd and it started fine (800x600).  I could then mount my Ubuntu and Windows partitions. Is there a way I could reset my graphics to safe mode?  Then I could try a new driver and hope it works.
Thanks,
Tim

---

### Post by ubuntu-freak on 2008-04-27
The reconfigure command doesn't work the same in Hardy. Try booting into recovery mode and use "xfix".
 
How did you install your NVIDIA driver? Try ENVY perhaps.
 
Nathan

---

### Post by tgood on 2008-04-27
I did try xfix and I got the same warning message.  I tried Envy but I'm  not sure if that's what broke xserver.  If I ever get my GUI back I was going to try a driver download direct from nvidia.
Thanks,
Tim

---

### Post by ubuntu-freak on 2008-04-27
> **tgood said:**
> I did try xfix and I got the same warning message.  I tried Envy but I'm  not sure if that's what broke xserver.  If I ever get my GUI back I was going to try a driver download direct from nvidia.
Thanks,
Tim

 
You did use Envy? Okay then, boot into recovery mode and type this command:
 
**envyng --uninstall-all** 
 
You should now be able to get into your desktop after you reboot.  
Try Envy again though, as if you install the NVIDIA driver yourself it may break after kernel updates.
 
Nathan

---

### Post by tgood on 2008-04-30
Thanks, Nathan for your help.  I didn't see your last reply so I have already deleted the partition and reinstalled fresh.  And the Compiz effects are working now, too.  I've just been playing with Ubuntu so I didn't have anything important to lose.  Thanks again.
Tim

---

