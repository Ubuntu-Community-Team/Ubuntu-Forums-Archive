---
title: "ATI Radeon HD 2600 Lucid Black Screen"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by ne0genius on 2010-05-02
I recently upgraded from 9.10 to 10.04 and was having trouble getting 3D graphics enabled on my ATI card. I am running on an MacPro3,1.

I read through this [guide]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") as I was having errors regarding fglrx so I uninstalled it and as instructed issued the following:

```

sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```

When I rebooted I got a black screen immediately after grub. I can not get to commend line with ctrl+alt+f1.

Any suggestions at this point to get a boting machine or get to a command line to see if I can fixx the drivers or possible the xorg configuration? 

Thanks

aj

---

### Post by linuxopjemac on 2010-05-02
I would chroot into your system from a liveCD
[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

---

### Post by ne0genius on 2010-05-02
ok. thanks for that.

this is my xorg.conf

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

```

should I delete the entire "Device" section referencing fglrx? is this causing the issue? or should I replace "fglrx" with "radeon" ?? I also could copy over the xorg.conf.failsafe.

video drivers and config is not an area I am familiar with. thanks.

-
aj

---

### Post by linuxopjemac on 2010-05-02
well, the driver is the actual ATI catalyst driver. Without a driver you won't see anything I guess. Maybe you can comment the Module section out for the moment, like this:

#Section "Module"
#        Load    "glx"
#EndSection

If you exchange fglrx for radeon, you might have luck too. It then uses the open source driver...

You might want to upgrade the ATI catalyst driver later:
[http://mac.linux.be/content/ati-catalyst-104-brings-initial-support-ubuntu-1004](http://mac.linux.be/content/ati-catalyst-104-brings-initial-support-ubuntu-1004)

---

### Post by linuxopjemac on 2010-05-02
[http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html)

---

### Post by ne0genius on 2010-05-02
well I made the changes to xorg.conf with no effect. I am curious as to what is happening with the system after grub is finished. Immediately goes to black. The only thing I can do is hit the power button once and it shuts down, so it seems like it is responsive. I need to get to a command line to see if I can reinstall these video drivers.

chroot did not work from the ubuntu livecd. I get the following

```
chroot: cannot run command `/bin/bash': Exec format error
```

edit:
I dont even know if the HD 2600 is compatible with the open source radeon driver. Can anyone confirm this. I think this is my real issue. I should have stuck with the closed source ATI drivers, but without getting to shell I am gonna have trouble installing them back. Will give Knoppix a shot at chroot.

---

### Post by linuxopjemac on 2010-05-02
It would surprise me that it wouldn't work from the Ubuntu liveCD...Normally this should work. At least I have heard people doing it from a Karmic CD.

---

### Post by ne0genius on 2010-05-02
> **linuxopjemac said:**
> It would surprise me that it wouldn't work from the Ubuntu liveCD...Normally this should work. At least I have heard people doing it from a Karmic CD.

ok. this was my fault. i booted a 32-bit livecd and tried to chroot into a 64-bit install. that was why i got the error. i am chroot'd now and will try to get these drivers installed. I will edit this post with an update.

edit:
@linuxopjemac, thank you for your help. your initial suggestions were correct from the get go. the issue with chroot'g into my install was my mistake. once i booted the correct architecture livecd i chroot'd and then issued

```
# wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run
# sh ati-driver-installer-10-4-x86.x86_64.run
```

I am typing this from 10.04! Thanks again for your help and patience.

---

### Post by ne0genius on 2010-05-02
well, while i am able to boot into the system with graphics support, it looks like the ati drivers did not install properly as i have no 3D support and can not enable effects. error from FGLRX-INSTALL.LOG

[http://pastebin.com/xiE7DZK7]("http://pastebin.com/xiE7DZK7")

I will move this problem on to another thread. thanks.

---

### Post by linuxopjemac on 2010-05-03
I think you have to be root to install the driver, so:
```

sudo sh ati-driver-installer-10-4-x86.x86_64.run
```

---

### Post by ne0genius on 2010-05-03
> **linuxopjemac said:**
> I think you have to be root to install the driver, so:
```

sudo sh ati-driver-installer-10-4-x86.x86_64.run
```

I was chroot'd so I was root ;) but you are correct

---

### Post by mike-g2 on 2010-08-19
This thread is relevant to other users such as myself, but it is difficult to follow exactly what you did to get your video working again.

For example, can one just execute your original code

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
``` 
and then follow it up with 
```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run
sudo sh ati-driver-installer-10-4-x86.x86_64.run
```
 and then reboot? Or was changing your xorg.conf necessary and, if so, what did you change it to?

If you could take a moment to clarify, I'd appreciate it greatly.

Mike

---

