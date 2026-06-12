---
title: "HELP small resolution!"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by phoenix5002 on 2008-02-02
I tried using envy and it wouldn't work automatically and said I could try manually at my own risk....and I did.
I restarted and X server wouldn't start so I started in text mode and logged in as root and typed:
envy --uninstall-all
Then I restarted and now the X server works, but the only resolutions are 640x480 and 800x600.

So I downloaded the latest drivers for my video card and restarted again, and I still only have those two resolutions available to me.

My screens native resolution is 1280x800 please help me.

---

### Post by phoenix5002 on 2008-02-02
When I go into my xorg.conf file I see this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon IGP 330M/340M/350M"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection
```


which is wierd because it already has 1280x800 listed, so why can't I select it??

---

### Post by Moop on 2008-02-02
Have you tried installing the nvidia driver through the restricted driver manager? What version of Ubuntu are you using?

edit: I see you have a ATI card but the same goes for that.

---

### Post by phoenix5002 on 2008-02-02
I am using 7.10 Gutsy.
No I havn't done the Nvidia Driver, but the only thing I see in the restricted drivers is "Atheros Hardware Access Layer (HAL)" and it's "In Use", and it was exactly like that before this all happened.

---

### Post by phoenix5002 on 2008-02-02
whew, got it working again, just had to reconfigure xserver:

**sudo dpkg-reconfigure xserver-xorg**

but detection is best if xserver is not running so I first did:
**sudo /etc/init.d/gdm stop**
and then after I configured I started xServer again:
**sudo /etc/init.d/gdm start**

---

