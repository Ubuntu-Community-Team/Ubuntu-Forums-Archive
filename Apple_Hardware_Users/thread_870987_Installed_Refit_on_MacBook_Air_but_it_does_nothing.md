---
title: "Installed Refit on MacBook Air but it does nothing?"
date: 2008-07-26
forum: Apple Hardware Users
---

### Post by steffi on 2008-07-26
If I only have OSX on a MacBook Air and I installed Refit what should appear when I hold down the "Option" key on startup?

---

### Post by hajk on 2008-07-26
The whole idea of rEFIt is that you don't hold down the Alt-Option key, since rEFIt (when enabled) will present a boot menu when the computer is booted. If you only have OS X installed, it should give you a single Apple icon as boot choice, selecting it will boot Mac OS X as before; doing nothing will boot it by default after some time. Assuming that you installed rEFIt the default way, it is enabled by opening a terminal and giving the command```

sudo /efi/refit/enable-always.sh
```

---

### Post by cyberdork33 on 2008-07-26
> **hajk said:**
> The whole idea of rEFIt is that you don't hold down the Alt-Option key, since rEFIt (when enabled) will present a boot menu when the computer is booted. If you only have OS X installed, it should give you a single Apple icon as boot choice, selecting it will boot Mac OS X as before; doing nothing will boot it by default after some time. Assuming that you installed rEFIt the default way, it is enabled by opening a terminal and giving the command```

sudo /efi/refit/enable-always.sh
```
well you aren't supposed to have to run the shell script, but if it is not working then you need to run it...

---

### Post by Matt926 on 2008-07-26
Whats the point of installing it with only one OS?

---

### Post by hajk on 2008-07-27
It would be a preparation for the subsequent installation of a "legacy" OS, like the Ubuntu flavour of GNU/Linux.

---

### Post by kdb424 on 2008-07-27
I have it with one OS now. I had windows and Ubuntu, but now windows won't boot, and I can't get rid of that without making the disk 1 partition, so bye Ubuntu again.

---

### Post by hajk on 2008-07-27
...or left over from an earlier multi-boot situation. 

**@OP** Why don't you give a bit more info on your problem, instead of resigning yourself to "bye Ubuntu"? We may be able to help you fix it...

---

