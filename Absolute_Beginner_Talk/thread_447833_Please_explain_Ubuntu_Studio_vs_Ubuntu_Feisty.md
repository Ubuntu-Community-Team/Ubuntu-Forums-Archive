---
title: "Please explain Ubuntu Studio vs Ubuntu Feisty"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by paker on 2007-05-18
I now have Feisty 32 bit running fine on my machine. But I had to go through frustrating period to make various audio files play/converted. I don't think I remember what I did.

1) If I install Ubuntu Studio, will I be able to play/convert audio files of different formats right away?
2) What will I lose by going to Ubuntu Studio from Ubuntu Feisty?

Thanks.

---

### Post by mikewhatever on 2007-05-18
Ubuntu studio is for recording and editing music, video and graphics. You'll learn a lot here [http://distrowatch.com/table.php?distribution=ubuntustudio](http://distrowatch.com/table.php?distribution=ubuntustudio)
Also, if you could tell more about the frustrating problems you had. Even with Ubuntu studio, you'd have to learn how to do things.

---

### Post by shen-an-doah on 2007-05-18
1) No, it's the same as Ubuntu with regards to codecs not being installed by default.
2) You won't lose anything with regards functionality, etc. The difference between studio and normal Ubuntu is that Studio includes a low-latency kernel and different applications and theme installed by default.

If you're talking about files, you don't necessarily have to do a complete reinstall to get Studio. You can just "upgrade" from your Feisty install.

[http://ubuntuforums.org/showthread.php?t=442506](http://ubuntuforums.org/showthread.php?t=442506)

Third post down.

---

### Post by paker on 2007-05-18
Thanks a lot. I thought I would have to sacrifice peripheral control. Will "upgrade."

The difficulty I had with audio files was not the codec issue, for I installed all codecs immediately after Feisty installation via automatix. I had to install different programs to do the right audio file manipulation. Some programs didn't work because of latency not being low enough, hardware confguration (which I still don't understand), etc.

---

### Post by nitrofurano on 2007-05-18
the awesome of UbuntuStudio (i didn't try it yet) is you having on one dvd (or cd?) all - or almost all -  enough for a arts-design-music school/university, professional, student, or curious - to have an operative system like linux and all known open-source productivity tools in these areas - i were one of those suggested and looked for this kind of distro - congratulations, really! :-D

---

### Post by ageilers on 2007-05-18
Nice to know it is available. I have a pc with a M-Audio Delta 66 audio card. Does anyone know if that would work? I have been using audacity for years and love it. Great for recording.

---

### Post by Patrick K on 2007-05-19
> **ageilers said:**
> Nice to know it is available. I have a pc with a M-Audio Delta 66 audio card. Does anyone know if that would work? I have been using audacity for years and love it. Great for recording.

The Delta 66 should work fine. Alsa has drivers for it. M-Audio are among the best supported. I use an Audiophile 2496 and it work great. 

[http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-ice1712](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-ice1712)

You should also get the Alsa-tools-gui. It has the Envy24 Control which is a very good mixer for VIA Ice1724 based cards, like your Delta.

---

