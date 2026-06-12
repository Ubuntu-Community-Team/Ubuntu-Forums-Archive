---
title: "Titanium PowerBook boot problem..."
date: 2008-09-08
forum: Apple Hardware Users
---

### Post by CreativeName5 on 2008-09-08
I installed Ubuntu 8.04.1 on a 1Ghz Titanium PowerBook and it keeps failing during the boot, the screen will flash white and get all spotty (check the video).

I found that hitting Control-Alt-F3 right before the screen flashes sometimes gets me into gnome, but it is hit and miss with this method. 

I have posted a video ( [http://www.youtube.com/watch?v=ESA7r4kCd4I](http://www.youtube.com/watch?v=ESA7r4kCd4I) ) of the PowerBook booting up so you can see what is happening and if anyone knows how to fix this problem please help...

-Sean

---

### Post by FredSambo on 2008-09-08
I have the same computer, double check your xorg.conf file...

press ctl-option-F1 to enter the terminal

do:

```
sudo nano /etc/X11/xorg.conf
```

go to 'Monitor' section and edit your HorizSync and VertRefresh to the following:

```
HorizSync 30-100
VertRefresh 50-160
```

press ctl-o, then Enter to confirm, then ctl-x to exit nano

At the prompt do:

```
sudo reboot
```

My tibook still gets kind of spotty like that right before x starts, but it goes right away and boots straight into gnome.

---

### Post by FredSambo on 2008-09-08
Here is the xorg.conf that I am using right now, on this very computer!  You should be able to drop this right in.  I am running Debian Lenny, however.

---

### Post by CreativeName5 on 2008-09-10
So I tried editing my Xorg.conf file and even then imported the one you are using, but it is still hanging there unless I press Control-Alt-F1. Could there be anything else possibly holding it up during boot?

And also just wondering here, but have you gotten the sound to work on your computer?

Thanks
-Sean

---

### Post by FredSambo on 2008-09-10
Yeah, you have to add snd-powermac to /etc/modules

[https://wiki.ubuntu.com/PowerPCFAQ#Enable%20sound%20with%20my%20Powerbook](https://wiki.ubuntu.com/PowerPCFAQ#Enable%20sound%20with%20my%20Powerbook)

To be honest, I can't get Hardy to load on my Powerbook, which is why I am running Debian.  Debian installs with no trouble and once you get the HorizSync and VertRefresh set it auto detects the resolution and everything!  You still have to add she sound modules though.

---

### Post by FredSambo on 2008-09-10
For sound I also have snd-seq in my /etc/modules listing:

```

# My /etc/modules file tibook
apm_emu
firewire-sbp2
loop
snd-powermac
snd-seq

```

---

### Post by CreativeName5 on 2008-09-19
Thanks for all your help, but none of the solutions you had seemed to work, i even tried installing Debian instead, but I was still experiencing problems so I just ended putting Leopard back on it and I am planning to sell. I have my PC with Ubuntu on it with me now (it was at home before) so I guess it's not necessary to run linux on the PowerBook anymore.

-Sean

---

