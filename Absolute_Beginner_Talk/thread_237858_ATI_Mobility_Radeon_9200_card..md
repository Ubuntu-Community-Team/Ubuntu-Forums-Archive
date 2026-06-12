---
title: "ATI Mobility Radeon 9200 card."
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by mskadu on 2006-08-16
Hi all,

I have been following instructions in :

[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

and picked fglrx as suggested. However, on restarting the machine i couldnt load my graphics mode :(

I am a complete newbie. Any suggestions?

My hardware: Sony Vaio PCG-K115Z

- M:confused:

---

### Post by Greycloak on 2006-08-16
Type the following:

```
sudo pico /etc/X11/xorg.conf
```

Look for:

```
Section "Device"
```

If it says anything other than "fglrx" change it to that.

Then press ctrl-o to write the file, ctrl-x to exit, then reboot.

See if that helps at all.

---

