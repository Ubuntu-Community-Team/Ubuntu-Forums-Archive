---
title: "screen blanks out after booting"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by yasasvy on 2007-02-26
hi. I have been using ubuntu dapper 6.06 for 6 months, without a prob. recently i configured my monitors resolution using 915resolution as i use intel 845 chipset. my problem started after configuring that, after  booting up, the screen simply blanks out. can anyone suggst me a possible solution?? i use a  CRT monitor with 1024*768 res and depth of 32. and is there any way to reinstall the 915resolution package with the default config??  plz help me... thnx in adv. and also i am able to hear the login sounds.. so i am sure the prob is with the resolution. The display works fine while using windows.. and aslo.. when i operate using LIVE CD.

---

### Post by mahiyar on 2007-02-26
My only suggestion would be to select the recovery mode in grub and undo/make the changes in the [B]/etc/X11/xorg.conf file
[/B]

---

### Post by ukripper on 2007-02-26
> **yasasvy said:**
> hi. I have been using ubuntu dapper 6.06 for 6 months, without a prob. recently i configured my monitors resolution using 915resolution as i use intel 845 chipset. my problem started after configuring that, after  booting up, the screen simply blanks out. can anyone suggst me a possible solution?? i use a  CRT monitor with 1024*768 res and depth of 32. and is there any way to reinstall the 915resolution package with the default config??  plz help me... thnx in adv. and also i am able to hear the login sounds.. so i am sure the prob is with the resolution. The display works fine while using windows.. and aslo.. when i operate using LIVE CD.

use follwoing to reconfigure your xserver

$ sudo dpkg -reconfigure xserver-xorg

 to correct drivers and resolutions

---

### Post by taurus on 2007-02-26
> **ukripper said:**
> use follwoing to reconfigure your xserver

$ sudo dpkg -reconfigure xserver-xorg

 to correct drivers and resolutions

There should be no space between dpkg and -reconfigure.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ukripper on 2007-02-26
> **taurus said:**
> There should be no space between dpkg and -reconfigure.

```
sudo dpkg-reconfigure xserver-xorg
```

thanks taurus to correct the space i might have overlooked it.

---

### Post by yasasvy on 2007-02-27
thnx guys for u help..now the display is working!! ill never meddle again with those resolutioons .. thns again.

---

### Post by mahiyar on 2007-02-27
Dont worry about meddling thts how you learn. Afterall if anything hapens what are forums for.

---

### Post by ukripper on 2007-02-27
> **yasasvy said:**
> thnx guys for u help..now the display is working!! ill never meddle again with those resolutioons .. thns again.

Now you know the resolution to your problem,  therefore you can take a plunge to experiment with your settings and if anything goes wrong you know where to look for.

Goodluck.

---

