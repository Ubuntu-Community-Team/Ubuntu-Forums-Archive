---
title: "X11 wont start up, I changed something and cant fix it"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-03-23
I attempted to change my nvidia drivers for my video card, to enable 3d acceleration and other gaming necessities. My result is X failing to load properly when I restarted my system. I checked the error logs, and it failed to load the kernel that I updated it too. How on earth do i correct this problem. My only option is the terminal, which I dont have too much experience with..

---

### Post by taurus on 2007-03-23
From the prompt, edit /etc/X11/xorg.conf and change the Driver from "nvidia" back to "nv".

```
sudo nano -Bw /etc/X11/xorg.conf
```
Save it and exit with <Ctrl>o and <Ctrl>x.  Reboot by running

```
sudo shutdown -r now
```

---

### Post by crispy_420 on 2007-03-23
So stuck in terminal. There is actually an easy way out. It involves just getting basic drivers going so you can get a GUI to search for your solution.

Log in with username and password.

sudo nano /etc/X11/xorg.conf

scroll down to your video driver in Section "Device"

change driver to vesa

reboot

you should have a basic gui with no video acceleration but you can at least search for a fix.

---

### Post by HgBoy on 2007-03-23
Taurus, You hit the nail on the head. Any advice on getting my nvidia card recognized? I just shelled out the money for cedega, and it wont even work. It is an Asus GeForce 7300GS.

---

### Post by taurus on 2007-03-23
You can try envy.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by HgBoy on 2007-03-24
envy causes the same error I was getting previously, no matter which version of the driver I try to load. Any other suggestions?

---

