---
title: "[SOLVED] Gutsy fresh install - now out of range message on startup and shutdown."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-11-05
Orange progress bar not showing either. Maybe this has to do with the out of range error.

Resolution set correctly and screen display is fine.

---

### Post by Tony3286 on 2007-11-05
I did an **upgrade** from Feisty and getting the red warning box about resolution out of range also - it travels down the screen and then Gutsy boots - same thing upon shutdown -resolution is also correct - interested to hear any suggestions too!

---

### Post by stoodleysnow on 2007-11-05
Looks like the initial boot up / shutdown resolutions have been messed up. I also get this bug on my Gutsy desktop installs (not so much on the laptop though).
:-k

---

### Post by philinux on 2007-11-05
Whats the fix then.

Here's my first grub entry.

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9024104a-fa2f-4f85-bb6d-385637bdee48 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

---

### Post by sailor2001 on 2007-11-05
with gutsy, I have to set resolution to 1280x1024 although normal (feisty) it would be 1024x768

---

### Post by philinux on 2007-11-05
Fixed this by installing and running startupmanager from the repo.

Should have read the sticky and this helped.

---

### Post by Tony3286 on 2007-11-05
Could you direct me to the post related to your fix
Thanks!

---

### Post by mujalan on 2007-11-05
Philinux,

I have been bugged with the "out-of-range" thing on Gutsy Kubuntu.  I followed your idea of loading and running startupmanager and now it works correctly.  No more "out-of-range".  Thanks!  You're a genius!

---

### Post by Tony3286 on 2007-11-05
Once Startup manager installed, what did you change  -your original resolution? What exactly corrected the out of range problem?

---

### Post by philinux on 2007-11-05
Sorry forgot to post the link

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

Boot splash screen does not display

      With some monitors the resolution is wrongly detected when installed from a desktop CD and the boot splash screen is not displayed. You can fix the resolution by editing /etc/usplash.conf. Bug #150930

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930)

In startup manager I just set resolution to 1024 768.
Left everything else as it detected.

---

