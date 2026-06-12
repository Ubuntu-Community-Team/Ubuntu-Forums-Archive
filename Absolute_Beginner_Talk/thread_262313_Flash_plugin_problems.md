---
title: "Flash plugin problems"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-09-21
Hello there! I had a ubuntu 6.01 installation, but I've changed my notebook and needed a fresh install. I'm using 6.06 now, with firefox 1.5.0.5. I tried to install the flash plugin but I get this error:

$sudo update-flashplugin
automatic installation failed due to network problems or upstream changes

doesn't seem to be an issue with my network. What could be causing this?

Regards

---

### Post by Kilz on 2006-09-21
> **viniciuscarvalho said:**
> Hello there! I had a ubuntu 6.01 installation, but I've changed my notebook and needed a fresh install. I'm using 6.06 now, with firefox 1.5.0.5. I tried to install the flash plugin but I get this error:

$sudo update-flashplugin
automatic installation failed due to network problems or upstream changes

doesn't seem to be an issue with my network. What could be causing this?

Regards

The problem is that the Flash in the repositories is a script. It downloads the files and installs them. But there was a security update not long ago. The update just hasnt made its way to the repo's yet. You can go to the [Macromedia site and download it to your desktop.]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash") Then 

```
cd ~/Desktop
tar -xzvf install_flash_player_7_linux.tar.gz
sudo linux32 ./install_flash_player_7_linux/flashplayer-installer
```

Hit enter again when it asks you if you want to install or quit.
The installer will ask you to make sure 2 fonts are installed. We did that along with some other packages as the first step of this howto so hit enter.
It will ask you to close all browsers, and then what location it wants you to install to. Type in "/usr/lib/firefox/".
Type yes to proceed with the installation, then n if you want to perform another install.

---

### Post by Tuxman on 2006-09-23
Hmm. I stop at this step:
~/Desktop$ sudo linux32 ./install_flash_player_7_linux/flashplayer-installer
sudo: linux32: command not found

---

### Post by ubuntuuser on 2006-09-23
After extracting, just type
```
 cd install_flash_player_7_linux
./flashplayer-installer
```to start the install.

---

### Post by Tuxman on 2006-09-23
Thanks for the help. But I cannot choose what loaction I will install it. How do I change that?

I think it has something do to that I am a noon-root user, am I right?

See the screen :) .

---

### Post by foxxx on 2006-10-05
try
"sudo ./flashplayer-installer"
should work better

---

