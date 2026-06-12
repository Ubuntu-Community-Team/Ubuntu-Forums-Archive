---
title: "Nvidia Driver Issue"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Kalifornia909 on 2008-02-08
I have a problem with 7.10. i have a clean install of 7.10. i enable the restricted drivers for my nvidia 7900gs and i get no video. i hear the drums at the login screen but nothing. ive reconfig my xorg. i cannot use the nvidia driver option and have display. if i select vesa or nv i get video. what am i doing wrong

---

### Post by dstew on 2008-02-08
Do you have the 32-bit or 64-bit Ubuntu installed?

---

### Post by Kalifornia909 on 2008-02-08
32 bit

---

### Post by dstew on 2008-02-08
Then you should be able to get it working OK. Have you tried [Envy]("http://albertomilone.com/nvidia_scripts1.html") yet? Many users have done well with this installer.

---

### Post by Kalifornia909 on 2008-02-08
yes i have enabled the restricted driver and tried using envy

---

### Post by firestormx37 on 2008-02-08
If you are using the restricted drivers, then xorg.conf should have Driver "nv".  If you are using the drivers from Nvidia, then you want to have Driver "nvidia" in xorg.conf.  I have found that having the restricted drivers enabled will interfere with the installation of the drivers from Nvidia.  So if you are trying to install them, disable the restricted drivers first.  But I think you said that you got video using the "nv" option?  With the restricted drivers, that is the correct option.

---

### Post by Kalifornia909 on 2008-02-08
conflicting drivers well thats cool. which drivers will enable me to use compiz fusion. ive used beryl before on this setup

---

### Post by firestormx37 on 2008-02-08
I have been able to successfully run compiz with both drivers.

Personally, I use the drivers from nvidia because they give you a settings config tool.  I don't do anything very graphics intensive often with Ubuntu, so I have noticed much of a difference in performance between the two.  The restricted drivers are less hassle to get working.

---

### Post by Kalifornia909 on 2008-02-08
whenever i run compiz --replace it keeps saying that the drivers i am using are not whitelisted when i use just restricted. i guess im back to know nothing about compiz again

---

### Post by firestormx37 on 2008-02-08
Have you uninstalled the drivers from nvidia?  Make sure they are uninstalled.  Reinstall the restricted drivers.  Check xorg.conf to make sure that it reads Driver "nv".  Or you could even try reconfiguring xorg.conf with "dpkg-reconfigure xserver-xorg".  It will backup your old file in case you want to go back to it.  After all that, throw in a reboot.  See if that helps.  Compiz can be a pain to get running sometimes.  I know I had problems in the beginning.

---

### Post by Kalifornia909 on 2008-02-08
whenever i use the NV setting it says i dont have xgl installed and therefore cannot use compiz

---

### Post by nynoah on 2008-02-08
Did you install the drivers from ***system/admistrator/restricted drivers manager***?   Or did you do it a different way?

---

### Post by Kalifornia909 on 2008-02-08
i do it that way. i guess im going to have to use the restricted drivers. no matter whcih driver i use the screen ends up blank

---

### Post by Kalifornia909 on 2008-02-09
what am i doing wrong

---

### Post by Kalifornia909 on 2008-02-09
/bump

---

### Post by firestormx37 on 2008-02-10
Sorry for the delay, I have been away for the weekend.  Have you tried the steps I listed at the bottom of the first page?  You should try first to get the restricted drivers working.  If you make sure that you uninstall the drivers from nvidia, enable the restricted drivers and reconfigure xorg.conf, you should be alright.

---

