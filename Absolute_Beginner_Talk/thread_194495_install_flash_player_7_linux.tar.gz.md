---
title: "install_flash_player_7_linux.tar.gz"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-06-11
Hi.
I've dowloaded the flashplayer installer on the desktop; now I don't know where to move it, - I mean - in which directory, before installing it.
Can anyone help me, please.? Thanks.:D

---

### Post by johnc4510 on 2006-06-11
There is a much easier way to install it via Synaptic Package Manager. Its called:
flashplugin-nonfree
Synaptic will install this to the correct directory for you.
You must have the extra repositories enabled though. If you don't know how to do this, post here and I will tell you how.

---

### Post by sanderella on 2006-06-11
I'm interested in the answer to this one, too. How does one "have the extra repositories enabled"
thanks

---

### Post by johnc4510 on 2006-06-11
System>Administration>Synaptic Package Manager
Launch it then:
Click on settings, click on repositories
Put a check mark in all the empty boxes and then close that window
Click on Reload, Click on Mark all Upgrades, Click on Apply
There will now be ready to install all the extra packages from Universe and Mulitverse.

---

### Post by hanexar on 2006-06-11
To add repositories, follow this howto: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

If you want to do it manually, I've done it by extracting the files to the /[home path]/.mozilla/firefox/plugins

If you want to see those folders in Nautilus, you need to check "show hidden files" in the view menu.

Don't forget to restart firefox after.

---

### Post by helphope on 2006-06-11
Thanks to you all. I'll do it via synaptic. At this moment the terminal is busy, just installing the pugl-in.
Thanks again

---

### Post by Drakkor on 2006-06-11
I supposedly did update the Synaptic Manager,but failed to find flashplugin-nonfree, or java runtime environment programs. :confused:

---

### Post by Dr. Nick on 2006-06-11
my personal expierence tells me not to use the synaptic version, It may work for some but always crashed for me.

If you download the tar from macromendia just extract it and run the installer, if it ask what to do hit run in terminal. It will guide you through it. That has always been best for me

---

### Post by racecat on 2006-06-11
It should have downloaded to Desktop. Open a terminal. Then:

```
cd Desktop
sudo tar -xvf install_flash_player_7_linux.tar.gz
```

It will create a new directory called "install_flash_player_7_linux"

```
cd install_flash_player_7_linux
./flashplayer-installer
```

Close down the browser when prompted and accept the default install location (for firefox, it will list a mozilla directory).

Done.

You can move the install stuff to home or just delete it.

Luck,
Bill

---

### Post by helphope on 2006-06-12
Thanks you wrote, 'cause the installation via synaptic didn't work.
:KS

---

