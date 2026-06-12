---
title: "Gfx drivers"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Namdrater on 2008-02-23
Hi everyone, I'm very new to linux. I found a thread about installing the 8800gt gfx drivers and I managed to do that fine, get back into linux straight from there and use it for a while, but everytime I reset my pc and get back into linux, I get told that my graphics driver couldnt be found and it gives me a list of cards to choose from (the same kind of thing that comes up during the installation of ubuntu live). I'm using ubuntu 7.10.

Is there any command I'm missing to make sure the graphics drivers are always loaded or something?

---

### Post by rapiscan on 2008-02-23
Hello,

I assume it's the nvidia glx drivers that you installed?  Did you do this by enabling it in the Restricted Drivers?

You can reconfigure x with the following command at your command line:

```
sudo dpkg-reconfigure xserver-xorg
```

As long as the binary driver is installed correctly, you should be able to select "nvidia" when you are prompted to select your driver.

---

### Post by PmDematagoda on 2008-02-23
That issue seems to be quite common with Nvidia 8800 GT's, the fix is to:-

1) Open a modules file for editing using:-
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
if you cannot start the X-Server then edit the file using:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

3) After that is done reconfigure your X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```
and select "nvidia" as the driver and any other options you may want, after that is done restart Ubuntu.

---

