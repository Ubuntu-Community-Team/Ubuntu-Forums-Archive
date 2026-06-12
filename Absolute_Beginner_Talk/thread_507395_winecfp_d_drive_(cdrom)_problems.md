---
title: "winecfp d: drive (cdrom) problems"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by frostbytes on 2007-07-22
I was trying to configure DVDDecrypter like it says to do in the link below, but when I try to auto detect my drives, I get this message...

```
joe@joe34:~$ winecfg
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
```

The D: is my cdrom drive that it is trying to configure.  It reads like this in the winecfp > drives tab...

```
d:  /media/cdrom0/ 
```

If anyone has an idea why this is happening and can help me fix it, that would be great.  Let me know, thanks everyone!

[https://help.ubuntu.com/community/DVDShrink]("https://help.ubuntu.com/community/DVDShrink")

---

### Post by wood144 on 2007-07-25
i have this same problem, i've tried installing wine from the sudo apt-get, from synaptic, through the add remove menu, even from the winehq archives.  what am i doing wrong? i alway get this error in the winecfg screen.

---

### Post by doctorstrangelove on 2007-07-30
I have the same problem when i'm trying to set up winetools. here is what the console says: "Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
cp: cannot stat `/usr/local/bin/../share/wine/wine.inf': No such file or directory
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0"
please help

---

