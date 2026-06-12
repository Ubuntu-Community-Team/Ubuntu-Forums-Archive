---
title: "Can't get GDM to start- flashing screen"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by phatdad on 2007-09-30
I have killed off my Ubuntu! It was all OK until I started  putting LMMS on. I had to install various dependancies- then the system hung. On reboot I get no log-in screen. I just get a flashing screen. 

I have tried various solutions by following other posts re what seemed similar problems, but no joy.

I have pressed ctrl+alt+f1 to get a command prompt and tried all these
sudo /etc/init.d/gdm stop 
startx
sudo dpkg reconfigure -phigh xserver-xorg
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo aptitude install gdm

Is there some way I can recover this without reinstalling, or reinstalling but keeping all my settings and files?

Hope someone can help.

---

### Post by reset3x on 2007-09-30
Try ```
sudo aptitude purge lmms
```

Reboot...

Reinstall ALSA via Synaptic..

---

### Post by phatdad on 2007-09-30
Thanks for the reply, but I'm afraid it didn't work. I have also forced new versions of ubuntu-desktop and gdm via sudo aptitude update/install. Still nothing. Is it anything to do with the login screen trying to get to my soundcard to play the start up sound? (I'm guessing here- I'm a total newbie)

---

### Post by reset3x on 2007-09-30
I don't believe that sound should have anything to do with being able to login. Its probably has more to do with the XServer. Have you installed video drivers? Did you do a kernel upgrade before your problem started? When you did sudo dpkg-reconfigure -phigh xserver-xorg which driver did you choose? What are your system specs?

---

### Post by phatdad on 2007-09-30
I have nvidia drivers installed via envy. The kernel is still the same. I chose the nvidia driver during reconfig. I'm on an AMD Athlon XP 2200+ (1.8 GHz), 768 Mb Ram, GeForce5200, on board SoundMax.

---

### Post by reset3x on 2007-09-30
Boot to recovery mode and ```
apt-get remove ubuntu-desktop
```

Then ```
apt-get install ubuntu-desktop
``` This should install everything including your GDM etc.. while preserving any settings you have in your /home/ dir...

Then ```
envy -t
``` Unstall your nvidia drivers..

Then ```
envy -t
``` Reinstall your nvidia drivers... Let Envy configure Xorg for you..

Then ```
reboot
```

Hope this helps!!!

---

### Post by phatdad on 2007-09-30
Thanks for the help, but it's still not working yet. When I run 
apt-get install ubuntu-desktop
I get this error at the end
invoke-rc.d: initscript.gdm action "reload" failed

---

### Post by reset3x on 2007-09-30
> **phatdad said:**
> Thanks for the help, but it's still not working yet. When I run 
apt-get install ubuntu-desktop
I get this error at the end
invoke-rc.d: initscript.gdm action "reload" failed

are you rebooting to recovery mode? You may have to hit esc when GRUB is loading...Then you will be logged on as root... Also this way gdm won't attempt to start....

Then ```
aptitude purge ubuntu-deskop
```

Then ```
apt-get install ubuntu-desktop
```

---

### Post by phatdad on 2007-10-01
Sorry got sidetracked last night. I'm afraid using purge didn't work either. I am in recovery mode. Any other ideas?

Thanks again

---

### Post by phatdad on 2007-10-02
Still stuck with the flashing screen. I have tried reinstalling libgtk2.0-0 after reading other posts but still the same. It's looking like I might have to reinstall everything but I don't want to loose all my settings etc. Can anyone suggest any other solutions?

---

### Post by Yoooder on 2007-10-04
Do you see anything appear on screen at all?  If it's just flashing it sounds to me as though it *might* be your X-server failing to start and retrying.

---

### Post by phatdad on 2007-10-06
Just to let you know I ended up reinstalling Ubuntu. Here's hoping I don't break it again...

---

