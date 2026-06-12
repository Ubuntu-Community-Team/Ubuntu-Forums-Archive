---
title: "Upgrading to 8.04 from 7.10: Noise and mouse problems"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by peterhaagerup on 2008-05-03
For some days ago I upgraded my Apple MacBook from Ubunto 7.10 to 8.04. For the first time I experienced no big problems afterwards. However, I can hear a whining noise all the time. It seems to stop for 1-2 seconds when I move the mouse or when there is harddrive activity. What is going on and how to stop the noise? I had similar problems with Ubuntu 7.10 but at that time I used the previous kernel because I had a lot of problems with the new kernel. I remember having the whining noise at that point as well - but with the older kernel - everything worked just fine.

With the newest kernel (installed with 8.04: 2.6.24-16-generic) the only problem I have is the noise problem. A minor problem I have as well is my touchpad going crazy after some hours of use. The pointer on the screen is "shaking" and when I try to move it using the touchpad, it is going crazy all over the screen. I can move it with my external bluetooth mouse without problems. The pointer is still vibrating sometimes, even without touching the touchpad.

I hope that some have experienced the same or similiar problems and knows a solution to this. Thanks :)

---

### Post by cyberdork33 on 2008-05-03
From now on, please indicate what kind of Mac you are using (Intel vs PPC) in the thread title.

upgrading often yields very odd problems. You might try regenerating your xorg.conf file after you make a backup of your old configuration:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by stream303 on 2008-05-03
There might be a slight problem with dpkg-reconfigure xserver-xorg in Hardy - I don't know if it is being deprecated, or is no longer totally compatible with xorg 7.3 when it comes to video drivers.

There are a few bug reports similar to this one:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/174214](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/174214)

---

### Post by ksquaredmedia on 2008-08-06
I had the same problem too with a weird buzz in the background.
I fixed it by opening my volume control then muting the 'PC Speaker' output. If this doesn't work, you might want to try on your volume control clicking 'Edit', 'Preferences', Check Box every option, then mute every unnecessary option, then unchecking the unessential options (everything but 'Master' 'PCM', 'Line In' and 'Microphone' .
The sound for all my video files still works after doing so.
Hopefully, this helps.

---

