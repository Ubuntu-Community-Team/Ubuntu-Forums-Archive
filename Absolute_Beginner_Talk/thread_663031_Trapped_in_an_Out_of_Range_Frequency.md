---
title: "Trapped in an Out of Range Frequency"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by sethosayher on 2008-01-09
**(Note: I've checked other posts but they don't appear to address my problem.)**

 I was messing around with different resolutions, trying to see what I could use...I was using 1024 x 768 but wanted to experiment...I ended up using something like 1600 times another value...I don't remember. I logged off to apply this new resolution, then received the "out of range frequency" message. Now, every time I start up ubuntu I get this message, meaning I can't even log in to adjust the resolution. 

Can anyone help me?

---

### Post by taurus on 2008-01-09
Boot into recovery mode from GRUB menu and reconfigure your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by sethosayher on 2008-01-09
Thanks, I'll try that now.

---

### Post by dcstar on 2008-01-09
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

or to save time, boot Ubuntu normally and then CTRL-ALT-F1 and log in with your user credentials, then:
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

This way you can stay booted up and make subsequent changes if you didn't get the reconfig quite right.

---

