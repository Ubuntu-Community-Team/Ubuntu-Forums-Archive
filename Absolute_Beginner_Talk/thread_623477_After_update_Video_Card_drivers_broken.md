---
title: "After update: Video Card drivers broken"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by gogetadbl on 2007-11-25
After I installed some updates to Ubuntu, I got the error: "Ubuntu failed to load the nvidia kernel module screens found but none have a usable configuration."  I don't remember what updates they are though but to get back into xwindows I had to delete my xorg.conf file.  I also did a xserver reconfigure.  After all of this, my mouse's scroll wheel no longer works and the computer is not seeing the video resolutions it should be seeing.

Is there a way to let Ubuntu re-detect my drivers again so they are working fresh?

EDIT: When I tried installing nvidia-xconfig then typing nvidia-xconfig to create a new config file, I'm getting the same error before where I can't boot into xwindows.  "Failed to load modlue "nvidia" (module does not exist, 0).  No drivers available"

---

### Post by stevemu on 2007-11-25
Try the following in a terminal window.

```
sudo dpkg-reconfigure xserver-xorg
```

Worked for me when I had a similar problem.

---

### Post by gogetadbl on 2007-11-25
> **stevemu said:**
> Try the following in a terminal window.

```
sudo dpkg-reconfigure xserver-xorg
```

Worked for me when I had a similar problem.


How do I know what settings to use?  Whenever I select "nv" for my video, I get the same error but when I choose VESA everything works fine...but I cant' use the resolution I need.  Previously, I could use the nvidia from the restricted list, but now when I choose it I get the above error.

My problem is that Ubuntu detects the correct card in the device manager, but I don't know how to configure it for xserver.

EDIT: 

Everything works fine again except my refresh rate! I just used Envy to install my nvidia drivers.  How do I configure my laptop monitor?

---

