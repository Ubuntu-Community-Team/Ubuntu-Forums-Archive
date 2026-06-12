---
title: "Modprobe help! :[["
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by brokenstrides on 2008-04-17
Hey!

I have been using Linux off and on over the past 5 years or so, and I started using Ubuntu about a year ago, and everything was running right away besides my graphics and wireless...

I was able to install wireless drivers through ndiswrapper and install graphics drivers through Envy (which I LOVE, very many thanks to alberto milone!) ANYWAY,

my problem is that even though my ndiswrapper instructions say to type in ```
sudo modprobe ndiswrapper
```

even though I type this in, everytime I reboot my computer, it seems like the wireless and graphics drivers never want to load. I have to type in ```
sudo depmod -a<br>sudo modprobe ndiswrapper
```

in the terminal every time I want the wireless to work. Also for some reason, every time I log in again I have to set the resolution back to my monitors actual res, and the driver is always switched to vesa.

I've done all this before, but for some reason never had this problem. What am I doing wrong, or not doing at all???

Thanks!

---

### Post by spiderbatdad on 2008-04-18
Possibly this...get your monitor and wireless running the way you want. Run command:```
sudo update-initramfs -u
```

---

### Post by Hospadar on 2008-04-18
I think you can add them to /etc/modules to get them to load on boot

---

