---
title: "Video card problem NVIDIA FX 5200"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by janesac1978 on 2008-01-05
I have the NVIDIA FX 5200 AGB card and it works with Ubuntu 6.06 LTS. But I was wanting to run 7.10 but the card doesn't work. So, I installed 7.10 with a different card figuring i would just download the driver afterwards. I went to the NVIDIA site and they had a driver but I was unable to to access the file after downloading. Is there trick to run the file....or is there a reason the driver is included on 6.06 and not 7.10? I'm new to Ubuntu so any help is appreciated..Thanks...

---

### Post by oliviacond on 2008-01-05
try install the driver from Restricted Drivers Manager

---

### Post by janesac1978 on 2008-01-05
I can't run the system with the card in. So, on the restricted drivers manger it says there is no hardware requiring restricted drivers? Is there a way around that? Thanks

---

### Post by oliviacond on 2008-01-06
what about install the driver from synaptic not Restricted Drivers Manager?

Open terminal 
```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo apt-get upgrade
sudo dpkg-reconfigure xserver-xorg
```

    * Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration

# Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working
# You can test this in the terminal by typing glxinfo | grep direct (the output should be direct rendering: yes)

---

