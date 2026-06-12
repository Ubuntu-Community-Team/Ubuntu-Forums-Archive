---
title: "Help- can't burn MP3 files to CD!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Marky-Mark47 on 2007-11-21
Can anyone please suggest an application that will provide a hassle-free way of burning MP3 files to a CD?  Have tried K3b, Gnomebaker and CD/DVD Creator, without success.  Thanks.

---

### Post by bluepowder7 on 2007-11-21
don't you need a special plug-in for that?  i seem to recall some burner programs specifically say "doesn't include MP3 support, get the separate plug-in here".  i think it was InfraRecorder.

---

### Post by rsambuca on 2007-11-21
Every single one of those work for me.  What types of errors are you getting?

---

### Post by skyjacker on 2007-11-21
> **Marky-Mark47 said:**
> Can anyone please suggest an application that will provide a hassle-free way of burning MP3 files to a CD?  Have tried K3b, Gnomebaker and CD/DVD Creator, without success.  Thanks. You have to install a special plug in for k3b, which will work VERY well to burn mp3's 
```
sudo aptitude install libk3b2-mp3
``` Good Luck:)

---

### Post by zvacet on 2007-11-21
For Gnomebaker

```
sudo aptitude install gstreamer0.8-mad gstreamer0.8-misc
```

---

### Post by Marky-Mark47 on 2007-11-24
> **skyjacker said:**
> You have to install a special plug in for k3b, which will work VERY well to burn mp3's 
```
sudo aptitude install libk3b2-mp3
``` Good Luck:)

Thanks.  I actually installed this library using Synaptic.

---

### Post by skyjacker on 2007-11-26
> **Marky-Mark47 said:**
> Thanks.  I actually installed this library using Synaptic.
If this solved your problem, please mark the thread "solved" using the thread tool.:)

---

