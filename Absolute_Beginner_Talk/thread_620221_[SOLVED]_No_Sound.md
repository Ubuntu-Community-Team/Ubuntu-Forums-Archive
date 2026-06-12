---
title: "[SOLVED] No Sound"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by corncob on 2007-11-22
I have a Dell OptiPlex, designed for Win98, NT, that I'm fixing up.  I put in more memory, a larger HD, a better CD drive, but the PII mobo with its onboard audio remain the same.  I installed Windows ME and the sound works fine.  I then installed Feisty as a dual boot but no sound.  I then upgraded it to Gutsy but still no sound.  When I click on the speaker icon (no, its not muted) I get a window saying "No volume control GStreamer plugins and/or devices found."  I have all 4 GStreamers from Add-Remove Programs installed although I haven't gone to Synaptic.  Other messages say "nothing to control, no card there or none configured.  The sound continues to work in WinME.

---

### Post by mahiyar on 2007-11-22
MObo with sound chip is difficult to configure in Linux / Ubuntu,  esp an old Mobo, what make/model is the MoBo? google it and you might get some help.

---

### Post by comprookie2000 on 2007-11-22
post
```

lspci | grep Audio

```

---

### Post by corncob on 2007-11-22
Nothing
> user@user-desktop:~$ lspci | grep Audio
user@user-desktop:~$ 

I'll try to find out something about the mother board but taking this thing apart is easier said than done.

---

### Post by mahiyar on 2007-11-23
Try putting the audio in small like $lspci | grep audio

---

### Post by corncob on 2007-11-23
I did.  Still nothing )-:

---

### Post by Pumalite on 2007-11-23
What about:
sudo lshw -C sound

---

### Post by corncob on 2007-11-24
Still nothing with that either:
```
user@user-desktop:~$ sudo lshw -C sound
user@user-desktop:~$    
```
Although before the prompt reappeared "PCI (sysfs)" flashed on the screen, followed by "SCSI", then finally by "Framebuffer devices" and then the prompt reappeared.  I guess it was just looking in vain, huh?

---

### Post by Pumalite on 2007-11-24
Try:
sudo apt-get install linux-backports-modules-generic

---

### Post by jingo811 on 2007-11-24
Try this I had problems once with Ubuntu while my dual boot Windows XP still had sound.
[img]http://i6.tinypic.com/6tcvq6f.png[/img]
If that doesn't work here's a comprehensive guide to follow and read.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by corncob on 2007-11-24
```
sudo apt-get install linux-backports-modules-generic
```
did its thing.  I then proceeded to install every gstreamer in Synaptic and rebooted but still no sound.  The Volume Control doesn't give me any Headphone sensor to unselect; it just gives me a window saying "The Volume Control didn't find any elements or devices to control."  I will go to that thread though.
I booted to Windows ME and under Sound in the Device Manager it told me I had a Crystal WDM MPV-401 Compatible device.  I googled this but finding a Linux driver for it is something else.

---

### Post by Pumalite on 2007-11-24
If my command worked, lets see:

sudo lshw -C sound

---

### Post by corncob on 2007-11-26
"sudo lshw -C sound" didn't give me anything even after installing the backports and all the gstreamers.  I'm thinking of buying a PCI sound card and putting it in the computer.  I've "fixed" onboard sound problems that way in the past:)  I still have to read jingo811's link though.

---

### Post by jingo811 on 2007-11-26
If it worked when you boot into Windows then it should work with a little tweaking in Ubuntu.  I don't think it's a case of broken sound device on your Mobo.

---

### Post by corncob on 2007-11-29
I remembered that I had an extra PCI sound card (Cobra) so I put it in.  The sound is now working fine -- in Win ME also so I'm taping over the onboard sound ports and forgetting about them.  I guess I should mark this thread as "solved" although its not really the way I wanted to do it.

---

