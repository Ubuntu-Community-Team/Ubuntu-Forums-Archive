---
title: "Display alignment on iMac"
date: 2009-07-29
forum: Apple Hardware Users
---

### Post by gab10 on 2009-07-29
I just installed 9.04 on a G5 iMac. Everything went great, except that my display is slightly misaligned. A couple dozen pixels that should be on the right of my display actually wrap over and show up on the left. I tried taking a screenshot, but it appears correct there.

Has anyone else seen this problem or have ideas on how I might fix it?

---

### Post by imacQ on 2009-08-01
This fix might work for the G5 iMac in Jaunty? I had the garbled graphics you describe on my 22" Apple Cinema Display when I upgraded from Hardy to 8.10. 

Install the nouveau driver and specify it in xorg.conf 

```
sudo apt-get install xserver-xorg-video-nouveau
```

```
sudo nano /etc/X11/xorg.conf
```

In the Device Section of xorg.conf replace what you have on the Driver line with "nouveau."

Control o, and Return to write the file.
Control x, and Return to exit nano.
 
Reboot and you're hopefully good to go.

---

