---
title: "OSD for global volume shortcuts in Kmix-- how?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Paradoxdruid on 2006-08-18
So, I have two Kubuntu boxes-

One, a Koala Mini system I bought pre-installed with Kubuntu from system76.com.  On this box, when I hit my Volume up and volume down keys, a nice on screen display of the current volume % and a slider in a grey box appears.

The other is my home-built PC with Kubuntu.  On it, turning the volume up and down doesn't display any OSD.

I haven't been able to find how to enable or disable OSD for Kmix anywhere.  I set the global shortcuts through the "Global Shortcuts" menu of the Kmix Mixer window.

Any advice?  Thanks in advance!

---

### Post by msak007 on 2006-08-18
kmilo is the service that provides the OSD. Check if you have it by going to System Settings --> KDE Components --> Service Manager and see if it's listed / running. If it isn't, simply issue a 

```
sudo aptitude install kmilo
```

and try again. Also make sure that your volume keys really are working and turning the volume up / down. If it's a different comp using different hardware, it may not be recognizing the keystrokes.

---

### Post by Phlogiston on 2007-10-31
> **msak007 said:**
> kmilo is the service that provides the OSD. Check if you have it by going to System Settings --> KDE Components --> Service Manager and see if it's listed / running. If it isn't, simply issue a 

```
sudo aptitude install kmilo
```

and try again. Also make sure that your volume keys really are working and turning the volume up / down. If it's a different comp using different hardware, it may not be recognizing the keystrokes.

Here kmilo is up and running but no osd display if I change the volume with my function keys. Although the volume is changed as I can see in kmix. Any idea?:confused:

---

