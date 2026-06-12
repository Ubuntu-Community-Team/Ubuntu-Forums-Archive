---
title: "Hard Drive drop protection not working"
date: 2013-03-10
forum: Apple Hardware Users
---

### Post by Benjamindaines on 2013-03-10
MacBook Pro 8,2 Kubuntu 12.10.  The auto-stop function on the hard drive meant to be triggered if the computer is dropped doesn't seem to be working.  What do I need to get it functioning?  Thanks.

---

### Post by ManamiVixen on 2013-03-10
Thats a fuction of the drive and not of the OS. If a drive feature isn't working, do a SMART test.

---

### Post by Benjamindaines on 2013-03-10
> **ManamiVixen said:**
> Thats a fuction of the drive and not of the OS. If a drive feature isn't working, do a SMART test.

Works in OS X

---

### Post by tgalati4 on 2013-03-10
Perhaps:  hdapsd - HDAPS daemon for IBM/Lenovo ThinkPads and Apple iBooks/PowerBooks

---

### Post by ManamiVixen on 2013-03-10
To me, thats a sign that the Macbook has an inertia/gravity/motion sensor in it that tells the Hard disk when to shut off if the computer was dropped. If that is the case, you need the driver for it. But as of the moment, I can not find any info on that posibility from Apple.

---

### Post by Benjamindaines on 2013-03-11
> **tgalati4 said:**
> Perhaps:  hdapsd - HDAPS daemon for IBM/Lenovo ThinkPads and Apple iBooks/PowerBooks

```
Mon Mar 11 00:22:27 2013: Starting hdapsd
Mon Mar 11 00:22:27 2013: WARNING: You did not supply any devices to protect, trying autodetection.
Mon Mar 11 00:22:27 2013: Adding autodetected device: sda
Mon Mar 11 00:22:27 2013: Could not find a suitable interface
```

Maybe I need to reboot after installing?

---

### Post by tgalati4 on 2013-03-11
I have an ACER laptop that has a vibration symbol on the underside of the hard disk, so I tried starting the hdapsd and got the following from:

```
dmesg | tail
```

[ 4419.801973] hdaps: supported laptop not found!
[ 4419.801981] hdaps: driver init failed (ret=-19)!
[ 4492.429663] thinkpad_ec: no ThinkPad embedded controller!
[ 4531.359666] thinkpad_ec: no ThinkPad embedded controller!

If yours shows the same, then it may not be supported with the current hdapsd daemon.

---

### Post by Benjamindaines on 2013-03-11
> **tgalati4 said:**
> I have an ACER laptop that has a vibration symbol on the underside of the hard disk, so I tried starting the hdapsd and got the following from:

```
dmesg | tail
```

[ 4419.801973] hdaps: supported laptop not found!
[ 4419.801981] hdaps: driver init failed (ret=-19)!
[ 4492.429663] thinkpad_ec: no ThinkPad embedded controller!
[ 4531.359666] thinkpad_ec: no ThinkPad embedded controller!

If yours shows the same, then it may not be supported with the current hdapsd daemon.

That is in fact what I'm seeing :(

---

### Post by jhohisel on 2013-03-13
Apple calls it the Sudden Motion Sensor (SMS): [http://support.apple.com/kb/ht1935](http://support.apple.com/kb/ht1935)

---

