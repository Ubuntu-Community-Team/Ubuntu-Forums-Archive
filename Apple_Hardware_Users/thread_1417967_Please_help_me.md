---
title: "Please help me"
date: 2010-02-28
forum: Apple Hardware Users
---

### Post by jazzlukejosh on 2010-02-28
Please help someone???

I running Ubuntu 9.10 on an old iMac G3 powerpc, it was a good installation except for  some issues, I don't have the right screen resolution so I can't view webpage properly and my daughter won't be able to play games.
I tried to download the old driver for it, which was "[I]Rage 128 Pro Ultra TR" but the system would let me install it, message says "newer driver allready installed".

Then I tried to manually change my xorg.conf but I didn't have one. So I tried to download Xorg and when I tried to save it in etc/X11, I got the message saying that I didn't have permission to save it there.

I'm totally stumped, if any one can help me, I would be so grateful.
Unfortunatly I need step by step instructions.
[/I]

---

### Post by pastalavista on 2010-02-28
Have you tried booting to recovery mode, open a root terminaal with networking and run ```
sudo aptitude update

sudo aptitude safe-upgrade

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by jazzlukejosh on 2010-02-28
Thank you I've done that, do I have to save it?
The command 'sudo dpkg-reconfigure xserver-xorg' didn't seem to do anything

What do I do now?

---

### Post by pastalavista on 2010-02-28
If you rebooted after doing that and nothing changed, you may have the wrong graphics driver installed. Is there anything in your System|Administration|Hardware Drivers that could be downloaded, activated or de-activated? If not, post the output of this terminal command ```
sudo lshw -C video
```

---

### Post by jazzlukejosh on 2010-02-28
Sorry turns out I didn't do it, I thought you meant in the terminal.
I don't know how to reboot to recovery mode.
sorry I'm an newbie

---

### Post by jazzlukejosh on 2010-02-28
Does this shed any light on the situation??

 *-display               
       description: Display controller
       product: Rage 128 Pro Ultra TR
       vendor: ATI Technologies Inc
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list rom
       configuration: driver=aty128fb latency=255 mingnt=8
       resources: irq:48 memory:94000000-97ffffff(prefetchable) ioport:400(size=256) memory:90000000-90003fff memory:90020000-9003ffff(prefetchable)

---

### Post by pastalavista on 2010-02-28
OK :) no problem. When you reboot, press and hold the shift key to bring up the grub menu and choose the second option. It says (recovery mode)

---

### Post by jazzlukejosh on 2010-02-28
I rebooted and typed in those commands but I think they failed, can't write it all down but heres some of it.
 
E: /root/.aptitude is readable but not writeable; unable to write configeration file
w: Not useing locking for read only lock file /var/lib/dpkg/lock
E:Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened 
 
Its said a similer thing for for both command, I think I'm locked out, Why?

---

### Post by jazzlukejosh on 2010-02-28
Hi. Rebooted to recovery menu. Got it back then did what you said. And everything updated successfully. Then looked in System/Admin/Hardware and it said "no proprietory drivers are in use on this system". So I posted the output as you know. What now?

---

### Post by pastalavista on 2010-02-28
Sorry, I really don't know what to tell you further. I did a [Google search of the forums]("http://www.google.com/search?num=30&hl=en&newwindow=1&safe=off&client=firefox-a&hs=5uJ&rls=com.ubuntu%3Aen-US%3Aunofficial&q=site%3Aubuntuforums.org+ati+rage+xorg.conf+mac&aq=f&aqi=&aql=&oq=") and there's been a lot written about it. Good luck getting it fixed.

---

### Post by jazzlukejosh on 2010-02-28
Thank you very much for your time Pastalavista.

---

### Post by tiresia on 2010-02-28
[http://forums.debian.net/viewtopic.php?f=16&t=20481](http://forums.debian.net/viewtopic.php?f=16&t=20481)

---

