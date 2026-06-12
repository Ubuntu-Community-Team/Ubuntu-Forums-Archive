---
title: "[SOLVED] Flash help!"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by albel65 on 2008-01-23
Hello people!

I've recently installed 64-bit Gutsy and had no problems with it until using Firefox and installing Flash. After the installation, the page is refreshed and still informs me that I still have the flash plugin to install, since no flash content is displayed. After several attempts of uninstalling and installing, i finally notice this:
```
Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

Is there a way to fix this?

Thanks.

---

### Post by rhc on 2008-01-23
After you opened tar.gz,go to that directory from terminal and run > ./flashplayer-installer.

---

### Post by albel65 on 2008-01-23
> **rhc said:**
> After you opened tar.gz,go to that directory from terminal and run .I have tried this, but i get an error: ```
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
```

---

### Post by rhc on 2008-01-23
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

please enter the site and click download now.
Download tar.gz again .

Open it go that directory and again > ./flashplayer-installer

Maybe you downloaded it from wrong place or from Synaptic.

---

### Post by ibizatunes on 2008-01-23
i had the simlar issue with x64 bit
 install "gnash" instead!
from add remove programs
This improved my x64 reliability, and all flash sites work fine!

---

### Post by albel65 on 2008-01-23
> **rhc said:**
> [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

please enter the site and click download now.
Download tar.gz again .

Open it go that directory and again 

Maybe you downloaded it from wrong place or from Synaptic.Actually, i did download it from there. And that's how i got the error.

> **ibizatunes said:**
> i had the simlar issue with x64 bit
 install "gnash" instead!
from add remove programs
This improved my x64 reliability, and all flash sites work fine!

I've tried gnash, i like it. But there are just some things gnash can't display. And that's why i have to stick with Adobe

---

### Post by ibizatunes on 2008-01-23
Adobe as far as i no, doesnt have a x64 version, its in devlopement, that is y u have that error try to install adobe flash, i386 = x32bit system
gnash is the best bet i think still

---

### Post by rhc on 2008-01-23
If you have 64 bit system,get a 32 bit browser and you can install 32 bit flash player.
Adobe doesn't support directly 64 bit.

---

### Post by albel65 on 2008-01-23
> **rhc said:**
> If you have 64 bit system,get a 32 bit browser and you can install 32 bit flash player.
Adobe doesn't support directly 64 bit.
Alright, seems like the best solution i can go for at the moment. Thank you!

---

### Post by m.capurso on 2008-01-23
The gnash plugin used with some sites (try with YouTube) hangs Firefox and the computer.
The only solution working for me is removing the gnash AND the Adobe plugin, going to YouTube WITHOUT any flash plugin, clicking on the DOWNLOAD PLUGIN, getting the tar.gz package and installing it as root.

---

