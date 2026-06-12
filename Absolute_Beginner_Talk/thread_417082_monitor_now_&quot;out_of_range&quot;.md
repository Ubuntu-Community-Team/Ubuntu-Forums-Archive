---
title: "monitor now &quot;out of range&quot;"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dynacrylic on 2007-04-21
Last night I did some updates to Breezy (not to Fiesty) and shutdown for the night.  Now this morning I'm getting an "out of range" on my monitor.

Any suggestions on how to get this working?

---

### Post by taurus on 2007-04-21
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by wh0rd on 2007-04-21
> **dynacrylic said:**
> Last night I did some updates to Breezy (not to Fiesty) and shutdown for the night.  Now this morning I'm getting an "out of range" on my monitor.

Any suggestions on how to get this working?

I've noticed this usually happening when you have the incorrect refresh rates. The refresh rates are specified in **/etc/X11/xorg.conf** under the Monitor section, for example (refresh rates are in bold):

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
[B]        HorizSync       28-80
        VertRefresh     48-75[/B]
EndSection

```

Check the monitor's Horizontal and Vertical refresh rate specifications for your modeled monitor from the manufacturer and make sure they match accordingly in xorg.conf

---

### Post by dynacrylic on 2007-04-21
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

thanks so much! 

that fixed it

---

### Post by en3rgy on 2007-04-21
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```I had an issue with my resolution and found your fix to work perfectly. Thank you! :guitar:

---

### Post by vnt87 on 2007-04-22
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

Sorry if this is obvious, but what does the -phigh option do?

---

### Post by taurus on 2007-04-22
It will only configure the resolutions, leaving everything else untouched.

---

