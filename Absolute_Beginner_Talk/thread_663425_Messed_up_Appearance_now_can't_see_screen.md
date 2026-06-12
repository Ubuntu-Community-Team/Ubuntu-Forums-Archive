---
title: "Messed up Appearance now can't see screen"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by splitnrag on 2008-01-10
I am very new the ubuntu OS and was trying to get the compiz running and changed the appearance to the highest level.  It asked if I wanted to install a new driver and I clicked yes it then had me reboot and now I get a washed out screen where I can't see a thing.  I can login under the maintainence mode but have no idea how to get it back to the simple appearance and the previous video driver.  I spent most of the night getting my wireless and apps installed.  I would prefer not to have to start over if possible.  Any help is appreciated.  Thanks

---

### Post by Xavieran on 2008-01-10
Could you please post your PC specs as well as the driver you installed?

If you know what package the video driver was in you could try :
sudo apt-get uninstall nameofdriver

---

### Post by splitnrag on 2008-01-10
I didn't RTFS (Read the F'n Screen) close enough.  I have a toshiba Satelellite Pro and I believe it tried installing or installed tje NVIDIA Accelerated Graphics Driver..  I can boot up in live CD mode just fine and in safe graphics mode but that is off the cd not the install.  Is there a way to reinstall that original driver over the top of the HDD installation?  I see if I do that on the live cd it tries to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/linux-restricted-modules-2.6.22/nvideoa-glx_1.0.9639+2.6.22.4-14.9.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/linux-restricted-modules-2.6.22/nvideoa-glx_1.0.9639+2.6.22.4-14.9.deb)

---

### Post by Xavieran on 2008-01-10
You could wget the link in the maintenance mode...ie ```
wget http://archive.ubuntu.com/ubuntu/pool/restricted/linux-restricted-modules-2.6.22/nvidea-glx_1.0.9639+2.6.22.4-14.9.deb
```

And then install it using dpkg ,man dpkg for more info on it :)

When in maintenance could you type ```
lspci
```

And post anything about video cards or nvidia?

---

### Post by arochester on 2008-01-10
From your messed up screen press Ctrl+Alt+F1. That will take you away from xserver and into terminal mode. 

Then input> sudo dpkg-reconfigure xserver-xorg That will start a text based wizard to reconfigure xserver. Answer any questions you can. If there are questions you can't answer then go with the given default. If at first you don't succeed then try again. If all else fails try VESA as the video driver. 

This will probably knock out your installed video card driver. I have had success using Albert  Milone's script "Envy" at [http://albertomilone.com/wordpress/?p=140](http://albertomilone.com/wordpress/?p=140). This works for many people but does not work for all. It will download and install the correct driver.

---

### Post by Xavieran on 2008-01-10
Eh,typical of me I have to suggest the hard option instead of the easy one :)...

Thanks for a probably better idea...:)

---

### Post by arochester on 2008-01-10
Also... if you have previously installed Compiz it should still run. In order to do so, press Alt+F2, input  > compiz --replace  then click Run

---

