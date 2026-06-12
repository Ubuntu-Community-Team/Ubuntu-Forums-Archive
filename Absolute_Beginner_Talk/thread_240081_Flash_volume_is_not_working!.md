---
title: "Flash volume is not working!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by MacDonagh on 2006-08-20
I installed Flash via Automatix and the screen shows the video actually running with no problems at all. It's just there is no volume. Can anybody help? Ta!

---

### Post by MacDonagh on 2006-08-20
Anyone at all?

---

### Post by xpod on 2006-08-20
Had the same prob after getting flash via automatix.I was given this to do

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd                      
```

Im not sure exactly what it did....New tooooo
But after sticking those two lines of code in one after the other and rebooting all was sound.

---

### Post by MacDonagh on 2006-08-20
Arghhh it didn't work!
Any other ideas?

---

### Post by %hMa@?b&lt;C on 2006-08-20
[https://help.ubuntu.com/community/FirefoxAMD64FlashJava?highlight=%28flash%29](https://help.ubuntu.com/community/FirefoxAMD64FlashJava?highlight=%28flash%29)

---

### Post by xpod on 2006-08-20
Surely the whole "automatix" thing is supposed to cut out all the need for those tougher routes(tough IF your new).

THAT was the only reason i initially got automatix was for the flash and java
so the last thing i wanted was still to have the problems with the sound that ive still had.
First there was that code and since then ive had it die again and i ended up trying to follow a tutorial that had me get alsa-oss.That worked BUT why did i even need to fix it all AGAIN???

Sound DONT seem to be too sound for us newcomers at first does it?

---

