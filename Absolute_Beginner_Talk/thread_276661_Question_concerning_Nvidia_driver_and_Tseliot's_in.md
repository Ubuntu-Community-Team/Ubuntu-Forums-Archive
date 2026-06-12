---
title: "Question concerning Nvidia driver and Tseliot's installation guide"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by teiresias on 2006-10-13
I bought a PNY Geforce 6200 AGP to use in this box after the 9500 Pro I'd planned to use went bye-bye.

In any case, I used tseliot's guide to install the driver.  Everthing went fine until I tried to restart X and I ended up with a blank screen, even when I rebooted.  I went into the recovery mode and played around with the xorg.conf file and ended up trying the Problem Note #4 in tseliot's guide.  This is the one where you add the following to your video card "device" entry in the xorg.conf file:

```

Option "NvAGP" "0" 
Option "RenderAccel" "Off" 
Option "IgnoreDisplayDevices" "DFP,TV" 
Option "NoRenderExtension" "Off" 
Option "AllowGLXWithComposite" "Off"
```

I did not have to use the "Accel" "Off" entry, so I'm assuming 3D acceleration is working fine, but I'm curious as to what I'm actually giving up by enabling these options.  Would it be advantageous to go through and comment out these options one at a time and see at what point it actually stops working so I'm using as few of these options as possible?

I'm just wondering if having these options on would hinder running Beryl or anything like that if I chose to try and do so in the future?  Thanks guys.

---

