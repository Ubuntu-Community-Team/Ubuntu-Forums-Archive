---
title: "Installing ATI Radeon Drivers"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by xelink on 2005-11-22
I have an ATi radeon 9250 which I wish to install drivers for. I tried their site, but I got a .run file which does nothing. Any help?

---

### Post by gord on 2005-11-22
make sure you set the .run file to executionable mode 
```
 
sudo chmod +x <filename>.run 
./<filename>.run

```

---

### Post by xelink on 2005-11-22
I entered this and get a "chmod: cannot access `ati-driver-installer-8.19.10-i386.run': No such file or directory
":

sudo chmod +x ati-driver-installer-8.19.10-i386.run
./ati-driver-installer-8.19.10-i386.run

ati-driver-installer-8.19.10-i386.run is the file name, and ti is on ym desktop. Anythign I am doing wrong

---

### Post by gord on 2005-11-22
```

cd ~/Desktop/
sudo chmod +x ati-driver-installer-8.19.10-i386.run
./ati-driver-installer-8.19.10-i386.run

```

you need to be in your desktop first, your desktop is a subdirectory of your home directory

---

### Post by Darrin on 2005-11-22
This was the easiest for me.
[Read this post.]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver")

---

### Post by xelink on 2005-11-23
thanks darin, should help alot... I did it and it seemed to detect everything... only bad part was that I enetered the code for an Nforce 2 motherboard(I have 3 and went stupid) so i ended up having to reinstall, but ohh well.

---

### Post by Darrin on 2005-11-23
Glad to hear its working out for you. :)

---

### Post by Darrin on 2005-11-23
[QUOTE=xelink]only bad part was that I enetered the code for an Nforce 2 motherboard(I have 3 and went stupid) so i ended up having to reinstall, but ohh well.[/QUOTE]
I would think you would just have to reverse the step to correct your problem. 
```
sudo gedit /etc/X11/xorg.conf
```

Change &#8220;Section "Device"
Remove the following line:
```
  Option  "UseInternalAGPGART" "no"
```

Restart your machine for changes to take effect.

---

### Post by xelink on 2005-11-23
I am, of course, too inexperienced to have thought of that(tried using the little go back option in the comand line, didn't work) I think I am getting somewhere, but am unsure... for some reason though, it falters on the second line,

sudo depmod -a ; sudo modprobe fglrx

I get: sudo depmod -a ; sudo modprobe fglrx

the package should be installed by default if I am nto correct, I even tried apt-get to make sure it was installed and it was.

I want to check before I restart and find myself in the same situation as before...





=================

I also tried the other method which was recomended, I DLed ATis driver set to the desktop, then it mentioned needing to be the superuser... any help, any command, like sudo i can use to get around/through this?

---

### Post by Gharchkhor on 2008-04-03
I have a problem while installing this driver.

please help me. i MUST install it to be able to run MAYA 7.0 on Ubuntu. that's why i migrated to Ubuntu from windows. to experience MAYA run more faster than windows.

```
untitled@untitled-desktop:/media/sda1$ sudo chmod +x ati-driver-installer-8-3-x86.x86_64.run 
untitled@untitled-desktop:/media/sda1$ ./ati-driver-installer-8-3-x86.x86_64.run
Created directory fglrx-install.yO6608
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.471...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Extraction failed.
Signal caught, cleaning up

```

and also when i try to run maya it releases like this:

```
untitled@untitled-desktop:/media/sda1$ maya
Segmentation fault (core dumped)

```

I got a damn ATi R9200 card. 
and P4 2.8 hrtz

---

### Post by Bushfire on 2008-04-03
I can't recall exactly, and the AMD website isn't behaving at the moment, but I think ATI dropped support for any Radeon earlier than 9500 at fglrx 8.28.8. This is, of course, available for download, but is unmaintained and isn't setup for any xorg version over 7.1. What this means is that if it is the case (and I'm pretty sure it is), once you do manage to install the driver, it won't work (X won't start up and you'll be left at a text console). On the bright side, the default xorg ati driver supports 3D acceleration and all, and it should be the one you are using right now.

---

### Post by Gharchkhor on 2008-04-03
> **Bushfire said:**
> I can't recall exactly, and the AMD website isn't behaving at the moment, but I think ATI dropped support for any Radeon earlier than 9500 at fglrx 8.28.8. This is, of course, available for download, but is unmaintained and isn't setup for any xorg version over 7.1. What this means is that if it is the case (and I'm pretty sure it is), once you do manage to install the driver, it won't work (X won't start up and you'll be left at a text console). On the bright side, the default xorg ati driver supports 3D acceleration and all, and it should be the one you are using right now.

Running MAYA on Ubuntu was my only reason for willing to installing that ATi closed source Driver.

Well so then do you know another Driver or way to fix my problem on Running MAYA?

---

### Post by PmDematagoda on 2008-04-03
Trying to solve your problems is understandable, but trying to resurrect old threads that are more than 3 years old in order to solve your problems is not understandable and is usually frowned upon.

This thread is closed, if you want to continue with this discussion then please start a new thread in the appropriate section.

---

